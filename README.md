# Desyana Kitchen — Telegram AI Bot (Python)

Bot Telegram customer service untuk Desyana Kitchen. Proyek ini ditulis dengan Python, menggunakan Telegram Bot API melalui `python-telegram-bot`, dan memanggil model AI melalui OpenRouter.

## Fitur
- Menjawab pertanyaan pelanggan menggunakan model AI.
- `/start`, `/menu`, `/help`, dan `/reset`.
- Menggunakan data menu dan FAQ dari file JSON.
- Menyimpan konteks percakapan singkat hanya selama sesi bot berjalan.
- Menangani error API tanpa membocorkan token atau detail rahasia.

## Teknologi
- Python 3.10+
- python-telegram-bot
- OpenRouter API
- httpx
- python-dotenv

## 1. Buat bot Telegram
1. Buka Telegram dan cari akun resmi `@BotFather`.
2. Kirim `/newbot` dan ikuti instruksi.
3. Simpan token bot secara privat. Jangan masukkan token ke kode atau README.

Jika kamu sudah punya bot Telegram, kamu bisa menggunakan token bot yang sudah ada. Jangan jalankan bot polling yang sama di dua program sekaligus; hentikan program lama terlebih dahulu untuk menghindari konflik polling.

## 2. Siapkan OpenRouter
1. Masuk ke https://openrouter.ai/ dan buat API key.
2. Periksa harga dan status model sebelum digunakan. ID `openai/gpt-oss-120b:free` di contoh ini ditujukan untuk model berlabel gratis, tetapi ketersediaan dan batas pemakaiannya dapat berubah.
3. API key tetap rahasia. Jangan pernah mengunggahnya ke GitHub.

## 3. Instalasi di Ubuntu / WSL
Masuk ke folder proyek, lalu jalankan:

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
cp .env.example .env
nano .env
```

Isi `.env`:
- `TELEGRAM_BOT_TOKEN` — token dari BotFather.
- `OPENROUTER_API_KEY` — API key dari OpenRouter.
- `OPENROUTER_MODEL` — ID model yang ingin dipakai.

Simpan file di nano dengan `Ctrl+O`, Enter, lalu keluar dengan `Ctrl+X`.

## 4. Jalankan bot

```bash
python bot.py
```

Buka chat bot di Telegram dan kirim `/start`, kemudian coba `/menu` atau ajukan pertanyaan. Hentikan bot dengan `Ctrl+C`.

## 5. Ubah data Desyana Kitchen
Edit:
- `data/menu.json` untuk menu dan harga.
- `data/faq.json` untuk informasi bisnis.

**Data di repository ini adalah contoh, bukan informasi resmi.** Ganti nomor WhatsApp `6281234567890`, harga, stok, jam operasional, pembayaran, dan pengiriman dengan data yang sudah diverifikasi sebelum dipakai pelanggan. Jangan biarkan bot mengklaim pesanan telah dikonfirmasi.

## 6. Unggah ke GitHub
Repository GitHub proyek ini tersedia di:
https://github.com/ratuayuysiana/project-chatbot

Untuk mengunggah perubahan terbaru, buka terminal di folder proyek dan jalankan:

git status
git add README.md
git commit -m "docs: update README project documentation"
git push origin main

Periksa perubahan menggunakan git status sebelum melakukan commit. Pastikan file .env dan informasi rahasia lainnya tidak ikut diunggah ke GitHub.

Jika perubahan mencakup file lain selain README, tambahkan hanya file yang memang ingin di-commit.

Jangan menjalankan git init atau git remote add origin lagi jika repository lokal sudah terhubung ke GitHub.
## Struktur proyek

```text
project-chtbot/
├── bot.py
├── requirements.txt
├── .env.example
├── .gitignore
├── README.md
└── data/
    ├── menu.json
    └── faq.json
```

## Batasan
- Bot membutuhkan koneksi internet dan layanan OpenRouter.
- Model gratis dapat memiliki batas kuota, rate limit, atau berubah ketersediaannya.
- Bot ini belum menyimpan pesanan ke database, memproses pembayaran, memeriksa stok real-time, atau mengirim notifikasi admin.
- Jangan jalankan token bot dan API key pada lingkungan yang tidak tepercaya.
