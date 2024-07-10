
# 215610061 - Novit Saputri - Responsi UAS Praktikum Teknologi Cloud

Membuat website sederhana


### 1. Persiapan

#### 1.1 Membuat 2 direktori : website utama dan website profil.
```bash
    mkdir website-utama
    cd website-utama
    mkdir website-profil
    cd website-profil
```

#### 1.2 Di dalam website-utama :
##### Buat file index.html
```bash
    nano index.html
```
Lalu masukkan script pada file index.html

```bash
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Halaman Utama</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            padding: 20px;
            max-width: 600px;
            margin: 0 auto;
        }
        h1 {
            text-align: center;
        }
        p {
            margin-bottom: 10px;
        }
        a {
            display: block;
            margin-top: 20px;
            text-align: center;
            text-decoration: none;
            background-color: #007bff;
            color: #fff;
            padding: 10px 20px;
            border-radius: 5px;
            transition: background-color 0.3s ease;
        }
        a:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>
    <h1>Halaman Utama</h1>
    <p>Nama Lengkap: Novit Saputri</p>
    <p>NIM: 215610061</p>
    <p>Program Studi: Sistem Informasi</p>
    <p>Hobi: Menonton Film</p>
    <a href="/profil">Profil</a>
</body>
</html>
```

#### pastikan link benar mengarah ke profil
```bash
<a href="https://8f61cc0b-b562-474a-9d64-4ca775a6c7aa-10-244-7-242-8081.papa.r.killercoda.com/">Profil</a>
```

#### 1.3 Di dalam website-profil, letakkan file gambar di profil anda (foto.jpg)

```bash
cd website-profil
nano index.html
```

##### lalu masukkan script pada file index.html untuk website-profil
#### 1.4 lanjut mengupload foto.jpg

```bash
wget --no-check-certificate 'https://docs.google.com/uc?export=download&id=1jmOEj2oJFbYrOUdzPkoVA7aviIOQl03Y' -O nama_file.ext
```
##### Setelah itu buat index.html pada website profil

### 2. Docker Network (Modul 13)

#### 2.1 Buat jaringan Docker dengan nama my-novit-network
```bash
$ docker network create my-novit-network
```

### 3. Dockerfile dan Image (Modul 11&12)
#### 3.1 Dockerfile untuk Website Utama (direktori website-utama)
```bash
FROM nginx:latest 
$ mkdir website-utama
$ cd website-utama
$ nano index.html
```

#### 3.2 Dockerfile untuk Website Profil (direktori website-profil)
```bash
FROM nginx:latest 
$ mkdir website-profil
$ cd website-profil
$ nano index.html
```

### 4. Build Image
#### 4.1 Bangun dua Docker dari Dockerfile yang sudah dibuat. Berikan nama yang jelas untuk setiap image (website-utama, website-profil)
##### website-utama
```bash
docker build -t website-utama .
```
##### website-profil
```bash
docker build -t website-profil .
```

### 5. Docker Volume (Modul 14) Opsional
#### 5.1 Tantangan Tambahan
##### Buat volume bernama profile-images
```bash
docker volume create profile-images
```
##### Konfigurasikan agar container website utama dan profil mengakses gambar profil melalui volume ini.

### 6. Menjalankan Container (Modul 9 & 10)
#### 6.1 Jalankan container dengan menyambungkan ke docker network yang sudah kalian buat sebelumnya
##### Jalankan Container Website Utama
```bash
docker run -d --name website-utama -network my-novit-network -o 8080:80 website-utama
```
##### Jalankan Container Website Profil
```bash
docker run -d --name website-profil -network my-novit-network -o 8081:80 website-profil
```

### 7. Pengujian
#### 7.1 Akses website
##### 1. Membuka traffic port acces pada killercoda ubuntu.
##### 2. Akses halaman utama di: https://localhost:8080. akan menampilkan website data diri /
##### 3. Klik halaman profil untuk bernavigasi ke "Halaman Profil"
##### 4. Akan menampilkan halaman profil




