# 🛠️ PANDUAN MODE GURU - LUDO DATA STRUCTURE

## 🔐 CARA MENGAKTIFKAN

Mode Guru **HANYA** aktif jika URL memiliki parameter `?debug=1`:

```
file:///C:/path/to/Ludo%20Data%20Structure%20(1).html?debug=1
```

### ⚠️ PENTING
- Parameter harus **persis** `?debug=1` (huruf kecil, angka 1)
- Parameter lain seperti `?debug=0`, `?debug=true`, `?debug=` **TIDAK** akan mengaktifkan Mode Guru
- Tanpa parameter, **TIDAK ADA** kode, elemen, atau fungsi debug yang dimuat

---

## 🎯 TUJUAN MODE GURU

Memungkinkan guru untuk:
1. ✅ Mengecek seluruh media dan konten tanpa harus bermain game sampai selesai
2. ✅ Melihat **semua tahapan kondisi menang** step-by-step
3. ✅ Memvalidasi soal dan audio
4. ✅ Monitoring log aktivitas dan error

---

## 📱 TAMPILAN MODE GURU

### Badge Debug (Pojok Kiri Bawah)
- Badge kuning dengan teks **"🛠️ DEBUG"**
- Klik untuk membuka/tutup panel Mode Guru
- Selalu visible saat Mode Guru aktif

### Panel Mode Guru (Bottom Sheet)
- Muncul dari bawah layar
- Maksimal 52% tinggi viewport
- Scrollable untuk konten panjang
- 4 Tab utama

---

## 🏆 TAB 1: MENANG

**Fungsi:** Testing lengkap kondisi menang dan semua tahapannya

### Kontrol Awal
- **Pemain:** Pilih 2, 3, atau 4 pemain
- **Pemenang:** Pilih pemain mana yang akan menang
- **Dadu:** Set nilai dadu (1-6) untuk langkah terakhir

### 7 Tahap Kondisi Menang

#### ✅ Tahap 1: Siapkan Papan
- Membuat game baru dengan N pemain
- Menempatkan pion pemenang di posisi 55 (1 langkah sebelum pusat)
- Set skor: pemenang rendah, yang lain tinggi
- Giliran diset ke pemain pemenang

#### ✅ Tahap 2: Lempar Dadu
- Animasi dadu berputar
- Suara "beep" saat lempar
- Nilai dadu sesuai yang dipilih

#### ✅ Tahap 3: Pion Bergerak ke Pusat
- Pion bergerak dari pos 55 → 56 (pusat papan)
- Animasi smooth transition
- Posisi pion di tengah papan dengan offset per pemain

#### ✅ Tahap 4: Efek di Papan
- Pion berputar dengan animasi `win`
- Konfeti burst dari posisi pion
- Fanfare (6 nada musik naik)

#### ✅ Tahap 5: Poin +200 dan Notifikasi
- Skor pemain +200
- Toast notification: "🏁 [Nama] sampai pusat! +200"
- HUD diupdate

#### ✅ Tahap 6: Game Berakhir
- Panggil fungsi `finish(pemenang)`
- Layar hasil muncul (tapi animasi pemenang ditahan)
- Data ranking disiapkan

#### ✅ Tahap 7: Animasi Pemenang
- Kartu emas dengan animasi pop-in
- Mahkota turun dari atas
- Nama pemenang dengan glow effect
- Podium 3D dengan animasi naik
- Konfeti penuh layar
- Shine effect pada kartu

### Tombol Kontrol

#### ▶ Langkah Berikutnya
- Jalankan 1 tahap berikutnya
- Caption muncul di atas layar menjelaskan tahap
- Panel otomatis hide, tombol "Lanjut" muncul di caption

#### ⏩ Putar Otomatis
- Jalankan semua 7 tahap berturut-turut
- Delay 1.5 detik antar tahap (1.8 detik untuk tahap 4)
- Panel hide selama pemutaran
- Panel muncul lagi setelah selesai

#### ↺ Reset
- Kembali ke tahap 0
- Caption hilang
- Siap untuk run ulang

