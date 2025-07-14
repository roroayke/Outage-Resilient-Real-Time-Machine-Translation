# ⚡ Efficient NMT via Knowledge Distillation (KD)

## 🚀 Project Overview

This project explores **Knowledge Distillation (KD)** to compress a large **MarianMT Teacher** model into a lightweight **Student** model for **German-English Neural Machine Translation (NMT)**. The goal: retain translation quality while improving inference speed, memory footprint, and energy efficiency — all deployable on **consumer-grade GPUs like the RTX 4070**.

> 🧠 We distilled translations using sequence-level KD, benchmarked energy use, and showed that efficient, low-carbon machine translation is possible on local devices.

---

## 🧪 Model Setup

| Component     | Description                                      |
|---------------|--------------------------------------------------|
| **Teacher**   | MarianMT (Helsinki-NLP, 6-layer Transformer)     |
| **Student**   | 3-layer Transformer (sequence-level distilled)   |
| **Training**  | Hugging Face + PyTorch + FP16 mixed-precision    |
| **Distillation** | Sequence-level only (no logits/intermediate layers) |

---

## 🖥️ Hardware Benchmarking

| Metric                 | RTX 4070        | Tesla T4         |
|------------------------|----------------|------------------|
| Training Time          | ~1.8 minutes    | ~0.6 minutes     |
| Cost (est.)            | ~$0.01          | ~$0.00           |
| BLEU (Teacher)         | 18.10           | 18.10            |
| BLEU (Student)         | 8.01            | 7.44             |
| Emissions Estimate     | << 0.001 kg CO₂ | ~0.001 kg CO₂    |

📉 **BLEU drop** shows the tradeoff with shallow KD + tiny data (~1k samples).  
🌱 But: Carbon impact = almost nothing. Let’s call it **"Green Translation."**

---

## 📂 Dataset

- **Language Pair**: German ↔ English
- **Corpus**: ~1,000 parallel sentence pairs
- **Tokenization**: Hugging Face pre-trained tokenizer
- **Note**: Tiny dataset = rapid prototyping, not full model fidelity

---

## 📈 Results Summary

| Model Type         | BLEU Score | Token Overlap (%) |
|--------------------|------------|-------------------|
| Teacher (MarianMT) | 18.10      | --                |
| Student (KD Model) | 8.01       | ~9.4% avg         |

The student model:
- Preserved coarse structure
- Struggled with idioms, imperatives, short phrases
- Was **~2.5x faster** at inference (qualitatively)

---

## 🌍 Environmental Insights

We benchmarked GPU energy and cost efficiency using **consumer hardware**:
- ✅ Trained in < 2 mins on RTX 4070
- ✅ Cost under **$0.01**
- ✅ CO₂ emissions estimated at **~1000x lower** than baseline

> Efficiency isn’t just good engineering — it’s ethical AI.

---
