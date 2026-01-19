[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/19C68qRCOC9VYm2bHD_-4Aewxu4zqtf_0#scrollTo=ZaAeQ16Y2au9)


# LoRA Learning Observatory

Early detection of healthy, degraded, and dead LoRA fine-tuning runs using adapter dynamics.

This repository contains a **single reproducible Colab notebook** that demonstrates how
fine-tuning failures can be detected **within the first 10 training steps**, without
waiting for training to complete.

---

## 🚀 Run in Colab

[Open the notebook in Colab](https://colab.research.google.com/drive/19C68qRCOC9VYm2bHD_-4Aewxu4zqtf_0?usp=sharing)

---

## What this notebook does

- Fine-tunes a **1.1B TinyLlama model** using **LoRA**
- Logs **LoRA adapter norms** at every training step
- Runs controlled experiments:
  - Healthy training
  - Degraded training (low learning rate)
  - Dead training (zero learning rate)
- Shows that:
  - The learning trajectory is determined very early
  - Steps **1–10** are sufficient to classify run health
- Visualizes:
  - Total LoRA norm vs step
  - Early signal vs full learning trajectory

---

## Key idea

Loss curves alone are often misleading during fine-tuning.
Instead, we analyze **adapter learning dynamics** to detect:

- 🟢 Healthy runs
- 🟡 Degraded runs
- 🔴 Dead runs

This detection is:
- model-agnostic
- dataset-agnostic
- cheap to compute
- usable early in training

---

## Why this matters

Dead and degraded fine-tuning runs waste significant compute.
By detecting failures early, practitioners can:

- stop bad runs early
- debug training recipes
- iterate faster

---

## Notes

- The notebook runs fully on a **single Colab GPU**
- No private datasets are required
- No UI or infrastructure dependencies

---

## Disclaimer

This project analyzes training artifacts only.
It does not provide a training service or replace existing fine-tuning frameworks.
