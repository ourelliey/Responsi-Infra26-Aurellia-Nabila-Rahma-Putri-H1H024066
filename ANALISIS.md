# Analisis Responsi Infrastruktur Teknologi Informasi

**Nama:** Aurellia Nabila Rahma Putri  
**NIM:** H1H024066

---

## Temuan Bug dan Penanganannya

### Bug #1 — Syntax Error: `services` Tanpa Titik Dua
| | |
|---|---|
| **Gejala** | `docker compose` gagal dijalankan |
| **Root Cause** | Keyword `services` tidak diakhiri tanda titik dua (`:`) |
| **Fix** | Ubah menjadi `services:` |

---

### Bug #2 — `DB_HOST` Salah pada web1
| | |
|---|---|
| **Gejala** | web1 tidak bisa terhubung ke database |
| **Root Cause** | `DB_HOST` bernilai `mysql`, sedangkan nama service yang benar adalah `db` |
| **Fix** | Ubah `DB_HOST` menjadi `db` |

---

### Bug #3 — Password Database Salah pada web2
| | |
|---|---|
| **Gejala** | web2 gagal autentikasi ke database |
| **Root Cause** | `DB_PASS` diisi `wrongpassword` |
| **Fix** | Ubah `DB_PASS` menjadi `student123` |

---

### Bug #4 — Context Path Salah pada web3
| | |
|---|---|
| **Gejala** | Docker gagal melakukan build image web3 |
| **Root Cause** | Context mengarah ke `./web33` yang tidak ditemukan |
| **Fix** | Ubah path menjadi `./web3` |

---

### Bug #5 — web3 Tidak Tergabung ke Network Frontend
| | |
|---|---|
| **Gejala** | Nginx tidak dapat menjangkau web3 |
| **Root Cause** | web3 hanya terdaftar di network `backend`, tidak di `frontend` |
| **Fix** | Tambahkan `frontend` ke daftar networks pada service web3 |

---

### Bug #6 — Nama Volume Tidak Konsisten
| | |
|---|---|
| **Gejala** | Docker gagal melakukan mount volume database |
| **Root Cause** | Volume didefinisikan sebagai `database-data` tetapi direferensikan sebagai `db-data` |
| **Fix** | Seragamkan nama volume menjadi `db-data` |

---

### Bug #7 — Upstream Server web1 Typo di Konfigurasi Nginx
| | |
|---|---|
| **Gejala** | Nginx tidak dapat meneruskan request ke web1 |
| **Root Cause** | Nama server ditulis `web11` (kelebihan satu karakter) |
| **Fix** | Ubah menjadi `web1:80` |

---

### Bug #8 — Port Upstream web3 Salah di Konfigurasi Nginx
| | |
|---|---|
| **Gejala** | Nginx tidak dapat meneruskan request ke web3 |
| **Root Cause** | Port web3 ditulis `8080`, seharusnya `80` |
| **Fix** | Ubah menjadi `web3:80` |

---

### Bug #9 — Typo Nama Image di Dockerfile web1
| | |
|---|---|
| **Gejala** | Docker gagal melakukan build web1 |
| **Root Cause** | Nama image ditulis `php:8.2-apach` (kurang huruf `e`) |
| **Fix** | Ubah menjadi `php:8.2-apache` |

---

### Bug #10 — Typo Nama Image di Dockerfile web3
| | |
|---|---|
| **Gejala** | Docker gagal melakukan build web3 |
| **Root Cause** | Nama image ditulis `php:8.2-apche` (huruf tertukar) |
| **Fix** | Ubah menjadi `php:8.2-apache` |

---

### Bug #11 — Hardcoded Container Name Salah di `index.php` web2
| | |
|---|---|
| **Gejala** | Output web2 menampilkan `WEB-WEB` |
| **Root Cause** | String nama container di-hardcode dengan nilai yang salah |
| **Fix** | Ubah menjadi `WEB-2` |

---

### Bug #12 — Hardcoded Container Name Salah di `index.php` web3
| | |
|---|---|
| **Gejala** | Output web3 menampilkan `WEB-WOB` |
| **Root Cause** | String nama container di-hardcode dengan nilai yang salah |
| **Fix** | Ubah menjadi `WEB-3` |

---

### Bug #13 — Variabel Nama dan NIM Belum Diisi
| | |
|---|---|
| **Gejala** | Output menampilkan nilai placeholder |
| **Root Cause** | Variabel `$nama` dan `$nim` di `index.php` masih kosong atau berisi placeholder |
| **Fix** | Isi dengan nama dan NIM praktikan yang sesuai |