### Lompat Langsung (Skenario Cepat)

#### Menang Lewat Pusat
- Langsung ke layar hasil dengan pemenang via pusat
- Pion di posisi 56, skor +200
- Animasi pemenang langsung muncul

#### Waktu Habis (Skor Beda)
- Simulasi: 20 menit habis, pemenang skor tertinggi
- Pion belum sampai pusat
- Tidak ada pemain khusus yang menang via pusat

#### Waktu Habis (Skor Seri)
- 2 pemain dengan skor sama tertinggi
- Log: "PERINGATAN: skor seri. Pemenang hanya ditentukan urutan pemain"
- Menunjukkan edge case belum sempurna

#### 🔁 Ulang Animasi Pemenang
- Replay tahap 7 saja (animasi pemenang)
- Harus jalankan skenario menang dulu
- Berguna untuk demo atau screenshot

---

## 🖥️ TAB 2: LAYAR & MEDIA

**Fungsi:** Navigasi cepat dan testing audio/visual

### Buka Layar
9 tombol untuk langsung ke layar:
- **Splash** → Layar pembuka
- **Menu** → Menu utama dengan tiles
- **Materi** → Penjelasan Tree & Graph
- **Cara Bermain** → Aturan dan poin
- **Tentang** → Tujuan pembelajaran
- **Lab Praktik** → Interactive diagrams
- **Pilih Pemain** → Setup pemain
- **Papan (game uji)** → Mulai game 2 pemain otomatis
- **Hasil (demo menang)** → Langsung ke skenario menang

### Audio & Dukungan

#### 🔊 Tes Suara
- Memutar kalimat: "Halo, ini tes suara untuk materi struktur data."
- Menggunakan suara Indonesia jika tersedia
- Fallback ke suara default browser

#### Tes Efek Bunyi
- **Klik** (700 Hz)
- **Benar** (1000 Hz)
- **Salah** (300 Hz)
- **Fanfare** (6 nada musik)

#### Info Dukungan
```
Web Speech: ✅ atau ❌
Suara Indonesia: ✅ N atau ⚠️ tidak ditemukan
Web Audio: ✅ atau ❌
Layar: [width]×[height]
```

---

## ❓ TAB 3: SOAL

**Fungsi:** Validasi dan testing bank soal

### Statistik Soal
```
28 soal · Tree 10 · Graph 10 · Mix 8 · Sulit 10
Posisi kunci di data (A/B/C/D): X / X / X / X
✅ Validasi otomatis lolos
```
atau
```
⚠️ N soal perlu dicek
```

### Daftar Soal
Setiap soal menampilkan:
- **Nomor** [kategori⚡jika sulit]
- **Teks soal** (70 karakter pertama)
- **Kunci jawaban** dengan tanda ✓
- **Peringatan validasi** (jika ada)
- **Tombol Uji**

### Validasi Otomatis

Setiap soal dicek untuk:

1. ❌ **Kunci di luar jangkauan**
   - Indeks jawaban < 0 atau >= jumlah opsi
   
2. ❌ **Opsi duplikat**
   - Ada 2 opsi dengan teks yang sama
   
3. ❌ **Tanpa penjelasan**
   - Field penjelasan kosong
   
4. ❌ **Jawaban muncul di soal**
   - Teks jawaban (>4 huruf) muncul di teks soal
   - Bisa bocor jawaban ke siswa

### Tombol Uji
- Menampilkan soal seperti yang dilihat siswa
- Timer berjalan normal
- Opsi diacak
- Tidak memengaruhi skor game utama
- Game uji 2 pemain dibuat otomatis jika belum ada

---

## 📜 TAB 4: LOG

**Fungsi:** Monitoring aktivitas dan error

### Fitur
- **80 log terakhir** ditampilkan (dari 300 yang disimpan)
- **Format:** `[HH:MM:SS] pesan`
- **Warna:** Error merah, normal hitam

