# Event Expense Tracker - ML Model

Repositori ini berisi pelatihan model BiLSTM-CRF untuk mengubah teks mentah nota belanja menjadi struktur data terorganisir.

## Struktur File
* `2nd_Phase.ipynb` : Fase pelatihan model Machine Learning menggunakan data berformat BIO, evaluasi model, dan konversi ke TFLite.
* `doccanoBIO_bersih.txt` : Dataset hasil pelabelan berformat BIO yang sudah dibersihkan.
* `best_ner_weights.h5` : Bobot model terbaik hasil pelatihan.

## Arsitektur Model
* **Algoritma Utama:** Bidirectional Long Short-Term Memory dipadukan dengan Conditional Random Fields (BiLSTM-CRF).
* **Word Embedding:** FastText Word2Vec (`cc.id.300.vec`) untuk representasi vektor kata bahasa Indonesia.
* **Format Output:** Model dikonversi ke format `.tflite` untuk ditanamkan ke dalam aplikasi Android.

## Metrik Evaluasi
Berikut adalah ringkasan performa F1-Score dari model klasifikasi entitas (NER) pada saat pengujian:

| Entitas (BIO Tag) | Precision | Recall | F1-Score |
|:---|:---:|:---:|:---:|
| **B-tanggal** | 0.90 | 0.94 | **0.92** |
| **B-jumlah** | 0.84 | 0.90 | **0.87** |
| **B-harga_satuan** | 0.83 | 0.87 | **0.85** |
| **B-harga_total_barang** | 0.84 | 0.86 | **0.85** |
| **B-total_belanja** | 0.78 | 0.81 | **0.80** |
| **B-nama_barang** | 0.80 | 0.76 | **0.78** |
| **B-diskon** | 0.80 | 0.69 | **0.74** |
| **B-nama_toko** | 0.73 | 0.69 | **0.71** |
* **Akurasi:** 92%

## Requirements
Pastikan environment Python kamu sudah terinstal *library* berikut:
* `tensorflow`
* `tensorflow-addons`
* `tf2crf`
* `numpy`
* `scikit-learn`
*(Bisa diinstal melalui terminal dengan perintah: `pip install tensorflow tensorflow-addons tf2crf numpy scikit-learn`)*

## Cara Penggunaan
1. Clone repositori ini: 
   `git clone https://github.com/sitifatiharh/event-expense-tracker-ml.git`
2. Unduh model FastText bahasa Indonesia (`cc.id.300.vec`) dan letakkan di **direktori utama (root folder)** repositori ini. *(File ini diabaikan oleh Git karena ukurannya besar)*.
3. Buka proyek ini menggunakan VS Code.
4. Buka `2nd_Phase.ipynb` dan klik **Run All** untuk melakukan proses pelatihan model, melihat evaluasi performa, hingga menghasilkan file `.tflite`.
