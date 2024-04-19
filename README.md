# Laporan Proyek : Sistem-Rekomendasi-Buku

### **Nama : Nurul Nyi Qoniah**
### **Email : nurulqoniah313@gmail.com**
### **Username : nurqoneah**


## **Deskripsi**
Membuat model system recommender dengan menggunakan dataset book, user, rating dari [dataset kaggle](https://www.kaggle.com/code/fahadmehfoooz/book-recommendation-system/notebook)

## **Project Overview**

Di era kemajuan informasi, mencari buku yang tepat untuk dibaca bisa menjadi hal yang sangat berharga. Sistem Rekomendasi Buku digunakan untuk membantu pengguna atau pembaca dengan memberikan rekomendasi personal berdasarkan preferensi pengguna, riwayat membaca, dan faktor lain yang relevan. Proyek ini bertujuan untuk mengembangkan sistem rekomendasi buku yang tangguh dengan memanfaatkan teknik-teknik machine learning.

referensi dari proyek ini : [Journal](https://colab.research.google.com/drive/1m5rPhoWhpEEKA4bKkZEE-GbJU71zr9Q2#scrollTo=8Itu1xEASkEl&line=5&uniqifier=1)


## **Business Understanding**

### **Problem Statements**
Bagaimana cara merekomendasikan buku yang disukai pembaca lain dapat direkomendasikan kepada pembaca lainnya juga?

### **Goals**
Dapat membuat sistem rekomendasi yang akurat berdasarkan ratings dan aktivitas pengguna pada masa lalu.

### **Solution approach**
Solusi yang saya buat yaitu dengan menggunakan 2 algoritma Machine Learning sistem rekomendasi,yaitu :

* Content Based Filtering adalah algoritma yang merekomendasikan item merekomendasikan item yang mirip dengan item yang disukai pengguna di masa lalu.
* Collaborative Filtering adalah algoritma yang bergantung pada pendapat komunitas pengguna.

## **Data Understanding**
Dataset yang digunakan untuk membuat sistem rekomendasi buku ini didapat dari situs Kaggle **Book Recommendation Dataset** yang dapat diakses melalui link [dataset](https://www.kaggle.com/datasets/arashnic/book-recommendation-dataset)

### **Univariate Exploratory Data Analysis**

Feature-feature dalam data **books** sebagai berikut:

*   ISBN : merupakan kode ISBN buku
*   Book_Title : merupakan judul buku
*   Book_Author : merupakan penulis buku
*   Year_Of_Publication : merupakan tahun buku saat dipublikasi
*   Image_URL_S : link gambar buku ukuran kecil
*   Image_URL_M : link gambar buku ukuran medium
*   Image_URL_L : link gambar buku ukuran besar

Feature-feature dalam data **user** sebagai berikut:

*   User-ID : merupkan Id User atau pembaca buku
*   Location : merupakan alamat pembaca buku atau user
*   Age : merupakan umur dari user atau pembaca buku

Feature-feature dalam data **ratings** sebagai berikut:

*   User-ID : merupkan Id User atau pembaca buku
*   ISBN : merupakan kode ISBN buku
*   Book-Rating : merupakan rating user untuk buku

## **Data Preparation**

*   **Mengatasi Misiing Value** : menggunakan isnull untuk melihat data yang null
*   **Mensorting data menurut ISBN** : mengurutkan data berdasarkan ISBN
*   **Menghapus data duplikat** : mengunakan drop_duplicates untuk meghilangkan data duplikat yang dapat memperngaruhi hasil
*   **Membuat data list** : mengubah data menjadi list
*   **TfidfVectorizer** : mengubah data teks menjadi vektor untuk digunakan dalam membuat sistem rekomendasi dengan content based filtering
*   **Encoder data** : mengubah data dari satu format menjadi format lainnya
*   **Membagi data atau Split Data Train dan Test** : membagi data menjadi 80% data untuk training dan 20% data untuk testing


## **Modeling and Result**
### **Content Filtered Recommendation System**
Teknik content based filtering akan merekomendasikan item yang mirip dengan item yang disukai pengguna di masa lalu dengan tfidf vectorizer dan menghitung tingkat kesamaan dengan cosine similarity. Hasil dari algoritma content based filtering adalah sebagai berikut:



### **Collaborative Filtered Recommendation System**
Dari data rating pengguna, maka akan diidentifikasi buku-buku yang mirip dan belum pernah dibaca oleh pengguna untuk direkomendasikan. Hasil dari algoritma collaborative content filtering adalah sebagai berikut:

## **Evaluation**
### **Content Filtered Recommendation System**

### **Collaborative Filtered Recommendation System**
Metriks eavaluasi yang digunakan untuk sistem rekomendasi buku dengan algoritma collaborative content filtering adalah metrik RMSE (Root Mean Squared Error).

RMSE (Root Mean Square Error) adalah salah satu metrik evaluasi yang umum digunakan dalam statistika dan machine learning untuk mengukur seberapa baik model memprediksi nilai dalam data. RMSE mengukur akurasi prediksi model dengan menghitung akar dari rata-rata kuadrat dari selisih antara nilai prediksi dengan nilai sebenarnya.

Rumus RMSE adalah sebagai berikut:

```math
\mathop{\mathrm{RMSE}} = \sqrt{ \frac{1}{n} \sum_{i=0}^{n-1} (y_i - x_i)^2 }
```

di mana:
- yi adalah nilai sebenarnya dalam data
- xi adalah nilai yang diprediksi oleh model untuk nilai yi
- n adalah jumlah observasi dalam data
- Σ adalah simbol untuk menjumlahkan semua nilai dalam suatu deret

Kelebihan RMSE:

* Mudah diinterpretasikan: RMSE memberikan nilai yang mudah diinterpretasikan dalam satuan yang sama dengan variabel yang diukur.
* Sensitif terhadap kesalahan besar: Karena RMSE mengkuadratkan selisih antara nilai sebenarnya dan prediksi, ia lebih sensitif terhadap kesalahan besar daripada metrik evaluasi lainnya seperti MAE (Mean Absolute Error).

Kekurangan RMSE:

* Rentan terhadap outlier: RMSE dapat terpengaruh oleh adanya outlier dalam data, karena mengkuadratkan selisih antara nilai sebenarnya dan prediksi.
* Tidak selalu intuitif: Kadang-kadang sulit untuk menginterpretasikan apakah nilai RMSE yang rendah sudah cukup baik atau tidak, terutama jika tidak ada nilai referensi untuk perbandingan.

Dalam proyek ini untuk menerapkan metrik ini gunakan parameter metrics untuk model yaitu `tf.keras.metrics.RootMeanSquaredError()` . Hasil dari metriks evaluasi untuk model rekomendasi buku dengan algirtma ini adalah sebagai berikut:
