SQL SCRIPT (MYSQL)
<br/><br/><p><a href="" style="color:red!important; font-size:1.3em;">PERHATIAN</a></p><p><a href="" style="color:orange!important; font-size:1.2em">BRANCH INI SUDAH KADALUWARSA. TIDAK LAGI LAYAK PAKAI. UNTUK SEMENTARA AKAN DIBIARKAN SAMPAI DIPUTUSKAN UNTUK DIHAPUS.</a></p><br/>
<h3><strong>Daftar Kode Wilayah NKRI</strong> (+KODE POS)</h3>Sumber:<a>https://www.nomor.net</a>

<br>Update per 23 Juli 2020:<br/>
<b>34</b> provinsi, <b>514</b> kota+kabupaten, <b>7.201</b> kecamatan/distrik, <b>83.436</b> desa/kelurahan.

<br><b>Contoh Verifikasi</b>

Jumlah Propinsi

<pre><code>SELECT COUNT(*) AS `Total Propinsi`<br>
FROM (SELECT kodewilayah<br>
      FROM kodewilayah<br>
      GROUP BY LEFT(kodewilayah,2)) AS kodewilayah
</code></pre>


Jumlah Kabupaten
<pre><code>SELECT COUNT(*) AS `Total Kabupaten`<br>
FROM (SELECT kodewilayah FROM kodewilayah<br>
      WHERE kodekabkota='Kabupaten'<br>
      GROUP BY LEFT(kodewilayah,5)) AS kodewilayah
</code></pre>


Jumlah Kota
<pre><code>SELECT COUNT(*) AS `Total Kota`<br>
FROM (SELECT kodewilayah FROM kodewilayah<br>
      WHERE kodekabkota='Kota'<br>
      GROUP BY LEFT(kodewilayah,5)) AS kodewilayah
</code></pre>      


Jumlah Kota+Kabupaten
<pre><code>SELECT COUNT(*) AS `Total Kota+Kabupaten`<br>
FROM (SELECT kodewilayah FROM kodewilayah<br>
      GROUP BY LEFT(kodewilayah,5)) AS kodewilayah
</code></pre>


Jumlah Kecamatan
<pre><code>SELECT COUNT(*) AS `Total Kecamatan`<br>
FROM (SELECT kodewilayah FROM kodewilayah<br>
      GROUP BY LEFT(kodewilayah,8)) AS kodewilayah
</code></pre>      


Jumlah Desa/Kelurahan
<pre><code>SELECT COUNT(*) AS `Total Desa/Kelurahan`<br>
FROM kodewilayah</code></pre>

<b>Contoh Rekap</b>:
<pre><code>SELECT (SELECT COUNT(*)
        FROM (SELECT NULL 
              FROM kodewilayah
              GROUP BY LEFT(kodewilayah,2)) Propinsi) AS 'Total Propinsi',
       (SELECT COUNT(*)
        FROM (SELECT NULL 
              FROM kodewilayah 
              GROUP BY LEFT(kodewilayah,5)) KotaKabupaten)  AS `Total Kota+Kabupaten`,
       (SELECT COUNT(*)
        FROM (SELECT NULL 
              FROM kodewilayah 
              GROUP BY LEFT(kodewilayah,8)) Kecamatan)  AS `Total Kecamatan`,
       (SELECT COUNT(*) 
        FROM kodewilayah)  AS `Total Desa/Kelurahan`
</code></pre>
