# Jarkom-Modul-1-ITB08-2022

## Anggota:
| Nama                      | NRP        |
|---------------------------|------------|
| Salsabila Briliana A. S.  | 5027201003 |
| Muhammad Rifqi Fernanda   | 5027201050 |
| Gilang Bayu Gumantara     | 5027201062 | 

## Soal 1 
---
Sebutkan web server yang digunakan pada "monta.if.its.ac.id!
### Solution 
---
Dikarenakan web kita harus memakai display filter yaitu http, lalu kita menemeukan webserver yang digunakan pada "monta.if.its.ac.id yaitu nginx/1.10.3
![nginx](https://user-images.githubusercontent.com/90242686/192086796-d8b88bd0-0914-48c8-9e19-6009efdd8919.jpeg)


## Soal 2
---
Ishaq sedang bingung mencari topik ta untuk semester ini , lalu ia datang ke website monta dan menemukan detail topik pada website “monta.if.its.ac.id” , judul TA apa yang dibuka oleh ishaq ?
### Solution
---
Setelah itu kita menuju ke Statistic lalu ke HTTP dan request sentence untuk mengetahui link website monta dan disitulah judul TA yang ia temukan 
![ws](https://user-images.githubusercontent.com/90242686/192087253-7dc51422-8160-49c9-a420-9af9d46c8942.jpeg)
![monta](https://user-images.githubusercontent.com/90242686/192087325-40199dae-5477-41a1-81f1-201329336129.jpeg)

## Soal 3 
---
Filter sehingga wireshark hanya menampilkan paket yang menuju port 80! 
### Solution
---
Untuk menampilkan paket yang menuju port 80, kita perlu menggunakan tcp.dstport == 80 dalam display filternya
![tdcdst](https://user-images.githubusercontent.com/90242686/192088153-2ae89dec-3bd9-4154-a7a4-b65f5b68245c.jpeg)







## Study Case Soal 8-10
---
Di sebuah planet bernama Viltrumite, terdapat Kementerian Komunikasi dan Informatika yang baru saja menetapkan kebijakan baru. Dalam kebijakan baru tersebut, pemerintah dapat mengakses data pribadi masyarakat secara bebas jika memang dibutuhkan, baik dengan maupun tanpa persetujuan pihak yang bersangkutan. Sebagai mahasiswa yang sedang melaksanakan program magang di kementerian tersebut, kalian mendapat tugas berupa penyadapan percakapan mahasiswa yang diduga melakukan tindak kecurangan dalam kegiatan Praktikum Komunikasi Data dan Jaringan Komputer 2022. Selain itu, terdapat sebuah password rahasia (flag) yang diduga merupakan milik sebuah organisasi bawah tanah yang selama ini tidak sejalan dengan pemerintahan Planet Viltrumite. Tunggu apa lagi, segera kerjakan tugas magang tersebut agar kalian bisa mendapatkan pujian serta kenaikan jabatan di kementerian tersebut!

## Soal 8
---
Telusuri aliran paket dalam file .pcap yang diberikan, cari informasi berguna berupa percakapan antara dua mahasiswa terkait tindakan kecurangan pada kegiatan praktikum. Percakapan tersebut dilaporkan menggunakan protokol jaringan dengan tingkat keandalan yang tinggi dalam pertukaran datanya sehingga kalian perlu menerapkan filter dengan protokol yang tersebut.

### Solution
---
Melakukan follow tcp stream untuk menemukan percakapan 2 mahasiswa. Setelah ditelusuri, terdapat percakapan pada tcp stream 12, 41, dan 90.

1. tcp.stream eq 12
![tcp12](image/soal8/tcp12.png)

2. tcp.stream eq 41
![tcp41](image/soal8/tcp41.png)

3. tcp.stream eq 90
![tcp90](image/soal8/tcp90.png)

## Soal 9
---
Terdapat laporan adanya pertukaran file yang dilakukan oleh kedua mahasiswa dalam percakapan yang diperoleh, carilah file yang dimaksud! Untuk memudahkan laporan kepada atasan, beri nama file yang ditemukan dengan format [nama_kelompok].des3 dan simpan output file dengan nama “flag.txt”.

### Solution
Pada percakapan tcp stream 12 disebutkan bahwa akan mengirim file melalui port 9002 sehingga dilakukan filter tcp.port == 9002

![port9002](image/soal9/port9002.png)

Kemudian melakukan follow tcp stream dan menemukan filenya. File tersebut disimpan dalam bentuk raw dan di rename menjadi ITB08.des3.

![file](image/soal9/salt.png)

![raw](image/soal9/rawFile.png)

Setelah itu file akan di decrypt menggunakan openssl dan hasilnya disimpan pada flag.txt (openssl des3 -d -in ITB04.des3 -out flag.txt)

![openssl](image/soal9/openssl.png)

## Soal 10
Temukan password rahasia (flag) dari organisasi bawah tanah yang disebutkan di atas!

### Solution
Percakapan pada tcp stream 12 terdapat clue untuk password pada file yang dikirim, yaitu nama karakter anime kembar 5. Saat menelusuri di internet diketahui bahwa passwordnya adalah nama keluarga dari karakter kembar 5 anime tersebut, yaitu "nakano".

![anime](image/soal10/anime.png)

## Kendala
Pada awalnya belum mengetahui password dari file yang ditemukan, kemudian setelah waktu pengerjaan soal shift selesai kami baru menemukan passwordnya dan mendemokannya pada asisten penguji.
