# Analisis Perbaikan

## Permasalahan 1

### Gejala

Perintah `docker compose up -d` gagal dijalankan dan menampilkan error parsing pada file `docker-compose.yml`.

### Penyebab

Bagian `services` tidak diakhiri dengan tanda titik dua (`:`) sehingga sintaks YAML tidak valid.

### Solusi

Mengubah `services` menjadi `services:` agar file dapat dibaca oleh Docker Compose.

---

## Permasalahan 2

### Gejala

Container `web1` tidak dapat terhubung ke database.

### Penyebab

Nilai `DB_HOST` menggunakan `mysql`, sedangkan nama service database yang benar adalah `db`.

### Solusi

Mengubah `DB_HOST` menjadi `db`.

---

## Permasalahan 3

### Gejala

Container `web2` gagal melakukan koneksi ke database.

### Penyebab

Password database pada `web2` menggunakan nilai `wrongpassword`.

### Solusi

Mengubah `DB_PASS` menjadi `student123` agar sesuai dengan konfigurasi database.

---

## Permasalahan 4

### Gejala

Docker gagal melakukan build pada service `web3`.

### Penyebab

Build context mengarah ke folder `web33` yang tidak tersedia.

### Solusi

Mengubah `context: ./web33` menjadi `context: ./web3`.

---

## Permasalahan 5

### Gejala

Nginx tidak dapat mengakses service `web3`.

### Penyebab

Container `web3` hanya terhubung ke network `backend` dan tidak terhubung ke network `frontend`.

### Solusi

Menambahkan network `frontend` pada service `web3`.

---

## Permasalahan 6

### Gejala

Konfigurasi volume tidak konsisten.

### Penyebab

Service database menggunakan volume `db-data`, sedangkan deklarasi volume menggunakan nama `database-data`.

### Solusi

Menyamakan nama volume menjadi `db-data`.

---

## Permasalahan 7

### Gejala

Container `nginx-lb` gagal dijalankan.

### Penyebab

File `nginx.conf` masih mengandung markdown code fence berupa ` ```nginx ` dan ` ``` `.

### Solusi

Menghapus seluruh code fence sehingga hanya tersisa konfigurasi Nginx yang valid.

---

## Permasalahan 8

### Gejala

Docker gagal melakukan build image `web1`.

### Penyebab

Dockerfile menggunakan image `php:8.2-apach` yang tidak tersedia.

### Solusi

Mengubah image menjadi `php:8.2-apache`.

---

## Permasalahan 9

### Gejala

Docker gagal melakukan build image `web3`.

### Penyebab

Dockerfile menggunakan image `php:8.2-apche` yang tidak tersedia.

### Solusi

Mengubah image menjadi `php:8.2-apache`.

---

## Permasalahan 10

### Gejala

Label halaman pada service `web2` tidak sesuai.

### Penyebab

Teks yang ditampilkan adalah `WEB-WEB` bukan `WEB-2`.

### Solusi

Mengubah label menjadi `WEB-2`.

---

## Permasalahan 11

### Gejala

Label halaman pada service `web3` tidak sesuai.

### Penyebab

Teks yang ditampilkan adalah `WEB-WOB` bukan `WEB-3`.

### Solusi

Mengubah label menjadi `WEB-3`.

---

## Permasalahan 12

### Gejala

Inisialisasi database berpotensi gagal dijalankan.

### Penyebab

File `init.sql` masih mengandung markdown code fence ` ```sql ` dan ` ``` `.

### Solusi

Menghapus code fence sehingga file hanya berisi perintah SQL yang valid.
