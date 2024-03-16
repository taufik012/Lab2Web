# Tugas PHP

'Tugas' : Buatlah program PHP sederhana dengan menggunakan form input yang menampilkan nama, tanggal
lahir dan pekerjaan. Kemudian tampilkan outputnya dengan menghitung umur berdasarkan inputan
tanggal lahir. Dan pilihan pekerjaan dengan gaji yang berbeda-beda sesuai pilihan pekerjaan.

```py
<!DOCTYPE html>
<html>

<head>
    <title>Form Input</title>
</head>

<body>

    <h2>Form Input Data</h2>
    <form method="post" action="<?php echo htmlspecialchars($_SERVER["PHP_SELF"]); ?>">
        Nama: <input type="text" name="nama"><br><br>
        Tanggal Lahir: <input type="date" name="tgl_lahir"><br><br>
        Pekerjaan:
        <select name="pekerjaan">
            <option value="Programmer">Programmer</option>
            <option value="Desainer">Desainer</option>
            <option value="Manajer">Manajer</option>
        </select><br><br>
        <input type="submit" name="submit" value="Submit">
    </form>

    <?php
    // Fungsi untuk menghitung umur berdasarkan tanggal lahir
    function hitungUmur($tgl_lahir)
    {
        $tgl_lahir = new DateTime($tgl_lahir);
        $today = new DateTime('today');
        $umur = $tgl_lahir->diff($today)->y;
        return $umur;
    }

    if ($_SERVER["REQUEST_METHOD"] == "POST") {
        $nama = $_POST['nama'];
        $tgl_lahir = $_POST['tgl_lahir'];
        $pekerjaan = $_POST['pekerjaan'];

        $umur = hitungUmur($tgl_lahir);

        // Array dengan pilihan pekerjaan dan gaji sesuai pekerjaan
        $gaji_pekerjaan = array(
            "Programmer" => 10000000,
            "Desainer" => 8000000,
            "Manajer" => 12000000
        );

        // Menampilkan output
        echo "<h2>Output:</h2>";
        echo "Nama : $nama <br>";
        echo "Umur : $umur tahun <br>";
        echo "Pekerjaan : $pekerjaan <br>";
        echo "Gaji : Rp " . number_format($gaji_pekerjaan[$pekerjaan], 0, ',', '.') . " per bulan";
    }
    ?>

</body>

</html>
```


![image](screenshot/1.PNG)
