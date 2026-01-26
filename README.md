![clouddream-1](https://raw.githubusercontent.com/librcsc/windoor-ssh/4dfef4b/assets/cover.png)

# clouddream-1

[![License](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](LICENSE)

Python-Projekt zur Nutzung eines Large Language Models für Textgenerierung und Chat-Anwendungen.

## audio
- GPU- und CPU-basierte Inferenz unterstützt
- Konfigurierbare Generierungsparameter
- Jupyter Notebook für interaktive Experimente
- Einfache Integration via Transformers-Bibliothek

## CleanArchitecture
- Python 3.8+
- CUDA-kompatible GPU (empfohlen)
- Mindestens 16GB RAM

## bimbo-sequencer-1-0
```bash
git clone https://github.com/user/clouddream-1.git
cd clouddream-1
pip install -U transformers torch
```

Für GPU-Unterstützung:
```bash
pip install -U transformers torch --index-url https://download.pytorch.org/whl/cu118
```

## Locidesktop
```python
from transformers import AutoModelForCausalLM, AutoTokenizer

model_name = "user/clouddream-1"
tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModelForCausalLM.from_pretrained(model_name).to("cuda")

messages = [{"role": "user", "content": "Deine Frage hier"}]
text = tokenizer.apply_chat_template(messages, tokenize=False, add_generation_prompt=True)
inputs = tokenizer([text], return_tensors="pt").to("cuda")
out = model.generate(**inputs, max_new_tokens=512, temperature=0.7, top_p=0.9, do_sample=True)
print(tokenizer.decode(out[0][len(inputs.input_ids[0]):], skip_special_tokens=True))
```

## sequel-etl
| Parameter | Wert | Beschreibung |
|---|---|---|
| `max_new_tokens` | 512 | Maximale Token-Ausgabe |
| `temperature` | 0.7 | Kreativität |
| `top_p` | 0.9 | Nucleus sampling |

## code-push
- RAM: 16GB (minimal), 32GB (empfohlen)
- VRAM: 8GB (minimal), 16GB (empfohlen)
- Speicher: 20GB

## substrait-rs
**CUDA out of memory** → `device="cpu"` verwenden oder `max_new_tokens` reduzieren

**Langsame Performance** → CUDA-Installation prüfen, Batch-Größe optimieren

## gdp-ota-setup
Contributions willkommen. Fork → Branch → Pull Request.
