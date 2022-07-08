# Boston-Crime-EDA
Crimes in Boston Explanatory Data Analysis with Data Visualization
By: Reyhan Alif Pradityo

<img src="https://www.bu.edu/admissions/files/2018/07/17-2005-AERIALS-101-cropped-e1535295662889-1920x600.jpg" alt="Boston City Scenery"></p>

Didirikan pada tahun 1630, Boston adalah kota terbesar sekaligus ibu kota di Massachusetts, AS. Setelah kemerdekaan AS, kota Boston terus menjadi kota dengan pelabuhan penting, pusat manufaktur, serta pusat pendidikan dan budaya. Sejarahnya yang kaya menarik banyak turis, dengan wisata Faneuil Hall menarik lebih dari 20 juta pengunjung per tahun. Boston Police Department (BPD) memiliki data mengenai laporan insiden kejahatan yang dimulai dari 14 Juni 2015 sampai 3 September 2018. Data tersebut dapat dimanfaatkan oleh BPD untuk mencegah dan mengurangi tingkat kriminalitas di kota Boston. Dalam project ini, kita memposisikan diri sebagai data analyst di BPD yang memiliki peran untuk menganalisis data dan memberikan rekomendasi kepada Director of Strategic Change untuk membentuk dan memandu pengambilan keputusan strategis di BPD untuk mengurangi tingkat tindakan kriminal yang terjadi.

# Problem Statement 
Sebagai komitmen untuk terus menjaga keamanan kota Boston, BPD ingin meningkatkan performa pelayanan dengan menargetkan penurunan laporan "Part 1 Crime" di tahun selanjutnya. Untuk mencapai target tersebut, kita perlu melihat kembali data laporan tindakan kriminal pada tahun-tahun sebelumnya sehingga kita dapat memberikan rekomendasi kebijakan yang dapat diambil untuk menurunkan tingkat "Part 1 Crime" 

Pertanyaan untuk mencari Insight:
1. Bagaimana tren jumlah laporan insiden tiap bulan dari tahun 2015-2018? </p>
2. Apa tipe tindakan kriminal yang paling sering terjadi</p>
3. tindakan kriminal apa yang paling banyak mengalami peningkatan dari tahun 2016-2017</p>
4. Dimana tindakan kriminal paling sering terjadi </p>
5. Kapan waktu tindakan kriminal paling sering terjadi</p>
6. Kapan waktu paling rawan terjadinya penembakan dan insiden apa yang paling banyak terdapat penembakan</p>

# Data Understanding
Dataset ini berisi informasi mengenai laporan insiden yang terjadi di kota Boston. Informasi yang terekam merupakan detail awal mengenai suatu kejadian yang dimana ditanggapi oleh polisi BPD. Terdapat 17 kolom pada dataset crime, yaitu:
- INCIDENT_NUMBER : Penomoran unik untuk tiap insiden yang terjadi
- OFFENSE_CODE : Kode insiden yang terjadi, keterengan kode insiden terdapat pada data offense_codes
- OFFENSE_CODE_GROUP : Kategori insiden yang terjadi
- OFFENSE_DESCRIPTION : Deskripsi awal yang menjelaskan mengenai kejadian 
- DISTRICT : Nomor distrik tempat terjadinya insiden  
- REPORTING_AREA : Kode area dimana insiden dilaporkan
- SHOOTING : Apakah terjadi insiden penembakan (Yes/No)
- OCCURRED_ON_DATE : Tanggal dan waktu terjadinya insiden
- YEAR : Tahun terjadinya insiden
- MONTH : Bulan terjadinya insiden
- DAY_OF_WEEK : Hari terjadinya insiden
- HOUR : Jam terjadinya insiden
- UCR_PART : Index Uniform Crime Report
- STREET : Nama jalan tempat terjadinya insiden
- Lat : Garis Lintang titik terjadinya insiden 
- Long : Garis Bujur titik terjadinya insiden 
- Location : Titik lokasi berdasarkan informasi garis lintang dan garis bujur