### Yang Di-log
1. ✅ Aktivitas Mode Guru (tahap, skenario)
2. ✅ Giliran permainan
3. ✅ Lempar dadu dan pergerakan pion
4. ✅ Soal ditampilkan
5. ✅ Jawaban (benar/salah/waktu habis)
6. ✅ Game selesai
7. ✅ **Error JavaScript** (via event listener)

### Tombol
- **Salin Log:** Copy semua log ke clipboard
- **Hapus:** Clear log (langsung tampil "(kosong)")

---

## 🎨 ANIMASI PEMENANG (Detail)

### Kartu Emas (`#winbox`)
```css
- Background: gradien emas (#ffe27a → #f4b400)
- Border: 4px solid var(--ink)
- Shadow: 0 6px 0
- Animation: pop-in (scale 0→1, rotate -12deg→0)
- Shine effect: sliding gradient overlay
```

### Mahkota 👑
```css
- Font-size: 2.6rem
- Animation: crown (turun dari atas, rotate, fade in)
- Delay: 0.5s
```

### Nama Pemenang
```css
- Font-size: clamp(2rem, 9vw, 3.2rem)
- Stroke: 2px var(--ink)
- Warna: sesuai pemain
- Animation: glow (pulse scale 1→1.08)
```

### Podium 3D
```css
- 3 kolom dengan tinggi berbeda
- Animation: rise (height 0→var(--h))
- Timing: 0.8s cubic-bezier
- Border radius: 12px atas
- Warna: sesuai pemain
```

### Konfeti
- Particle burst dari posisi pion
- 90 partikel
- Warna acak (merah, hijau, kuning, biru)
- Gravity dan fade out

---

## 🔧 IMPLEMENTASI TEKNIS

### Isolasi Kode
```javascript
(function() {
  if (new URLSearchParams(location.search).get('debug') !== '1') return;
  // Semua kode Mode Guru di dalam IIFE ini
})();
```

### Event Handling
- ❌ Tidak ada `onclick` di HTML
- ✅ Semua event via `addEventListener`
- ✅ Menggunakan `data-a` attribute
- ✅ Event delegation pada panel

```javascript
P.addEventListener('click', run);
// run mencari [data-a] dan memanggil fungsi
```

### Tidak Ada Global Pollution
- ❌ Tidak ada `window.debugHooks`
- ❌ Tidak ada variabel di global scope
- ✅ Semua dalam closure IIFE
- ✅ Intercept fungsi game via wrapping

### Intercept Functions
```javascript
// Wrap fungsi untuk logging tanpa ubah behaviour
const origRoll = roll;
roll = function(...args) {
  log('lempar dadu');
  return origRoll.apply(this, args);
};
```

### Dynamic Elements
```javascript
const style = createElement('style');
style.textContent = `...CSS...`;
document.head.appendChild(style);
```

---

## 📊 STATISTIK SOAL

### Distribusi Kategori
- **Tree:** 10 soal (35.7%)
- **Graph:** 10 soal (35.7%)
- **Mix:** 8 soal (28.6%)

### Distribusi Kesulitan
- **Mudah:** 18 soal (64.3%)
- **Sulit (⚡):** 10 soal (35.7%)

### Distribusi Posisi Jawaban
Ideal: ~25% untuk masing-masing A, B, C, D
(dicek di Mode Guru untuk memastikan tidak ada bias)

---

## 🐛 DEBUGGING TIPS

### Jika Mode Guru Tidak Muncul
1. ✅ Cek URL, pastikan ada `?debug=1`
2. ✅ Refresh halaman (Ctrl+R atau F5)
3. ✅ Buka Console (F12), cek error JavaScript
4. ✅ Pastikan browser support (Chrome/Edge/Firefox)

### Jika Animasi Tidak Jalan
1. ✅ Cek browser setting "Reduce motion"
2. ✅ Pastikan tidak ada CSS override
3. ✅ Cek Console untuk error

### Jika Suara Tidak Keluar
1. ✅ Cek volume browser dan sistem
2. ✅ Klik area page dulu (browser policy)
3. ✅ Cek Tab 2 info suara Indonesia
4. ✅ Browser Safari: suara terbatas

