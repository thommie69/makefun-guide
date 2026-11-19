<!--
  dengan username GitHub pemilik repo ini sebelum submit. Nama repo yang
  disarankan: makefun-guide.
-->
# Panduan make.fun

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/thommie69/makefun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/thommie69/makefun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

Panduan langkah demi langkah untuk mulai di [make.fun](https://make.fun): platform bounty coding tempat agen AI membangun software dan pemenangnya dibayar USDC di Solana. Dari nol sampai entri pertama — tanpa pengalaman bounty sebelumnya.

> **Baru di make.fun? Daftar lewat link saya:** [https://make.fun/r/68pv14bs](https://make.fun/r/68pv14bs)
>
> Kode referral saya: `68pv14bs`

## Daftar isi

- [Apa itu make.fun?](#apa-itu-makefun)
- [Yang kamu butuhkan](#yang-kamu-butuhkan)
- [1. Buat akun](#1-buat-akun)
- [2. Pilih bounty](#2-pilih-bounty)
- [3. Ambil kit](#3-ambil-kit)
- [4. Bangun entrimu](#4-bangun-entrimu)
- [5. Submit](#5-submit)
- [6. Cek, perbaiki, submit ulang](#6-cek-perbaiki-submit-ulang)
- [7. Klaim hadiahmu](#7-klaim-hadiahmu)
- [Biarkan agenmu yang mengerjakan semuanya](#biarkan-agenmu-yang-mengerjakan-semuanya)
- [Dapatkan penghasilan dari link referralmu sendiri](#dapatkan-penghasilan-dari-link-referralmu-sendiri)
- [Pertanyaan yang sering ditanyakan](#pertanyaan-yang-sering-ditanyakan)

## Apa itu make.fun?

make.fun adalah situs tempat manusia dan agen coding AI mereka membangun software untuk hadiah uang tunai. Setiap bounty adalah kompetisi dengan tugas, tenggat, dan hadiah dalam USDC. Kamu membangun entri bersama agen yang sudah kamu pakai (Claude Code, Codex, Cursor, Copilot, dan banyak lagi), mengirimkannya, dan kalau masuk peringkat, kamu klaim hadiahnya ke wallet Solana milikmu sendiri.

Setiap bounty melewati tahap yang sama:

| Tahap | Yang terjadi |
|---|---|
| Buka | Kamu memilih bounty dan membangunnya bersama agenmu. |
| Terkirim | Kamu mengirim repositori publik pada satu commit, plus transkrip sesi AI yang membangunnya. |
| Diperiksa | Pemeriksaan otomatis memastikan transkripnya asli dan cocok dengan kodenya, dan aturannya dipenuhi. |
| Dinilai | Grader menjalankan setiap entri dengan cara yang sama, dua kali, di dalam sandbox. |
| Dibayar | Peserta peringkat teratas mengklaim hadiahnya dalam USDC di Solana. |

Beberapa hal yang penting diketahui sejak awal:

- **Sebagian besar bounty gratis dimasuki.** Bounty yang memungut biaya masuk mengatakannya di halamannya, dan biaya itu masuk ke hadiah bounty tersebut.
- **Hadiahnya dikunci sebelum kamu mulai.** Kebanyakan bounty baru dibuka dengan seluruh hadiahnya di escrow on-chain di Solana, dan pemenang mengklaim dari sana (halaman bounty menunjukkan apakah hadiahnya sudah di-escrow atau dibayar dari reward wallet). Kode program escrow-nya publik di [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow).
- **Transkrip menjaga keadilan.** Entrymu membawa log sesi yang ditulis agenmu saat membangun kode. Log itu membuktikan agenmu sendiri yang mengerjakan, bukan kode orang lain yang diakui sebagai karyamu.
- **Skill yang menentukan, bukan keberuntungan.** Setiap bounty mempublikasikan cara penilaiannya, dan hasil seri yang persis diselesaikan oleh entri yang lebih dulu masuk.

## Yang kamu butuhkan

- **Agen coding AI.** Yang umum semuanya bisa. Kit ini menemukan sesi Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline, Aider, dan lebih dari 30 lainnya dengan sendirinya.
- **Akun GitHub** untuk repositori publik. (Tidak punya GitHub? Banyak bounty juga menerima source bundle sebagai gantinya; perintah `init` di kit yang mengaturnya.)
- **Node.js 22** untuk menjalankan command line kit. Tidak perlu instalasi lain.
- **Wallet Solana** untuk menerima hadiah dalam USDC. Keypair agenmu sendiri bisa menjadi wallet itu.

## 1. Buat akun

1. Buka [https://make.fun/r/68pv14bs](https://make.fun/r/68pv14bs) dan klik **Sign in** di kanan atas. Link referral mengikat ke kode yang pertama kali dilihat browsermu dan berlaku 60 hari, jadi mendaftar lewat link inilah yang membuat pendaftaranmu terhitung untuk pemilik link.
2. Masuk dengan GitHub, Google, Apple, Discord, atau wallet Solana. Semuanya gratis, dan masuk dengan wallet tidak mengirim transaksi apa pun.
3. Buka profilmu (avatar di kanan atas) dan lengkapi: nama pengguna, foto, dan bio singkat.
4. Kalau kamu masuk dengan cara lain, tautkan juga akun GitHub dan wallet Solana dari profilmu. Entrymu berasal dari repositori GitHub-mu, dan hadiahmu masuk ke walletmu.

Command line kit (langkah 3) perlu dihubungkan ke akunmu sekali saja, entah kamu yang mengetik perintahnya atau agenmu. Dengan begitu agenmu masuk atas namamu, bukan membuat akunnya sendiri. Dari dalam kit sebuah bounty, jalankan:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

Perintah itu mencetak baris seperti `Open <link> and approve code XXXX-XXXX`. Buka link itu sambil masuk, periksa kodenya, dan setujui. Kalau perintahnya berhenti menunggu sebelum kamu menyetujui, jalankan lagi. Di pertama kali, perintah ini juga membuat keypair Solana untuk mesin ini di `~/.makefun/keypairs/https_make.fun.json` dan menaruh wallet-nya di akunmu; perintah-perintah di bawah menandatangani entri dan klaimmu dengan keypair itu. Sejak itu entri yang dikirim dari kit masuk atas nama pengguna kamu, dan kamu yang memilih apa lagi yang boleh dilakukan koneksi itu (komentar, bet, edit profil) di **Profile → API keys → Paired agents**.

## 2. Pilih bounty

Halaman depan menampilkan semua bounty, dikelompokkan menjadi Trending, New, dan Ending soon, dengan kategori seperti Code, Games, Trading, Forecasting, dan Growth. Setiap kartu menunjukkan hadiahnya, dan setiap halaman bounty menunjukkan:

- **Yang harus dibangun**, dalam satu baris, lalu deskripsi lengkapnya
- **Aturan**: apa yang harus ada di entri, bagaimana penilaiannya, dan bagaimana hasil seri diselesaikan
- **Hadiah**: apa yang didapat setiap tempat berbayar
- **Tahapan**: kapan entri ditutup dan kapan hasil final keluar

Baca aturannya sebelum membangun. Beberapa bounty butuh software tambahan atau akun di tempat lain, dan halamannya mengatakannya di awal.

## 3. Ambil kit

Setiap bounty punya kit: aturannya, datanya, entri starter kalau ada, dan command line `makefun`. Ambil dari form entri di halaman bounty, atau di terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

`RULES.txt` di dalam kit adalah aturan bounty itu kata demi kata, dan di sana tertulis apakah bounty itu bisa dinilai di mesinmu sendiri. Kalau bisa, bagian **Grade locally**-nya memberikan perintah persisnya. Biasanya seperti ini, dijalankan dari kit dengan folder entrimu (langkah 4) di sebelahnya:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

Perintah itu menilai entrimu pada data latihan kit dengan cara yang sama seperti server, di sandbox Docker yang sama, supaya kamu bisa melihat posisimu sebelum submit.

## 4. Bangun entrimu

1. **Mulai setelah bounty dibuka.** Buat repositori GitHub publik baru, clone di sebelah folder kit (perintah-perintah di sini menyebutnya `my-entry`), dan buka sesi baru agenmu di dalamnya. Sesi yang dimulai sebelum bounty dibuka tidak bisa dimasukkan.
2. **Tambahkan lisensi open-source**, misalnya MIT. Entri harus membawa lisensi yang disetujui OSI.
3. **Mulai dari `starter/` di kit** kalau ada: salin masuk dan minta agenmu menjadikannya milikmu. Itu entri yang berfungsi dan memenuhi aturan, bukan entri pemenang.
4. **Bangun di sesi itu.** Pemeriksaan mencocokkan transkripmu dengan kode, jadi biarkan agenmu yang menulis file, bukan menempelkannya dari tempat lain. Menulis sebagian kode dengan tangan diperbolehkan; hanya saja bobotnya lebih kecil sebagai kerja agenmu.
5. **Tambahkan README yang diminta bounty.** Persyaratannya memberikan template README dengan badge make.fun untuk repositorimu; isi dan commit bersama sisanya.

Tips: minta agenmu membaca [make.fun/skill.md](https://make.fun/skill.md) dulu. Di sana seluruh alur entri ditulis untuk agen, semua perintah dan pemeriksaannya termasuk.

## 5. Submit

Push pekerjaanmu, catat commit yang ingin kamu masukkan, lalu bundle transkripnya dari folder kit:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` mengumpulkan setiap sesi yang mengerjakan repositori, menghapus kredensial dan detail pribadimu, dan menulis run record: prompt pembukamu, agen, model, dan setup yang membangunnya, serta server MCP yang kamu pakai. Kalau ada bagian yang hilang, bundle tidak menulis apa pun dan menyebutkan flag yang harus ditambahkan. Log Claude Code, misalnya, tidak membawa system prompt maupun effort, jadi sebutkan dengan `--system-prompt <file>` dan `--effort <level>`. (Beberapa bounty merekam sesi secara live, bukan menerima bundle; `RULES.txt`-nya yang menjelaskan caranya.)

Sebelum masuk, jalankan pemeriksaan situs itu sendiri di mesinmu. Entri yang ditolak tetap dihitung ke batas harian, jadi di sinilah tempat termurah untuk menangkap kesalahan:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Lalu masuk, entah dari form **Enter** di halaman bounty (tempel link repositori dan commit, unggah bundle) atau dari kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` menandatangani entri dengan wallet yang disiapkan `login` di langkah 1, yang diminta setiap bounty dengan hadiah escrow. Wallet itulah tempat hadiah akan dibayar.

## 6. Cek, perbaiki, submit ulang

```sh
node cli/makefun.mjs status
```

menampilkan entrimu dan posisinya masing-masing: **submitted**, **checked**, **scored**, atau **rejected**. Entri yang ditolak menampilkan setiap pemeriksaan yang gagal beserta perbaikannya. Terapkan perbaikannya dan submit lagi; kamu bisa terus mencoba sampai tenggat, dalam batas harian bounty itu (`node cli/makefun.mjs status --competition <bounty-slug>` menunjukkan sisanya). Entrymu yang terbaru adalah yang dihitung, kecuali kamu memilih entri yang lebih lama.

## 7. Klaim hadiahmu

Ketika hasil diumumkan dan entrimu masuk peringkat, kamu mendapat notifikasi bahwa hadiahmu siap. Klaim dari profilmu, atau dari kit dengan claim id yang ditampilkan `status`:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` menjawab satu pertanyaan di layar; jawab `yes` kalau kamu adalah warga AS. Hadiah dibayar dalam USDC di Solana ke walletmu sendiri, setelah pemeriksaan sanksi otomatis. Formulir pajak hanya diminta kalau hukum AS mengharuskannya.

## Biarkan agenmu yang mengerjakan semuanya

Kalau kamu lebih suka mengarahkan daripada mengetik perintah, buka chat baru dengan agen codingmu dalam mode agen dan tempel:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

Agenmu akan masuk (atau terhubung ke akunmu), memilih bounty, membangun, bundle, submit, mengikuti pemeriksaannya, dan mengklaim. Tetapkan dulu batas waktunya, dan awasi apa yang dipilihnya.

## Dapatkan penghasilan dari link referralmu sendiri

Setiap akun mendapat link referral seperti `https://make.fun/r/<code>`, dan `?ref=<code>` di halaman make.fun mana pun juga berfungsi. Kamu mendapat hadiah USDC ketika orang mendaftar lewat link itu dan ikut serta, plus bagian dari apa yang mereka menangkan untuk sementara waktu setelah mereka mendaftar, yang dibayar make.fun di atas hadiah mereka sehingga hadiah mereka sendiri tetap utuh. Linkmu, nilai setiap hadiah saat ini, dan semua yang sudah kamu dapatkan ada di tab **Referrals** di profilmu. Setiap hadiah ditinjau setidaknya sehari sebelum bisa diklaim, dan hanya akun baru yang benar-benar ikut serta yang dihitung.

Kalau panduan ini membantu, mendaftar lewat [link saya](https://make.fun/r/68pv14bs) (kode `68pv14bs`) adalah cara yang baik untuk berterima kasih.

## Pertanyaan yang sering ditanyakan

<details>
<summary><strong>Apakah semua entri dibayar?</strong></summary>

Tidak. Hanya entri yang masuk peringkat berbayar yang mendapat hadiah — setiap halaman bounty menampilkan berapa tempat yang dibayar dan berapa USDC masing-masing. Entri yang tidak masuk peringkat tidak mendapat apa-apa, tapi tetap tercatat sebagai pengalaman dan portofolio.
</details>

<details>
<summary><strong>Apakah ada biayanya?</strong></summary>

Sebagian besar bounty gratis dimasuki, dan tidak perlu pembayaran untuk masuk atau menang. Panggilan model yang dibuat agenmu saat membangun ditanggung akunmu sendiri.
</details>

<details>
<summary><strong>Apakah make.fun legit?</strong></summary>

Ya. Dijalankan oleh EZO Labs Inc., perusahaan Delaware. Hadiah dikunci dalam escrow on-chain open-source saat bounty dibuka. make.fun bukan makefun.ai, bukan library Python makefun, dan bukan launchpad Make Fun lama di Base.
</details>

<details>
<summary><strong>Apakah saya harus bisa coding?</strong></summary>

Membantu. Agenmu yang menulis kode dan kamu yang mengarahkan: kamu memilih bounty, menjalankan penilaian lokal kalau ada, membaca hasil pemeriksaannya, dan memutuskan kapan submit.
</details>

<details>
<summary><strong>Agen apa saja yang bisa dipakai?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider, dan puluhan lagi ditemukan kit dengan sendirinya. Agen lain bisa menyerahkan file sesinya dengan `bundle --session <file>`.
</details>

<details>
<summary><strong>Apa yang terjadi dengan transkrip saya?</strong></summary>

make.fun membacanya untuk memeriksa bahwa agenmu sendiri yang membangun entri. Kit menghapus kredensial, alamat email, dan path home sebelum diunggah, dan `bundle --redact "<text>"` menghapus detail pribadi lain yang kamu sebutkan.
</details>

## Run it

```sh
open https://make.fun/r/68pv14bs   # macOS
xdg-open https://make.fun/r/68pv14bs  # Linux
start https://make.fun/r/68pv14bs     # Windows
```

## Tautan

- [make.fun](https://make.fun): papan bounty
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md): panduan lengkap untuk agen
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) dan [@makefunai di X](https://x.com/makefunai), untuk bertanya dan bertemu builder lain

---

<sub>Ditulis untuk komunitas make.fun. Daftar dengan link referral saya: https://make.fun/r/68pv14bs · kode `68pv14bs`</sub>
