# <h1 align="center">Laporan Praktikum Modul Exploratory Data Analysis (EDA)</h1>
<p align="center">Yoka Romadani</p>

## Dasar Teori
                            Apa itu EDA

“Exploratory Data Analysis (EDA) is an approach/philosophy for data analysis that
employs a variety of techniques (mostly graphical) to maximize insight into a data
set”
Secara  definitif, Exploratory  DataAnalysismengacu  pada  proses kritis  dalam  melakukan  investigasi  awal  pada  data untuk menemukan pola, untuk menemukan anomali, untuk menguji hipotesis dan untuk memeriksa asumsi dengan bantuan statistik  ringkasan dan representasi  grafis[1]. Analisis Data Eksploratif (EDA) adalah pendekatan/filosofi untuk analisis data yang
menggunakan berbagai teknik (sebagian besar berupa grafis) untuk memaksimalkan
wawasan terhadap sebuah dataset, dengan:
1.mengungkap struktur dasar;
2.mengekstraksi variabel penting;
3.mendeteksi outlier dan anomali;
4.test underlying assumptions (menguji asumsi-asumsi yang mendasar;
5.mengembangkan model-model yang sederhana
6.Menentukan setting faktor yang optimal.
## Guided 
### 1. mengiport library pandas dan numpy

```python
import pandas as pd
import numpy as np
```


### 2. mensumon data file csv 

```python
df = pd.read_csv('Movie_classification.csv')
```
menampilkan data Movie_classification.csv 

### 3. Buat fungsi yang menampilkan apakah suatu angka adalah bilangan prima

```python
import pandas as pd
iris_filename = 'Iris.csv'
iris = pd.read_csv(iris_filename, sep=',',
                   decimal=',', header=None,
                   names= ['sepal_length',
                           'sepal_widht',
                           'petal_lenght',
                           'petal_width',
                           'target'])

```
Kode program di atas adalah skrip Python yang menggunakan library **pandas** untuk membaca file CSV bernama `Iris.csv`. Pertama, baris `import pandas as pd` mengimpor library pandas dan memberinya alias `pd`, yang memudahkan penggunaan fungsi-fungsinya. Kemudian, variabel `iris_filename` menyimpan nama file CSV yang akan dibaca. Pada baris berikutnya, fungsi `pd.read_csv()` digunakan untuk membaca data dari file tersebut dengan beberapa parameter. Parameter **sep=','** menunjukkan bahwa pemisah antar kolom dalam file adalah koma, sedangkan **decimal=','** mengindikasikan bahwa tanda desimal yang digunakan adalah koma, yang biasanya berlaku di beberapa negara. Parameter **header=None** menunjukkan bahwa file CSV tidak memiliki baris header, sehingga pandas akan menganggap semua baris sebagai data. Selain itu, **names=[...]** memberikan nama pada kolom-kolom data yang dihasilkan, yaitu 'sepal_length', 'sepal_widht', 'petal_lenght', 'petal_width', dan 'target'. Setelah eksekusi kode ini, variabel `iris` akan berisi DataFrame yang menyimpan data dari file CSV dengan kolom yang dinamai sesuai dengan yang telah ditentukan. DataFrame ini dapat digunakan untuk analisis lebih lanjut dalam proyek pengolahan data atau pembelajaran mesin.
## Unguided 

### 1. Load data (movie classification)

```python
# 1.
import pandas as pd
import numpy as np
```
mengimport library pandas disingkat sebagai pd dan numpy sebagai np
#### Output:

### 2. Cek nilai duplikat

```python
# 2.
file_path = 'Movie_classification.csv'
data = pd.read_csv(file_path)

# Memeriksa nilai duplikat
duplikat = data[data.duplicated()]

# Menampilkan baris yang duplikat
if not duplikat.empty:
    print("Enti duplikat ditemukan:")
    print(duplikat)
else:
    print("Tidak ada entri duplikat ditemukan.")
```
#### Output:

![image](https://github.com/yokaroo/IPSD-Asisgment-2/blob/main/Modul%202/ss%20output/Screenshot%202024-10-09%20011828.png)

Kode program di atas berfungsi untuk memeriksa nilai duplikat dalam sebuah file CSV yang bernama `Movie_classification.csv`. Pertama, variabel `file_path` menyimpan nama file yang akan dibaca. Kemudian, baris `data = pd.read_csv(file_path)` menggunakan fungsi `read_csv()` dari library **pandas** untuk membaca data dari file tersebut dan menyimpannya dalam variabel `data` sebagai sebuah DataFrame. Setelah data dimuat, kode selanjutnya memeriksa apakah terdapat nilai duplikat dalam DataFrame dengan menggunakan `data[data.duplicated()]`, yang menghasilkan DataFrame baru bernama `duplikat` yang berisi hanya baris-baris yang memiliki nilai duplikat. Selanjutnya, blok kondisi `if not duplikat.empty:` digunakan untuk memeriksa apakah DataFrame `duplikat` tidak kosong. Jika terdapat duplikat, program akan mencetak pesan "Enti duplikat ditemukan:" diikuti dengan menampilkan baris yang duplikat. Sebaliknya, jika tidak ada nilai duplikat yang ditemukan, program akan mencetak pesan "Tidak ada entri duplikat ditemukan." Ini memungkinkan pengguna untuk dengan mudah mengetahui apakah ada data yang terduplikasi dalam file CSV yang dianalisis.

### 3. Menemukan null values buat presentase

```python
# 3.
file_path = 'Movie_classification.csv'
data = pd.read_csv(file_path)

# Menghitung persentase nilai null di setiap kolom
persentase_null = data.isnull().mean() * 100

# Menampilkan persentase nilai null
print("Persentase nilai null di setiap kolom:")
print(persentase_null[persentase_null > 0])  # Menampilkan hanya kolom dengan nilai null
```
#### Output:

![image](https://github.com/yokaroo/IPSD-Asisgment-2/blob/main/Modul%202/ss%20output/Screenshot%202024-10-09%20011838.png)

Kode program di atas bertujuan untuk menghitung dan menampilkan persentase nilai null (kosong) dalam setiap kolom dari file CSV yang bernama `Movie_classification.csv`. Pertama, variabel `file_path` menyimpan nama file yang akan dibaca. Selanjutnya, baris `data = pd.read_csv(file_path)` menggunakan fungsi `read_csv()` dari library **pandas** untuk memuat data dari file tersebut ke dalam variabel `data`, yang berupa sebuah DataFrame. Setelah data dimuat, program menghitung persentase nilai null di setiap kolom dengan menggunakan `data.isnull().mean() * 100`. Fungsi `isnull()` menghasilkan DataFrame boolean yang menunjukkan nilai null, kemudian `mean()` menghitung rata-rata dari nilai tersebut (yang, dalam konteks ini, merepresentasikan proporsi nilai null). Hasilnya dikalikan dengan 100 untuk mendapatkan persentase. Terakhir, kode `print("Persentase nilai null di setiap kolom:")` mencetak judul, dan `print(persentase_null[persentase_null > 0])` menampilkan persentase nilai null hanya untuk kolom yang memiliki nilai null, sehingga pengguna dapat dengan mudah melihat di mana terdapat data yang hilang dalam dataset.

### 4. Drop missing value berdasarkan baris, kolom, imputasi dengan mean, modus, median

```python
# 4. 
# Menampilkan data sebelum penanganan nilai hilang
print("Data sebelum penanganan nilai hilang:")
print(data)

# 1. Menghapus baris yang memiliki nilai hilang
data_baris_dihapus = data.dropna()
print("\nData setelah menghapus baris yang memiliki nilai hilang:")
print(data_baris_dihapus)

# 2. Menghapus kolom yang memiliki nilai hilang
data_kolom_dihapus = data.dropna(axis=1)
print("\nData setelah menghapus kolom yang memiliki nilai hilang:")
print(data_kolom_dihapus)

# 3. Mengisi nilai yang hilang dengan mean untuk kolom numerik
data_mean_imputasi = data.fillna(data.mean())
print("\nData setelah imputasi dengan mean untuk kolom numerik:")
print(data_mean_imputasi)

# 4. Mengisi nilai yang hilang dengan modus untuk kolom kategorikal
for column in data.select_dtypes(include=['object']).columns:
    mode_value = data[column].mode()[0]  # Ambil modus
    data[column].fillna(mode_value, inplace=True)

print("\nData setelah imputasi dengan modus untuk kolom kategorikal:")
print(data)

# 5. Mengisi nilai yang hilang dengan median untuk kolom numerik
data_median_imputasi = data.fillna(data.median())
print("\nData setelah imputasi dengan median untuk kolom numerik:")
print(data_median_imputasi)
```
#### Output:

![image](https://github.com/yokaroo/IPSD-Asisgment-2/blob/main/Modul%202/ss%20output/Screenshot%202024-10-09%20011858.png)
![image](https://github.com/yokaroo/IPSD-Asisgment-2/blob/main/Modul%202/ss%20output/Screenshot%202024-10-09%20011910.png)
![image](https://github.com/yokaroo/IPSD-Asisgment-2/blob/main/Modul%202/ss%20output/Screenshot%202024-10-09%20011921.png)
![image](https://github.com/yokaroo/IPSD-Asisgment-2/blob/main/Modul%202/ss%20output/Screenshot%202024-10-09%20011935.png)
![image](https://github.com/yokaroo/IPSD-Asisgment-2/blob/main/Modul%202/ss%20output/Screenshot%202024-10-09%20011951.png)
![image](https://github.com/yokaroo/IPSD-Asisgment-2/blob/main/Modul%202/ss%20output/Screenshot%202024-10-09%20012005.png)
![image](https://github.com/yokaroo/IPSD-Asisgment-2/blob/main/Modul%202/ss%20output/Screenshot%202024-10-09%20012015.png)
![image](https://github.com/yokaroo/IPSD-Asisgment-2/blob/main/Modul%202/ss%20output/Screenshot%202024-10-09%20012025.png)
![image](https://github.com/yokaroo/IPSD-Asisgment-2/blob/main/Modul%202/ss%20output/Screenshot%202024-10-09%20012034.png)
![image](https://github.com/yokaroo/IPSD-Asisgment-2/blob/main/Modul%202/ss%20output/Screenshot%202024-10-09%20012052.png)
![image](https://github.com/yokaroo/IPSD-Asisgment-2/blob/main/Modul%202/ss%20output/Screenshot%202024-10-09%20012108.png)
![image](https://github.com/yokaroo/IPSD-Asisgment-2/blob/main/Modul%202/ss%20output/Screenshot%202024-10-09%20012117.png)
![image](https://github.com/yokaroo/IPSD-Asisgment-2/blob/main/Modul%202/ss%20output/Screenshot%202024-10-09%20012125.png)
![image](https://github.com/yokaroo/IPSD-Asisgment-2/blob/main/Modul%202/ss%20output/Screenshot%202024-10-09%20012132.png)
![image](https://github.com/yokaroo/IPSD-Asisgment-2/blob/main/Modul%202/ss%20output/Screenshot%202024-10-09%20012140.png)
![image](https://github.com/yokaroo/IPSD-Asisgment-2/blob/main/Modul%202/ss%20output/Screenshot%202024-10-09%20012242.png)

Kode program di atas bertujuan untuk menangani nilai hilang dalam dataset yang telah dimuat sebelumnya. Pertama, program menampilkan data sebelum dilakukan penanganan nilai hilang dengan mencetaknya ke konsol, sehingga pengguna dapat melihat kondisi awal dataset. Selanjutnya, langkah pertama adalah menghapus baris yang memiliki nilai hilang menggunakan `data.dropna()`, dan hasilnya disimpan dalam variabel `data_baris_dihapus`, yang kemudian juga dicetak untuk menunjukkan perubahan yang terjadi setelah baris-baris tersebut dihapus. 

Langkah kedua adalah menghapus kolom yang memiliki nilai hilang, yang dilakukan dengan `data.dropna(axis=1)`, dan hasilnya disimpan dalam variabel `data_kolom_dihapus`. Setelah itu, program mencetak hasil untuk menunjukkan data setelah kolom dengan nilai hilang dihapus. 

Langkah ketiga adalah mengisi nilai hilang pada kolom numerik dengan rata-rata kolom tersebut menggunakan `data.fillna(data.mean())`, dan hasilnya disimpan dalam variabel `data_mean_imputasi`, yang juga dicetak. 

Selanjutnya, langkah keempat berfokus pada kolom kategorikal; program menggunakan loop untuk mengidentifikasi kolom-kolom tersebut dan mengisi nilai hilang dengan modus (nilai yang paling sering muncul) dari masing-masing kolom. Hasil perubahan ini kemudian ditampilkan.

Akhirnya, langkah kelima mengisi nilai hilang dalam kolom numerik dengan median menggunakan `data.fillna(data.median())`, dan hasilnya disimpan dalam variabel `data_median_imputasi`, yang juga dicetak. Dengan demikian, program ini secara menyeluruh menangani nilai hilang dalam dataset dengan berbagai metode, baik dengan menghapus maupun mengisi nilai hilang.

### 5. Export data ke csv dan excel
```python
# 5. 
data.to_excel('Movie_classification.xlsx') # mengubah data ke excel
```
```python
data.to_csv('Movie_classification.csv') # mengubah data menjadi csv
```
#### Output:

## Kesimpulan
Kesimpulan dari materi tersebut menunjukkan pentingnya pemeriksaan dan penanganan data dalam analisis. Kode yang digunakan memuat file CSV dan memeriksa data untuk menemukan nilai duplikat serta nilai null, yang merupakan langkah penting untuk memastikan integritas dan kualitas data sebelum analisis lebih lanjut. Beberapa metode diterapkan untuk menangani nilai hilang dalam dataset, termasuk menghapus baris dan kolom yang memiliki nilai hilang, serta mengisi nilai hilang dengan rata-rata, modus, dan median untuk kolom numerik dan kategorikal. Penggunaan teknik imputasi untuk mengisi nilai yang hilang membantu menjaga jumlah data tetap utuh, yang sangat penting dalam analisis data dan pembelajaran mesin. Hasil akhir dari proses ini adalah dataset yang lebih bersih dan siap untuk dianalisis. Secara keseluruhan, langkah-langkah tersebut menekankan pentingnya pembersihan dan persiapan data dalam analisis agar hasil yang diperoleh lebih akurat dan dapat diandalkan.

## Referensi
[1] F. V. P. Samosir, L. P. Mustamu, E. D. Anggara, A. I. Wiyogo, and A. Widjaja, “Exploratory Data Analysis terhadap Kepadatan Penumpang Kereta Rel Listrik”, JuTISI, vol. 7, no. 2, pp. 449 –, Aug. 2021.
