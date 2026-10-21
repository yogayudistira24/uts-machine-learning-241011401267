# uts-machine-learning-241011401267
# UTS Machine Learning – Linear Regression & Logistic Regression

- **Nama** : Yoga Yudistira
- **NIM** : 241011401267
- **Kelas** : Reg B 
- **random_state** : 42 *(ganti dengan 2 digit terakhir NIM)*

Seluruh model dan metrik (`train_test_split`, `LinearRegression`, `LinearRegressionGD`, `LogisticRegression`, `accuracy_score`, `confusion_matrix`, MAE/MSE/RMSE/R², precision/recall/F1) diimplementasikan sendiri dengan NumPy. scikit-learn hanya dipakai pada soal bonus.

## Isi Repositori

| File | Keterangan |
|---|---|
| `tugas_UTS.ipynb` | Notebook jawaban, sudah dijalankan lengkap dengan output dan grafik |
| `Ads_Data.csv` | Dataset Bagian A (biaya iklan vs penjualan, 40 data) |
| `Email_Data.csv` | Dataset Bagian B (deteksi spam, 60 data) |

## Ringkasan Hasil

### Bagian A – Linear Regression (`Ads_Data.csv`, test_size = 0.2)

| Item | Hasil |
|---|---|
| Persamaan (Normal Equation) | ŷ = 26.345 + 9.363 · BiayaIklan |
| R² training / testing | 0.955 / 0.814 |
| RMSE testing | 7.50 juta Rp |
| MAE testing | 6.57 juta Rp |
| Gradient descent lr = 0.001 | belum konvergen (terlalu lambat) |
| Gradient descent lr = 0.02 | konvergen, sama dengan Normal Equation |
| Gradient descent lr = 0.1 | divergen (overflow, hasil NaN) |
| Prediksi biaya iklan 4.5 / 7 / 12 juta | 68.48 / 91.89 / 138.70 juta Rp (12 juta = ekstrapolasi) |

### Bagian B – Logistic Regression (`Email_Data.csv`, test_size = 0.25)

| Item | Hasil |
|---|---|
| Persamaan | P(Spam) = σ(−9.133 + 0.808 · JumlahLink + 0.790 · KataPromo) |
| Accuracy (threshold 0.5) | 0.933 |
| Precision / Recall / F1 | 0.857 / 1.000 / 0.923 |
| Confusion matrix (TN, FP, FN, TP) | 8, 1, 0, 6 |
| Threshold yang dipilih | 0.7 (memprioritaskan precision karena FP lebih merugikan) |

Prediksi email baru (threshold 0.7): E1 = Bukan Spam, E2 = Bukan Spam, E3 = Spam, E4 = Spam.

### Bonus – Perbandingan dengan scikit-learn

- Linear Regression: hasil identik dengan scikit-learn.
- Logistic Regression: koefisien berbeda dari `LogisticRegression` default scikit-learn karena scikit-learn memakai regularisasi L2 (`C = 1.0`). Tanpa regularisasi (`C = 1e10`) dan dengan iterasi gradient descent yang lebih panjang, hasilnya hampir sama.

## Cara Menjalankan

```
pip install numpy pandas matplotlib
jupyter notebook tugas_UTS.ipynb   # lalu Run All
```