# Data Wrangling
- Dataset crime memiliki 319073 Baris dan 17 Kolom
- Kolom `DISTRICT`, `SHOOTING`, `UCR PART`, `STREET`, `Lat`, dan `Long` memiliki nilai kosong yang diwakili dengan nilai NaN
- Kolom `INCIDENT_NUMBER` memuat informasi mengenai nomor unik dari setiap laporan insiden. Karena setiap datanya bersifat unik karena mewakili satu laporan insiden, tidak boleh ada data dengan nomor insiden yang sama. Perlu dicek lebih lanjut mengenai data duplikat tersebut.
- Kolom `OFFENSE_CODE`, `OFFENSE_CODE_GROUP`, `OFFENSE_DESCRIPTION` memuat informasi dengan tujuan yang sama, yaitu menjelaskan tentang pelanggaran yang terjadi dari setiap insiden. Pada analisis ini, kolom yang akan digunakan sebagai acuan jenis pelanggaran yang terjadi adalah `OFFENSE_CODE_GROUP` karena memiliki nilai unique yang paling kecil. Kolom lainnya akan di drop.
- Kolom `REPORTING_AREA` memuat informasi tempat asal laporan berdasarkan kode area telpon pembuat laporan. Untuk melihat lokasi suatu insiden sebetulnya sudah diwakili oleh kolom `DISTRICT`, `STREET`, dan juga `Location` yang secara spesifik memberikan informasi tempat terjadinya insiden sehingga kolom `REPORTING_AREA` dapat di drop.
- Pada kolom `SHOOTING` dapat dilihat adanya laporan penembakan diwakili dengan nilai 'Y' dan tidak adanya laporan penambakan diwakili dengan nilai 'nan'. Nilai 'nan' dapat kita isi dengan nilai 'N' agar sebanding dengan lawan nilai kategorikalnya.
- Kolom `Location` memiliki beberapa nilai kosong. Jika kita cek data dari kolom `Location` yang memiliki nilai kosong, terdapat data pada kolom `STREET` dan `DISTRICT` yang memiliki nilai kosong juga, sehingga kita dapat drop data yang memiliki nilai kosong pada ketiga kolom tersebut karena kita tidak tau lokasi insiden tersebut. Data pada kolom `STREET` dan `DISTRICT` yang kosong dapat dilengkapi dengan melihat lokasi di kolom `Location` 
- Kolom `Lat` dan `Long` dapat kita drop karena kedua informasi tersebut sudah digabung dalam kolom `Location` dan kedua kolom tersebut tidak bisa digunakan untuk analisis jika secara individu atau tidak digabung 
- Kolom `UCR_PART` memiliki 90 nilai kosong dan dapat kita lengkapi dengan melihat jenis pelanggaran pada `OFFENSE_CODE_GROUP` 

