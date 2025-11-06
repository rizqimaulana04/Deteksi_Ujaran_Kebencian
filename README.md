# Deteksi Ujaran Kebencian Bahasa Indonesia (TF-IDF & SVM)
| Anggota Kelompok 8            |                        |    
| ----------- | ---------------------- |
| Muhammad Rizqi Maulana        | 312210360 |
| Afrizal Fajrianto A.S | 312210449      |
| Sandy Ramadhan| 312210633              |
| Dhefi Nurkholik    | 312210414              |
*Dosen Pengampu: Dr. Muhamad Fatcan, S.Kom., M.Kom.*
---
*Memenuhi Tugas UTS Mata Kuliah Kecerdasan Buatan*
---

Klasifikasi *biner* pada teks berbahasa Indonesia dari media sosial (0 = tidak mengandung ujaran kebencian, 1 = mengandung ujaran kebencian).  
Repository ini berisi pipeline end-to-end: *preprocessing → representasi (TF-IDF) → model (Linear SVM / Logistic Regression) → evaluasi, serta visualisasi distribusi label dan Word Cloud*.

---

## ✨ Fitur Utama
- *Preprocessing* (sesuai ketentuan):
  - Case folding (lowercase)
  - Menghapus URL/mention/hashtag, angka, dan tanda baca
  - Tokenisasi whitespace
  - Stopword removal (NLTK Bahasa Indonesia)
  - Opsional *stemming Sastrawi*
- *Representasi Fitur:* *TF-IDF* (unigram & bigram)
- *Model Klasifikasi:*
  - *Linear SVM (utama)* dengan class_weight='balanced'
  - *Logistic Regression* (pembanding)
- *Evaluasi:* Confusion Matrix, Accuracy, Precision, Recall, F1-Score, Classification Report
- *Visualisasi:* Distribusi label & *Word Cloud* untuk kelas *1 (HS)*

---

## 🗃 Dataset
Gunakan salah satu:
1. *Dataset pribadi* (CSV/XLSX) milik Anda sendiri.
2. *Dataset publik Kaggle: Indonesian Abusive and Hate Speech Twitter Text (mencakup kolom HS).  
   Pada proyek ini label *biner* didefinisikan sebagai:
   - label = 1 jika HS == 1 (mengandung ujaran kebencian)
   - label = 0 jika selain itu (tidak mengandung ujaran kebencian)

> *Catatan:* Jika memakai Kaggle, Anda perlu kaggle.json (Kaggle → Profile → Account → Create New API Token).

---

## ⚙ Persiapan Lingkungan

### Opsi A — Google Colab (disarankan)
- Buka notebook/sel Colab yang disertakan di repo ini (folder notebooks/ atau snippet pada README).
- Jika menggunakan Kaggle, upload kaggle.json saat diminta.

### Opsi B — Lokal (Python ≥ 3.9)
```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -U pip
pip install numpy pandas scikit-learn seaborn matplotlib wordcloud charset-normalizer nltk Sastrawi imbalanced-learn joblib
python -c "import nltk; nltk.download('stopwords')"