---

## 📝 CATATAN PENGEMBANG

### Untuk Menghapus Mode Guru
Hapus blok kode antara:
```javascript
// ===== MODE GURU =====
...
// ===== AKHIR MODE GURU =====
```

### File Terlibat
- `Ludo Data Structure (1).html` - File dengan Mode Guru (minified)
- `Ludo Data Structure.html` - File rapi tanpa Mode Guru (opsional)

### Ukuran Impact
- Mode Guru menambah ~8KB (gzip)
- Tidak mempengaruhi performa game normal
- Lazy load: kode hanya dieksekusi jika `?debug=1`

---

## ✅ CHECKLIST TESTING MODE GURU

### Testing Awal
- [ ] Buka tanpa parameter → tidak ada badge
- [ ] Buka dengan `?debug=1` → badge muncul
- [ ] Klik badge → panel muncul
- [ ] Semua tab bisa dibuka

### Testing Tab Menang
- [ ] Ubah jumlah pemain → reset berhasil
- [ ] Ubah pemenang → update berhasil
- [ ] ▶ Langkah berikutnya → caption muncul, tahap jalan
- [ ] ⏩ Putar otomatis → semua tahap jalan otomatis
- [ ] ↺ Reset → kembali ke tahap 0
- [ ] Lompat: Menang lewat pusat → animasi lengkap
- [ ] Lompat: Waktu habis → no winner specified
- [ ] Lompat: Skor seri → peringatan di log
- [ ] 🔁 Ulang animasi → replay animation

### Testing Tab Layar & Media
- [ ] Semua 9 tombol layar berfungsi
- [ ] 🔊 Tes suara → terdengar
- [ ] Efek bunyi → semua bunyi terdengar
- [ ] Info dukungan → data benar

### Testing Tab Soal
- [ ] Statistik benar
- [ ] Validasi berjalan
- [ ] Daftar soal lengkap
- [ ] Tombol Uji → soal muncul dengan timer

### Testing Tab Log
- [ ] Log aktivitas tercatat
- [ ] Salin log → clipboard berisi text
- [ ] Hapus → log kosong

### Testing Kondisi Menang (Paling Penting!)
- [ ] Tahap 1: Papan siap, pion di pos 55
- [ ] Tahap 2: Dadu berputar dan berhenti
- [ ] Tahap 3: Pion ke pusat (pos 56)
- [ ] Tahap 4: Konfeti burst, fanfare terdengar
- [ ] Tahap 5: Skor +200, toast muncul
- [ ] Tahap 6: Layar hasil muncul
- [ ] Tahap 7: Kartu emas, mahkota, podium, konfeti penuh

---

## 🎓 UNTUK GURU

### Persiapan Sebelum Kelas
1. Buka Mode Guru di komputer/laptop
2. Test semua layar (Tab 2)
3. Test audio (suara Indonesia)
4. Test beberapa soal acak (Tab 3)
5. Run kondisi menang sekali (Tab 1)

### Saat Demo di Kelas
1. Tampilkan layar normal (tanpa `?debug=1`) untuk siswa
2. Gunakan Mode Guru di layar guru untuk monitoring
3. Jika ada pertanyaan "bagaimana kalau menang?", gunakan Tab 1

### Troubleshooting di Kelas
- Siswa: "Suara tidak keluar" → Cek Tab 2, pastikan suara ada
- Siswa: "Soal tidak muncul" → Cek Tab 3, test soal
- Siswa: "Game error" → Cek Tab 4, lihat log error

---

## 🚀 FITUR LANJUTAN (Future)

Ide untuk pengembangan Mode Guru:
- [ ] Export/import state game
- [ ] Rekam session dan replay
- [ ] Statistik jawaban siswa (aggregated)
- [ ] Editor soal inline
- [ ] Testing multi-device (mobile, tablet)

---

**Dibuat dengan ❤️ untuk guru yang peduli kualitas media pembelajaran**

*Versi: 1.0 | Update: Desember 2024*