# EDA
![alt text](https://github.com/reyhanalif/Boston-Crime-EDA/blob/main/Presentation/8.jpg?raw=true)
![alt text](https://github.com/reyhanalif/Boston-Crime-EDA/blob/main/Presentation/9.jpg?raw=true)
![alt text](https://github.com/reyhanalif/Boston-Crime-EDA/blob/main/Presentation/10.jpg?raw=true)
![alt text](https://github.com/reyhanalif/Boston-Crime-EDA/blob/main/Presentation/11.jpg?raw=true)
![alt text](https://github.com/reyhanalif/Boston-Crime-EDA/blob/main/Presentation/12.jpg?raw=true)
![alt text](https://github.com/reyhanalif/Boston-Crime-EDA/blob/main/Presentation/13.jpg?raw=true)
![alt text](https://github.com/reyhanalif/Boston-Crime-EDA/blob/main/Presentation/14.jpg?raw=true)
![alt text](https://github.com/reyhanalif/Boston-Crime-EDA/blob/main/Presentation/15.jpg?raw=true)
![alt text](https://github.com/reyhanalif/Boston-Crime-EDA/blob/main/Presentation/16.jpg?raw=true)
![alt text](https://github.com/reyhanalif/Boston-Crime-EDA/blob/main/Presentation/17.jpg?raw=true)

# Tableu Dashboard
Dashboard tableu dari visualisasi data pada EDA ini dapat diakses pada link berikut
https://public.tableau.com/app/profile/reyhan.alif/viz/BostonCrimeDashboard_16571323867760/Dashboard1?publish=yes

# Kesimpulan dan Rekomendasi 
Kesimpulan yang dihasilkan dari EDA data laporan insiden di kota boston dari tahun (2015-2018) adalah sebagai berikut:
1. Trendline jumlah laporan insiden memiliki suatu pola musiman, intervensi untuk mengurangi suatu pelanggaran ringan dapat disesuaikan dengan melihat pola musiman suatu pelanggaran
2. Part Three Crime adalah tipe insiden yang paling banyak terjadi. Laporan insiden yang paling banyak terjadi adalah kecelakaan lalu lintas, namun jika hanya melihat Part One Crime Saja, laporan insiden yang paling banyak terjadi adalah Pencurian.
3. Aggravated Assault adalah laporan insiden yang paling banyak mengalami peningkatan dari tahun 2016-2017
4. Distrik yang paling sering terjadi laporan insiden di kota boston adalah distrik B2. Jika kita hanya melihat Part One Crime, maka distrik yang paling berbahaya adalah distrik D4. 
5. Jalan yang paling rawan di Kota Boston adalah Washington St, Boylston St, dan Blue Hill Ave.
6. Laporan insiden paling banyak terjadi saat Shift 3 (15.00-23.00). Hari paling rawan terjadinya insiden adalah hari Jumat, khususnya Jumat Malam. Jika dilihat berdasarkan pola musiman, laporan insiden akan meningkat pada musim panas, atau mulai dari awal Juni sampai akhir Agustus
7. Kasus penembakan paling banya terjadi pada tengah malam (23.00-01.00) dengan puncaknya adalah jam 00.00. Laporan insiden yang paling banyak terdapat kasus penembakan adalah Aggravated Assault.

Dari kesimpulan tersebut, maka direkomendasikan untuk BPD mengambil langkah berikut untuk menurunkan tingkat Part One Crime
1. Berdasarkan prinsip pareto, insiden kejahatan yang perlu difokuskan untuk mengurangi tingkat Part One Crime adalah Larceny, Aggravated Assault, dan Residential Burglary
2. Strategi yang perlu diterapkan untuk mengurangi kejadian Aggravated Asasult adalah melalui Community-based prevention, menyusun strategic enforcement priorities seperti penentuan lokasi, investigasi intensif di lokasi untuk orang yang mencurigakan.
3. Melakukan identifikasi lebih lanjut mengenai faktor pendorong Aggravated Assault di suatu lokasi (kekerasan bersenjata, kekerasan domestik, kelompok kriminal, transaksi obat terlarang, atau faktor pendorong lain) sebagai bahan penyusunan strategic enforcement priorities
4. Community-Based Policy pada tahun 2017 tebukti efektif dalam mengurangi tindak kejahatan yang berkaitan dengan Larceny, sehingga untuk selanjutnya direkomendasikan untuk melakukan pendekatan ke komunitas secara intensif melalui acara seperti Neighborhood Watches dan National Night Out
5. Penambahan personil kedepannya direkomendasikan untuk ditempatkan di distrik B2 dan D4 untuk memperkuat respon terhadap jumlah laporan insiden yang tinggi.
6. Jalan yang perlu mendapat pengawasan lebih adalah Washington St, Boylston St, dan Blue Hill Ave. Karena ketiga jalan tersebut merupakan jalan besar dan membentang jauh, pengawasan dapat difokuskan di area B2 Washington St, D4 Washington St, B2 Boylston St, dan B2 Bluehill Ave
7. Personil direkomendasikan untuk dialokasikan lebih banyak pada shift 3 (15.00 - 23.00)
8. Jumat Malam perlu menjadi perhatian lebih dengan menambah personil untuk memperketat pengawasan di sekitar area ramai (Bar Malam)
9. Pada musim panas, atau awal bulan Juni sampai akhir agustus, BPD harus mengantisipasi kenaikan jumlah laporan insiden dengan memplotkan kegiatan komunitas yang telah direkomendasikan lebih banyak pada musim ini. 
10. Untuk mengurangi kasus Aggravated Assault dengan penembakan, polisi perlu melakukan razia rutin terhadap legalitas kepemilikan senjata api tiap orang dengan memfokuskan di area rawan yang telah direkomendasikan. Jika senjata api ilegal, maka polisi harus menyita senjata tersebut.   
