# Dashboard TBC Kota Bandung 2021–2026

Situs **statis** (HTML + JS + JSON agregat) hasil akhir analisis kaskade & investigasi kontak
pasien TBC Kota Bandung — Penelitian Unpad. **Tidak** memuat data mentah, database, atau data
individu/PII; hanya angka agregat yang dibutuhkan untuk tampilan.

Live: **https://rdwnilyas-coder.github.io/sitb-bandung-dashboard/**

## Halaman
- `index.html` — **dashboard utama** (peta kaskade spasio-temporal, drill-down, faskes, tren) = root situs
- `cascade_spatial.html` — salinan dashboard utama (untuk tautan langsung / balik dari alur)
- `alur_proses.html` — diagram alur proses kaskade + Investigasi Kontak
- `struktur.html` — pohon struktur data (kolom & missing value)

Data tampilan ada di `data/*.json` dan `data/geo/*` (agregat; regenerasi dari pipeline riset di repo terpisah).

## Deploy ke GitHub Pages (akun rdwnilyas-coder)

1. Buat repo kosong `sitb-bandung-dashboard` di https://github.com/new (owner: **rdwnilyas-coder**, public).
2. Dari folder ini:
   ```bash
   git remote add origin https://github.com/rdwnilyas-coder/sitb-bandung-dashboard.git
   git push -u origin main
   ```
3. Di repo GitHub → **Settings → Pages** → Source: **Deploy from a branch** → Branch: **main**, folder **/(root)** → Save.
4. Tunggu ±1 menit, situs live di URL di atas.

> Alternatif via GitHub CLI: `gh repo create rdwnilyas-coder/sitb-bandung-dashboard --public --source=. --push`
> lalu aktifkan Pages: `gh api -X POST repos/rdwnilyas-coder/sitb-bandung-dashboard/pages -f build_type=legacy -f 'source[branch]=main' -f 'source[path]=/'`

Semua path di HTML bersifat **relatif** (`data/x.json`), jadi jalan di sub-path `…github.io/sitb-bandung-dashboard/`.
File `.nojekyll` menonaktifkan Jekyll agar semua aset disajikan apa adanya.
