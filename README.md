# ProjectUAS_PM1


Nama    : Zulaeha

NIM     : 312210575

Kelas   : TI.22.A5

Matkul  : Pemrograman Mobile 1

Dosen   : Donny Maulana, S.Kom., M.M.S.I.


# **Daftar Isi**
- **[Tugas 1](#tugas-1)**

- **[Tugas 2](#tugas-2)**

- **[Tugas 3](#tugas-3)**

- **[Penjelasan & Hasil Program Tugas 1](#penjelasan--hasil-program-tugas-1)**

- **[Penjelasan & Hasil Program Tugas 2](#penjelasan--hasil-program-tugas-2)**

- **[Penjelasan & Hasil Program Tugas 3](#penjelasan--hasil-program-tugas-3)**

- **[Demo Tugas 1](#demo-program-tugas-1)**

- **[Demo Tugas 2](#demo-program-tugas-2)**

- **[Demo Tugas 3](#demo-program-tugas-3)**


## Tugas 1 
```
Buatkanlah :
1. Launcher Splash logo masing-masing Individu 
2. Buatkanlah untuk menampilkan semua project sebelum UTS dengan metode Ekplisit Intent dan
     Implisit Intent:
    a. Project Hallo
    b. Project Count
    c. Project Sianida
    d. Project TwoActivity
    e. Project Set Alarm
 
Untuk tampilan Layout Bebas, terima kasih.
```

## Tugas 2
![tugas pert10](https://github.com/zulaeha168/ProjectUAS_PM1/assets/130324650/b96922b9-ceb3-4cf1-b19d-bae5ca09faaa)

## Tugas 3
![tugas pert12](https://github.com/zulaeha168/ProjectUAS_PM1/assets/130324650/1518b1b2-78fd-487a-9809-6921a5e80afc)

## Penjelasan & Hasil Program Tugas 1
1. Launcher Splash Logo
Pertama, yaitu membuat Launcher Splash Logo atau menampilkan logo / icon saat kita pertama kali membuka aplikasi.
Caranya adalah :

- Persiapkan gambar terlebih dahulu
- Selanjutnya kita klik `app`, lalu klik `res` dan setelahnya kita pilih dan klik `mipmap`
- Setelah itu klik kanan pada bagian `mipmap` , lalu pilih `new`
- Lalu pilih dan klik `Image Asset`
- Lalu ketika sudah terbuka, kita klik bagian `Icon Type` lalu pilih yang `Launcher Icons (Adaptive and Legacy)`
- Lalu pada bagian `Path` kita klik logo file lalu kita pilih dan klik file gambar yang telah disiapkan sebelumnya dan klik `OK`
- Lalu untuk ukuran logo / ikon bisa kita atur pada bagian `Resize`, Jika sudah kita klik `Next`
- Setelah itu kita klik `Finish`, Maka logo / ikon aplikasi kita akan berubah sesuai gambar yang kita inginkan

Untuk menambahkan file gambar seperti untuk SplashScreen, Background di setiap project kita bisa klik bagian `Resource Manager` lalu kita klik tanda `+`. Setelah itu kita pilih dan klik `Import Drawables`, setelah itu kita pilih dan klik file gambar yang sudah kita siapkan lalu klik `OK`. Maka gambar akan tersedia di `res` pada `drawable`.

- Lalu buka `backgroundlauncher.xml` dan masukkan code ini :
```
<?xml version="1.0" encoding="utf-8"?>
<layer-list xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:drawable="@color/purple"/>
    <item>
        <bitmap
            android:src="@drawable/logo"
            android:gravity="center" />
    </item>
</layer-list>
```

> Untuk Warna bisa kita sesuaikan dengan Logo yang telah kita tambahkan tadi
- Lalu, buka `themes.xml` yang letaknya ada di *res/values/themes*, dan tambahkan code ini didalam resourcesnya :
```
<resources xmlns:tools="http://schemas.android.com/tools">
    <!-- Base application theme. -->
    <style name="SplashScreen" parent="Theme.MaterialComponents.DayNight.NoActionBar">
        <item name="android:windowBackground">@drawable/bg2</item>
        <item name="android:statusBarColor">?attr/colorOnPrimary</item>
    </style>
</resources>
```

- Selanjutnya kita buat java class nya agar SplashScreen bisa berjalan, lalu pada `SplashScreen.java` kita masukkan code dibawah ini :
```
package com.projectzulaeha;
import android.content.Intent;
import android.os.Bundle;
import android.os.Handler;
import androidx.appcompat.app.AppCompatActivity;
public class SplashScreen extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        new Handler().postDelayed(new Runnable() {
            @Override
            public void run() {
                startActivity(new Intent(SplashScreen.this, MainActivity.class));
                finish();
            }
        }, 2500);
    }
}
```

> Code di atas digukankan untuk menampilkan SplashScreen, ketika SplashScreen selesai dalam 2.5 detik maka akan langsung berpindah pada tampilan `MainActivity.java`.
- Buka `AndroidManifest.xml`, dan tambahkan code berikut didalam *application* :
```
<activity
            android:name=".SplashScreen"
            android:exported="true"
            android:theme="@style/SplashScreen">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
</activity>
```
Selesai sudah kita membuat perintah Launcher Splash Logo, Selanjutnya kita akan ke tahap berikutnya yaitu membuat menu untuk menampilkan semua project yang sudah dibuat pada pertemuan sebelumnya.


## 2. Menu Utama 
Yang kedua, disini kita akan membuat menu utamanya yang akan berjalan setelah SplashScreen Logo.
Caranya adalah:

Jika awal pembuatan project kita memilih template Empty Views Activity, maka pada layout otomatis terbuat file `activity_main.xml` dan pada java akan ada `MainActivity.java`.
Maka langsung saja kita buka `activity_main.xml`, dan buat code seperti berikut ini:
```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">
    <ImageView
        android:id="@+id/background"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:background="@drawable/bgungu"
        android:adjustViewBounds="true"
        android:scaleType="centerCrop"/>
    <TextView
        android:id="@+id/txtJudul"
        android:layout_width="match_parent"
        android:layout_height="68dp"
        android:layout_alignParentTop="true"
        android:layout_alignParentBottom="true"
        android:layout_marginTop="46dp"
        android:layout_marginBottom="569dp"
        android:gravity="center"
        android:scaleType="centerCrop"
        android:text="Please select and click on the project below"
        android:textColor="@color/black"
        android:textSize="25dp"
        android:textStyle="bold" />
    <Button
        android:id="@+id/btnHelloWorld"
        android:layout_width="150dp"
        android:layout_height="60dp"
        android:layout_alignParentStart="true"
        android:layout_alignParentTop="true"
        android:layout_alignParentEnd="true"
        android:layout_marginStart="100dp"
        android:layout_marginTop="200dp"
        android:layout_marginEnd="100dp"
        android:onClick="btnHelloWorld"
        android:background="@color/cream"
        android:text="Hello World"
        tools:ignore="UsingOnClickInXml"
        android:scaleType="centerCrop"/>
    <Button
        android:id="@+id/btnProjectCount"
        android:layout_width="150dp"
        android:layout_height="60dp"
        android:layout_below="@+id/btnHelloWorld"
        android:layout_alignParentStart="true"
        android:layout_alignParentEnd="true"
        android:layout_marginStart="100dp"
        android:layout_marginTop="20dp"
        android:layout_marginEnd="100dp"
        android:onClick="btnCount"
        android:background="@color/soft"
        android:text="Count"
        tools:ignore="UsingOnClickInXml"
        android:scaleType="centerCrop"/>
    <Button
        android:id="@+id/btnProjectSianida"
        android:layout_width="150dp"
        android:layout_height="60dp"
        android:layout_below="@+id/btnProjectCount"
        android:layout_alignParentStart="true"
        android:layout_alignParentEnd="true"
        android:layout_marginStart="100dp"
        android:layout_marginTop="20dp"
        android:layout_marginEnd="100dp"
        android:onClick="btnSianida"
        android:background="@color/abu"
        android:scaleType="centerCrop"
        android:text="Scroll Movie"
        tools:ignore="UsingOnClickInXml" />
    <Button
        android:id="@+id/btnTwoActivity"
        android:layout_width="150dp"
        android:layout_height="60dp"
        android:layout_below="@+id/btnProjectSianida"
        android:layout_alignParentEnd="true"
        android:layout_alignParentStart="true"
        android:layout_marginTop="20dp"
        android:layout_marginEnd="100dp"
        android:layout_marginStart="100dp"
        android:onClick="btnTwoActivity"
        android:background="@color/hijaumuda"
        android:text="Two Activity"
        tools:ignore="UsingOnClickInXml"
        android:scaleType="centerCrop"/>
    <Button
        android:id="@+id/btnSetAlarm"
        android:layout_width="150dp"
        android:layout_height="60dp"
        android:layout_below="@+id/btnTwoActivity"
        android:layout_alignParentStart="true"
        android:layout_alignParentEnd="true"
        android:layout_marginStart="100dp"
        android:layout_marginTop="20dp"
        android:layout_marginEnd="100dp"
        android:onClick="btnSetAlarm"
        android:background="@color/tosca"
        android:text="Set Alarm"
        tools:ignore="UsingOnClickInXml"
        android:scaleType="centerCrop"/>
</RelativeLayout>
```
- Setelah itu kita buka `MainActivity.java` untuk menambahkan code intent untuk masing-masing tombol :
```
package com.projectzulaeha;
import androidx.appcompat.app.AppCompatActivity;
import android.content.Intent;
import android.os.Bundle;
import android.view.View;
public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        findViewById(R.id.btnSetAlarm).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Panggil metode untuk mengatur alarm
                setAlarm();
            }
        });
    }
    private void setAlarm() {
        Intent alarm = new Intent(android.provider.AlarmClock.ACTION_SET_ALARM);
        startActivity(alarm);
    }
    public void btnHelloWorld(View view) {
        Intent helloworld = new Intent(MainActivity.this, HelloActivity.class);
        startActivity(helloworld);
    }
    public void btnCount(View view) {
        Intent count = new Intent(MainActivity.this, CountActivity.class);
        startActivity(count);
    }
    public void btnSianida(View view) {
        Intent sianida = new Intent(MainActivity.this, SianidaActivity.class);
        startActivity(sianida);
    }
    public void btnTwoActivity(View view) {
        Intent twoact = new Intent(MainActivity.this, TwoActivity.class);
        startActivity(twoact);
    }
}
```
> Button *HelloWorld, Count, Sianida dan TwoActivity* menggunakan Explicit Intent, dan project *SetAlarm* menggunakan Implicit Intent.
> Menu halaman utama dan tombol-tombol aplikasi sudah berhasil dibuat. Maka selanjutnya yang kita lakukan adalah menambahkan coding pada `AndroidManifest.xml` agar aplikasi dapat berjalan.
## 3. AndroidManifest.xml
Didalam `AndroidManifest.xml` kita tambahkan semua java class dari semua project kita sebelumnya. Berikut nama java class dari berbagai project yang telah saya buat:

a. Project Hello World = HelloActivity.java
b. Project Count = CountActivity.java
c. Project Scroll Movie = SianidaActivity.java
d. Project TwoActivity = TwoActivity.java dan Two2Activity.java
e. Project Set Alarm = MainActivity.java (karena merupakan Implicit Intent, jadi code untuk set alarm langsung dibuat disini)

```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">
    <uses-permission
        android:name="com.android.alarm.permission.SET_ALARM" />
    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.Design.Light"
        tools:targetApi="31">
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.SET_ALARM" />
                <category android:name="android.intent.category.DEFAULT" />
            </intent-filter>
        </activity>
        <activity
            android:name=".HelloActivity"
            android:exported="true" />
        <activity
            android:name=".TwoActivity"
            android:exported="true" />
        <activity
            android:name=".Two2Activity"
            android:exported="true" />
        <activity
            android:name=".CountActivity"
            android:exported="true" />
        <activity
            android:name=".SianidaActivity"
            android:exported="true" />
        <activity
            android:name=".SplashScreen"
            android:exported="true"
            android:theme="@style/SplashScreen">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>
</manifest>
```

## 4. Code All Projects (Strings, Colors dan Dimens)
> `Strings.xml`
```
<resources>
    <string name="app_name">ProjectZulaeha</string>
    <string name="Hello_World">Hello World</string>
    <string name="button_main">Send</string>
    <string name="editText_main">Enter Your Message Here</string>
    <string name="text_header">Message Received</string>
    <string name="buttton_second">Reply</string>
    <string name="editText_second">Enter Your Reply Here</string>
    <string name="text_header_reply">Reply Received</string>
    <string name="button_label_toast">Toast</string>
    <string name="button_label_count">Count</string>
    <string name="count_initial_value">1</string>
    <string name="toast_massage">Hello Toast!</string>
    <string name="button_label_restart">Restart</string>
    <string name="enter_fibonacci_limit">Masukkan Angka Limit</string>
    <string name="article_title"> Kasus Sianida</string>
    <string name="article_subtitle">ICE COLD!</string>
    <string name="article_text"> Film dokumenter Ice Cold: Murder, Coffee and Jessica Wongso memaparkan pertanyaan tak terjawab tentang persidangan yang dilalui Jessica Wongso. Dengan menyajikan perspektif baru, film ini hadir bertahun-tahun setelah kematian sahabat Jessica, Wayan Mirna Salihin.
Film ini menggambarkan bagaimana Jessica yang mengajak teman-temannya, termasuk Mirna, untuk bertemu setelah sekian lama tak berjumpa. Pertemuan di salah satu kafe di mal ibu kota tersebut pun berlangsung lancar, sebelum akhirnya Mirna pingsan sesaat setelah meminum kopi yang sebelumnya dipesan Jessica.Dokumenter ini turut menyajikan rekaman CCTV pada waktu kejadian, berbagai footage berita saat persidangan berlangsung, hingga wawancara eksklusif dengan beberapa sumber, termasuk Jessica Wongso.
Persidangan atas dugaan pembunuhan Mirna Salihin digelar lima bulan setelah kematiannya. Sidang tersebut melalui 32 kali persidangan dengan menghadirkan puluhan saksi di pengadilan. Hasilnya, Jessica Wongso divonis bersalah atas kematian Mirna dan dijatuhi hukuman 20 tahun penjara.
Kasus yang berjalan cukup lama tersebut menyita banyak perhatian dari masyarakat Indonesia. Musababnya, banyak misteri tak terjawab selama rangkaian persidangan yang panjang tersebut. Salah satunya adalah mengenai akses untuk mendapatkan bubuk sianida yang tidak bisa didapatkan oleh orang sembarangan. Selain itu, motif Jessica di balik pembunuhan tersebut pun belum menemukan jawabannya.
        
Film dokumenter buatan Netflix ini menyoroti rangkaian persidangan yang saat itu menjadi sidang pertama yang disiarkan secara langsung di berbagai stasiun televisi Indonesia. Selain itu, kasus ini juga diliput secara intens oleh media massa, baik nasional maupun internasional.Tak hanya itu, pihak rumah produksi Beach House Pictures juga berhasil mendapatkan akses untuk mewawancarai Jessica Wongso secara langsung dari balik tahanan. Dalam video trailer yang diluncurkannya, ditampilkan juga sejumlah wawancara eksklusif yang dilakukan dengan beberapa narasumber. Mulai dari ayah dan saudara kembar  Mirna Salihin, pengacara Jessica Wongso, jurnalis yang mendalami kasus tersebut, hingga bagaimana saat itu kasus ini begitu ramai diberitakan oleh media massa Indonesia dan internasional.</string>
    
</resources>
```

> `Colors.xml`
```
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="black">#FF000000</color>
    <color name="white">#FFFFFFFF</color>
    <color name="blue">#3700B3</color>
    <color name="pink">#FFC0CB</color>
    <color name="colorPrimary">#3F5185</color>
    <color name="colorPrimaryDark">#303F9F</color>
    <color name="colorAccent">#FF4081</color>
    <color name="salem">#F8C6E6</color>
    <color name ="purple">#E3A2ED</color>
    <color name="biru">#8FC2EA</color>
    <color name="hijaumuda">#C2E69C</color>
    <color name="cream">#E6C18A</color>
    <color name="coklat">#65362c</color>
    <color name="abu">#B0B0B2</color>
    <color name="tosca">#70AE98</color>
    <color name="soft">#AED9EA</color>
    <color name="pastel">#5E96AE</color>
</resources>
```

> `Dimens.xml`
```
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <dimen name="padding_regular">10dp</dimen>
    <dimen name="line_spacing">5sp</dimen>
</resources>
```

## A. Code Project Hello World 
> `activity_hello.xml`
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".HelloActivity">
    <ImageView
        android:id="@+id/background"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:background="@drawable/bgcream"
        android:adjustViewBounds="true"
        android:scaleType="centerCrop"/>
    <TextView
        android:id="@+id/txthello"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:gravity="center"
        android:text="Hello World"
        android:textColor="@color/coklat"
        android:textSize="20pt"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.503"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.413"
        tools:ignore="TextSizeCheck" />
</androidx.constraintlayout.widget.ConstraintLayout>
```

> `HelloActivity.java`
```
package com.projectzulaeha;
import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
public class HelloActivity extends AppCompatActivity{
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_hello);
    }
}
```

## B. Code Project Count
> `activity_count.xml`
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:ignore="ExtraText"
    tools:context=".CountActivity">
    <ImageView
        android:id="@+id/background"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:background="@drawable/bgbiru"
        android:adjustViewBounds="true"
        android:scaleType="centerCrop" />
    <Button
        android:id="@+id/button_limit"
        android:layout_width="354dp"
        android:layout_height="76dp"
        android:layout_marginStart="8dp"
        android:layout_marginTop="16dp"
        android:layout_marginEnd="8dp"
        android:background="@color/pastel"
        android:onClick="setLimit"
        android:text="Masukkan Angka Limit"
        android:textColor="@android:color/black"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.507"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        tools:ignore="UsingOnClickInXml,VisualLintButtonSize" />
    <Button
        android:id="@+id/button_count"
        android:layout_width="173dp"
        android:layout_height="70dp"
        android:layout_marginStart="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="24dp"
        android:background="@color/pastel"
        android:onClick="countUp"
        android:text="Count"
        android:textColor="@android:color/black"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.039"
        app:layout_constraintStart_toStartOf="parent"
        tools:ignore="UsingOnClickInXml,VisualLintButtonSize" />
    <Button
        android:id="@+id/button_restart"
        android:layout_width="173dp"
        android:layout_height="72dp"
        android:layout_marginStart="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="24dp"
        android:background="@color/pastel"
        android:onClick="back1"
        android:text="Restart"
        android:textColor="@android:color/black"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.965"
        app:layout_constraintStart_toStartOf="parent"
        tools:ignore="UsingOnClickInXml" />
    <TextView
        android:id="@+id/show_count"
        android:layout_width="305dp"
        android:layout_height="442dp"
        android:layout_marginTop="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="8dp"
        android:gravity="center_vertical"
        android:text="1"
        android:textAlignment="center"
        android:textColor="@color/colorAccent"
        android:textSize="160sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toTopOf="@id/button_count"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.505"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@id/button_limit"
        app:layout_constraintVertical_bias="0.51"
        tools:ignore="RtlCompat" />
</androidx.constraintlayout.widget.ConstraintLayout>
```

> `CountActivity.java`
```
package com.projectzulaeha;
import android.app.AlertDialog;
import android.content.DialogInterface;
import android.graphics.Color;
import android.os.Bundle;
import android.view.View;
import android.widget.EditText;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;
public class CountActivity extends AppCompatActivity {
    private TextView show_count;
    private int count = 1;
    private long fibNMinus1 = 1;
    private long fibNMinus2 = 1;
    private int limit = -1; // Inisialisasi limit dengan nilai default
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_count);
        show_count = findViewById(R.id.show_count);
    }
    public void countUp(View view) {
        if (count == 0) {
            show_count.setText("0");
        }
        else if (count == 1) {
            show_count.setText("1");
        }
        else {
            if (limit != -1 && count > limit) {
                // Jika count melebihi limit, atur ulang perhitungan
                count = 0;
                fibNMinus1 = 1;
                fibNMinus2 = 0;
                show_count.setText(getString(R.string.count_initial_value));
            }
            else {
                long fibCurrent = fibNMinus1 + fibNMinus2;
                fibNMinus2 = fibNMinus1;
                fibNMinus1 = fibCurrent;
                //Mengatur warna teks berdasarkan angka Fibonacci
                int colorResId = R.color.colorAccent; // Warna Default
                switch (count % 11) {
                    case 1:
                        colorResId = R.color.colorAccent; // Warna Pink Tua
                        break;
                    case 2:
                        colorResId = R.color.hijaumuda; // Warna Hijau Muda
                        break;
                    case 3:
                        colorResId = R.color.purple; // Warna Ungu
                        break;
                    case 4:
                        colorResId = R.color.salem; // Warna Salem
                        break;
                    case 5:
                        colorResId = R.color.birumuda; // Warna Biru Muda
                        break;
                    case 6 :
                        colorResId = R.color.kuning; // Warna Kuning
                        break;
                    case 7:
                        colorResId = R.color.hijau; // Warna Hijau
                        break;
                    case 8:
                        colorResId = R.color.cream; // Warna Cream
                        break;
                    case 9:
                        colorResId = R.color.pink; // Warna Pink
                        break;
                    case 10:
                        colorResId = R.color.biru; // Warna Biru
                        break;
                    case 11:
                        colorResId = R.color.orange; // Warna Orange
                        break;
                }
                show_count.setTextColor(getResources().getColor(colorResId));
                show_count.setText(String.valueOf(fibCurrent));
            }
        }
        count++;
    }
    public void back1(View view) {
        count = 1;
        fibNMinus1 = 1;
        fibNMinus2 = 0;
        show_count.setText(getString(R.string.count_initial_value));
    }
    public void setLimit(View view) {
        // Create and display a dialog to set the limit
        AlertDialog.Builder builder = new AlertDialog.Builder(this);
        builder.setTitle("Set Limit");
        final EditText input = new EditText(this);
        input.setInputType(android.text.InputType.TYPE_CLASS_NUMBER);
        builder.setView(input);
        builder.setPositiveButton("OK", new DialogInterface.OnClickListener() {
            @Override
            public void onClick(DialogInterface dialog, int which) {
                // Get the limit from the input and set it for calculations
                String limitStr = input.getText().toString();
                limit = Integer.parseInt(limitStr);
            }
        });
        builder.setNegativeButton("Cancel", new DialogInterface.OnClickListener() {
            @Override
            public void onClick(DialogInterface dialog, int which) {
                dialog.cancel();
            }
        });
        builder.show();
    }
}
```

## C. Code Project Scroll Movie
> `activity_scrollmovie.xml`
```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    xmlns:tools="http://schemas.android.com/tools"
    tools:context=".SianidaActivity">
    <TextView
        android:id="@+id/article_heading"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:background="@color/abu"
        android:padding="@dimen/padding_regular"
        android:text="@string/article_title"
        android:textAppearance="@android:style/TextAppearance.DeviceDefault.Large"
        android:textColor="@android:color/white"
        android:textStyle="bold" />
    <ScrollView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/article_heading">
        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical">
            <TextView
                android:id="@+id/article_subheading"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:padding="@dimen/padding_regular"
                android:text="@string/article_subtitle"
                android:textAlignment="center"
                android:textAppearance="@android:style/TextAppearance.DeviceDefault"
                android:textColor="#1AA0C1" />
            <TextView
                android:id="@+id/article"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:autoLink="web"
                android:lineSpacingExtra="@dimen/line_spacing"
                android:padding="@dimen/padding_regular"
                android:text="@string/article_text"
                tools:ignore="VisualLintLongText" />
        </LinearLayout>
    </ScrollView>
</RelativeLayout>
```

> `SianidaActivity.java`
```
package com.projectzulaeha;
import android.os.Bundle;
import androidx.appcompat.app.AppCompatActivity;
public class SianidaActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState){
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_scrollmovie);
    }
}
```


## D. Code Project Two Activity
> `activity_twoactivity.xml`
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    xmlns:tools="http://schemas.android.com/tools"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    tools:context=".TwoActivity">
    <ImageView
        android:id="@+id/background"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:adjustViewBounds="true"
        android:scaleType="centerCrop"
        android:src="@drawable/bghijau" />
    <TextView
        android:id="@+id/text_header_reply"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginTop="16dp"
        android:text="@string/text_header_reply"
        android:textAppearance="@style/TextAppearance.AppCompat.Medium"
        android:textStyle="bold"
        android:visibility="invisible"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"/>
    <TextView
        android:id="@+id/text_message_reply"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginTop="8dp"
        android:visibility="invisible"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/text_header_reply" />
    <Button
        android:id="@+id/button_main"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="16dp"
        android:layout_marginRight="16dp"
        android:text="@string/button_main"
        android:background="@color/pink"
        android:onClick="LaunchSecondActivity"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        tools:ignore="UsingOnClickInXml"/>
    <EditText
        android:id="@+id/editText_main"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="16dp"
        android:ems="10"
        android:hint="@string/editText_main"
        android:inputType="textLongMessage"
        android:minHeight="48dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toStartOf="@+id/button_main"
        app:layout_constraintStart_toStartOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>
```

> `activity_twoact2.xml`
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    xmlns:tools="http://schemas.android.com/tools"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    tools:context=".Two2Activity">
    <ImageView
        android:id="@+id/background"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:adjustViewBounds="true"
        android:scaleType="centerCrop"
        android:src="@drawable/bghijau" />
    <TextView
        android:id="@+id/text_header"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginTop="16dp"
        android:text="@string/text_header"
        android:textAppearance="@style/TextAppearance.AppCompat.Medium"
        android:textStyle="bold"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />
    <TextView
        android:id="@+id/text_message"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginTop="8dp"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/text_header" />
    <Button
        android:id="@+id/button_second"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="16dp"
        android:layout_marginRight="16dp"
        android:text="@string/buttton_second"
        android:onClick="returnReply"
        android:background="@color/pink"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        tools:ignore="UsingOnClickInXml" />
    <EditText
        android:id="@+id/editText_second"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="16dp"
        android:ems="10"
        android:hint="@string/editText_second"
        android:inputType="textLongMessage"
        android:minHeight="48dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toStartOf="@+id/button_second"
        app:layout_constraintStart_toStartOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>
```

> `TwoActivity.java`
```
package com.projectzulaeha;
import androidx.appcompat.app.AppCompatActivity;
import android.content.Intent;
import android.os.Bundle;
import android.util.Log;
import android.view.View;
import android.widget.EditText;
import android.widget.TextView;
public class TwoActivity extends AppCompatActivity {
    private static final String LOG_TAG = TwoActivity.class.getSimpleName();
    public static final String EXTRA_MESSAGE = "com.example.android.Two2Activity.extra.MESSAGE";
    public static final int TEXT_REQUEST = 1;
    private EditText mMessageEditText;
    private TextView mReplyHeadTextView;
    private TextView mReplyTextView;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_twoactivity);
        mMessageEditText = findViewById(R.id.editText_main);
        mReplyHeadTextView = findViewById(R.id.text_header_reply);
        mReplyTextView = findViewById(R.id.text_message_reply);
    }
    public void LaunchSecondActivity(View view) {
        Log.d(LOG_TAG, "Button clicked!");
        Intent intent = new Intent(this, Two2Activity.class);
        String message = mMessageEditText.getText().toString();
        intent.putExtra(EXTRA_MESSAGE, message);
        startActivityForResult(intent, TEXT_REQUEST);
    }
    @Override
    public void onActivityResult(int requestCode, int resultCode, Intent data) {
        super.onActivityResult(requestCode, resultCode, data);
        if (requestCode == TEXT_REQUEST) {
            if (resultCode == RESULT_OK) {
                String reply = data.getStringExtra(Two2Activity.EXTRA_REPLY);
                mReplyHeadTextView.setVisibility(View.VISIBLE);
                mReplyTextView.setText(reply);
                mReplyTextView.setVisibility(View.VISIBLE);
            }
        }
    }
}
```

> `Two2Activity.java`
```
package com.projectzulaeha;
import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.EditText;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;
public class Two2Activity extends AppCompatActivity {
    public static final String EXTRA_REPLY ="com.example.android.Two2Activity.extra.REPLY";
    public static final String EXTRA_MESSAGE ="com.example.android.Two2Activity.extra.MESSAGE";
    private EditText mReply;
    @Override
    protected void onCreate(Bundle savedInstanceState){
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_twoact2);
        mReply = findViewById(R.id.editText_second);
        Intent intent = getIntent();
        String message = intent.getStringExtra(Two2Activity.EXTRA_MESSAGE);
        TextView textView = findViewById(R.id.text_message);
        textView.setText(message);
    }
    public void returnReply(View view){
        String reply = mReply.getText().toString();
        Intent replyIntent = new Intent();
        setResult(RESULT_OK, replyIntent);
        finish();
    }
}
```

## E. Code Project Set Alarm
> Pertama, buatlah button terlebih dahulu pada `activity_main.xml`, bersama dengan button aplikasi lainnya :
```
<Button
        android:id="@+id/btnSetAlarm"
        android:layout_width="150dp"
        android:layout_height="60dp"
        android:layout_below="@+id/btnTwoActivity"
        android:layout_alignParentStart="true"
        android:layout_alignParentEnd="true"
        android:layout_marginStart="100dp"
        android:layout_marginTop="20dp"
        android:layout_marginEnd="100dp"
        android:onClick="btnSetAlarm"
        android:background="@color/tosca"
        android:text="Set Alarm"
        tools:ignore="UsingOnClickInXml"
        android:scaleType="centerCrop"/>
```

> Lalu tambahkan code Implicit Intent pada `MainActivity,java` :
```
findViewById(R.id.btnSetAlarm).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Panggil metode untuk mengatur alarm
                setAlarm();
            }
        });
    }
    private void setAlarm() {
        Intent alarm = new Intent(android.provider.AlarmClock.ACTION_SET_ALARM);
        startActivity(alarm);
    }
```

> - Selanjutnya buka `AndroidManifest.xml` dan tambahkan code untuk izin membuka Alarm :
```
<uses-permission android:name="com.android.alarm.permission.SET_ALARM" />
```

- Tambahkan code berikut pada bagian *application* agar set alarm dapat berjalan :
```
<activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.SET_ALARM" />
                <category android:name="android.intent.category.DEFAULT" />
            </intent-filter>
</activity>
```

> **Hasil Program Tugas 1 :**  
![menupert9](https://github.com/zulaeha168/ProjectUAS_PM1/assets/130324650/994dd90e-6cf7-44ea-87c1-7cb964ac46fc)



## Penjelasan & Hasil Program Tugas 2

1. Menu Utama 
Pertama yang harus kita lakukan adalah mengganti tampilan menu utamanya dengan code yang baru agar ikon tombol berubah menjadi gambar, caranya adalah :

Jika awal pembuatan project kita memilih template Empty Views Activity, maka pada layout otomatis terbuat file `activity_main.xml` dan pada java akan ada `MainActivity.java`. Maka langsung saja kita buka `activity_main.xml`, dan buat code seperti berikut ini:

```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">
    <RelativeLayout
        android:layout_width="500dp"
        android:layout_height="match_parent"
        android:background="@drawable/bgpink">
    </RelativeLayout>
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_marginLeft="16dp"
        android:layout_marginTop="100dp"
        android:layout_marginRight="16dp"
        android:orientation="vertical">
        <TextView
            android:id="@+id/textView"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:fontFamily="serif"
            android:text="Menu Program"
            android:textAlignment="center"
            android:textColor="@color/black"
            android:textSize="34sp"
            android:textStyle="bold" />
        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="150dp"
            android:layout_margin="5dp"
            android:orientation="horizontal">
            <androidx.cardview.widget.CardView
                android:id="@+id/cdMenu1"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_margin="10dp"
                android:layout_weight="1"
                app:cardCornerRadius="20dp"
                app:cardElevation="7dp">
                <LinearLayout
                    android:layout_width="match_parent"
                    android:layout_height="match_parent"
                    android:orientation="vertical">
                    <ImageView
                        android:id="@+id/imageView0"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:layout_margin="16dp"
                        android:layout_weight="1"
                        app:srcCompat="@drawable/iconhello" />
                    <TextView
                        android:id="@+id/textView0"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:fontFamily="serif"
                        android:text="Hello World"
                        android:textAlignment="center"
                        android:textSize="18dp"
                        android:textStyle="bold" />
                </LinearLayout>
            </androidx.cardview.widget.CardView>
            <androidx.cardview.widget.CardView
                android:id="@+id/cdMenu2"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_margin="10dp"
                android:layout_weight="1"
                app:cardCornerRadius="20dp"
                app:cardElevation="7dp">
                <LinearLayout
                    android:layout_width="match_parent"
                    android:layout_height="match_parent"
                    android:orientation="vertical">
                    <ImageView
                        android:id="@+id/imageView1"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:layout_margin="16dp"
                        android:layout_weight="1"
                        app:srcCompat="@drawable/iconcount" />
                    <TextView
                        android:id="@+id/textView1"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:fontFamily="serif"
                        android:text="Fibonacci"
                        android:textAlignment="center"
                        android:textSize="18dp"
                        android:textStyle="bold" />
                </LinearLayout>
            </androidx.cardview.widget.CardView>
        </LinearLayout>
        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="150dp"
            android:layout_margin="5dp"
            android:orientation="horizontal">
            <androidx.cardview.widget.CardView
                android:id="@+id/cdMenu3"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_margin="10dp"
                android:layout_weight="1"
                app:cardCornerRadius="20dp"
                app:cardElevation="7dp">
                <LinearLayout
                    android:layout_width="match_parent"
                    android:layout_height="match_parent"
                    android:orientation="vertical">
                    <ImageView
                        android:id="@+id/imageView2"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:layout_margin="16dp"
                        android:layout_weight="1"
                        app:srcCompat="@drawable/iconscroll" />
                    <TextView
                        android:id="@+id/textView2"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:fontFamily="serif"
                        android:text="Scroll Movie"
                        android:textAlignment="center"
                        android:textSize="18dp"
                        android:textStyle="bold" />
                </LinearLayout>
            </androidx.cardview.widget.CardView>
            <androidx.cardview.widget.CardView
                android:id="@+id/cdMenu4"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_margin="10dp"
                android:layout_weight="1"
                app:cardCornerRadius="20dp"
                app:cardElevation="7dp">
                <LinearLayout
                    android:layout_width="match_parent"
                    android:layout_height="match_parent"
                    android:orientation="vertical">
                    <ImageView
                        android:id="@+id/imageView3"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:layout_margin="16dp"
                        android:layout_weight="1"
                        app:srcCompat="@drawable/iconalarm" />
                    <TextView
                        android:id="@+id/textView3"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:fontFamily="serif"
                        android:text="Alarm"
                        android:textAlignment="center"
                        android:textSize="18dp"
                        android:textStyle="bold" />
                </LinearLayout>
            </androidx.cardview.widget.CardView>
        </LinearLayout>
        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="150dp"
            android:layout_margin="5dp"
            android:orientation="horizontal">
            <androidx.cardview.widget.CardView
                android:id="@+id/cdMenu5"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_margin="10dp"
                android:layout_weight="1"
                app:cardCornerRadius="20dp"
                app:cardElevation="7dp">
                <LinearLayout
                    android:layout_width="match_parent"
                    android:layout_height="match_parent"
                    android:orientation="vertical">
                    <ImageView
                        android:id="@+id/imageView4"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:layout_margin="16dp"
                        android:layout_weight="1"
                        app:srcCompat="@drawable/iconactivity" />
                    <TextView
                        android:id="@+id/textView4"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:fontFamily="serif"
                        android:text="Two Activity"
                        android:textAlignment="center"
                        android:textSize="18dp"
                        android:textStyle="bold" />
                </LinearLayout>
            </androidx.cardview.widget.CardView>
            <androidx.cardview.widget.CardView
                android:id="@+id/cdMenu6"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_margin="10dp"
                android:layout_weight="1"
                app:cardCornerRadius="20dp"
                app:cardElevation="7dp">
                <LinearLayout
                    android:layout_width="match_parent"
                    android:layout_height="match_parent"
                    android:orientation="vertical">
                    <ImageView
                        android:id="@+id/imageView5"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:layout_margin="16dp"
                        android:layout_weight="1"
                        app:srcCompat="@drawable/iconmaps" />
                    <TextView
                        android:id="@+id/textView5"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:fontFamily="serif"
                        android:text="Maps"
                        android:textAlignment="center"
                        android:textSize="18dp"
                        android:textStyle="bold" />
                </LinearLayout>
            </androidx.cardview.widget.CardView>
        </LinearLayout>
    </LinearLayout>
</RelativeLayout>
```

> - Setelah itu kita buka `MainActivity.java` untuk menambahkan code intent untuk masing-masing tombol :
```
package com.projectzulaeha;
import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.view.View;
import androidx.appcompat.app.AppCompatActivity;
public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        findViewById(R.id.cdMenu4).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                setAlarm();
            }
        });
        findViewById(R.id.cdMenu1).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Ketika tombolSatu ditekan, pindah ke HelloActivity
                Intent helloworld = new Intent(MainActivity.this, HelloActivity.class);
                startActivity(helloworld);
            }
        });
        findViewById(R.id.cdMenu2).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Ketika tombolDua ditekan, lakukan aksi yang diinginkan
                // Misalnya, pindah ke aktivitas lain atau jalankan fungsi khusus
                Intent toast = new Intent(MainActivity.this, CountActivity.class);
                startActivity(toast);
            }
        });
        findViewById(R.id.cdMenu3).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Ketika tombolDua ditekan, lakukan aksi yang diinginkan
                // Misalnya, pindah ke aktivitas lain atau jalankan fungsi khusus
                Intent sianida = new Intent(MainActivity.this, SianidaActivity.class);
                startActivity(sianida);
            }
        });
        findViewById(R.id.cdMenu5).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Ketika tombolDua ditekan, lakukan aksi yang diinginkan
                // Misalnya, pindah ke aktivitas lain atau jalankan fungsi khusus
                Intent twoactivity = new Intent(MainActivity.this, TwoActivity.class);
                startActivity(twoactivity);
            }
        });
        findViewById(R.id.cdMenu6).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Example location: Jakarta, Indonesia
                Uri geoLocation = Uri.parse("geo:-6.2088,106.8456");
                openMaps(geoLocation);
            }
        });
    }
    private void setAlarm() {
        Intent alarmIntent = new Intent(android.provider.AlarmClock.ACTION_SET_ALARM);
        // Add extra details for the alarm, e.g., alarm time, label, etc.
        // alarmIntent.putExtra(...
        startActivity(alarmIntent);
    }
    private void openMaps(Uri geoLocation) {
        Intent maps = new Intent(Intent.ACTION_VIEW);
        maps.setData(geoLocation);
        if (maps.resolveActivity(getPackageManager()) != null) {
            startActivity(maps);
        }
    }
}
```

> Button *HelloWorld, Count, Sianida dan TwoActivity* menggunakan Explicit Intent, dan untuk project *SetAlarm* beserta *Maps* menggunakan Implicit Intent.
> Menu halaman utama dan tombol-tombol aplikasi sudah berhasil dibuat. Maka selanjutnya yang kita lakukan adalah menambahkan coding pada `AndroidManifest.xml` agar aplikasi dapat berjalan.
**2. AndroidManifest.xml**
Didalam `AndroidManifest.xml` kita tambahkan semua java class dari semua project kita sebelumnya. Berikut nama java class dari berbagai project yang telah saya buat:

a. Project Hello World = HelloActivity.java 

b. Project Count = CountActivity.java 

c. Project Scroll Movie = SianidaActivity.java 

d. Project TwoActivity = TwoActivity.java dan Two2Activity.java 

e. Project Set Alarm = MainActivity.java 

f. Project Maps = MainActivity.java (karena merupakan Implicit Intent, jadi code untuk SetAlarm dan Maps langsung dibuat disini)

```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">
    <uses-permission
        android:name="com.android.alarm.permission.SET_ALARM" />
    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.Design.Light"
        tools:targetApi="31">
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.SET_ALARM" />
                <category android:name="android.intent.category.DEFAULT" />
                <action android:name="android.intent.action.VIEW" />
                <data android:scheme="geo" />
                <category android:name="android.intent.category.DEFAULT" />
            </intent-filter>
        </activity>
        <activity
            android:name=".HelloActivity"
            android:exported="true" />
        <activity
            android:name=".TwoActivity"
            android:exported="true" />
        <activity
            android:name=".Two2Activity"
            android:exported="true" />
        <activity
            android:name=".CountActivity"
            android:exported="true" />
        <activity
            android:name=".SianidaActivity"
            android:exported="true" />
        <activity
            android:name=".SplashScreen"
            android:exported="true"
            android:theme="@style/SplashScreen">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>
</manifest>
```

**3. Code All Projects (XML files / res)**
> Pada menu values :
- `Strings.xml` 
```
<resources>
    <string name="app_name">projectzulaeha</string>
    <string name="Hello_World">Hello World!!</string>
    <string name="button_main">Send</string>
    <string name="editText_main">Enter Your Message Here</string>
    <string name="text_header">Message Received</string>
    <string name="buttton_second">Reply</string>
    <string name="editText_second">Enter Your Reply Here</string>
    <string name="text_header_reply">Reply Received</string>
    <string name="button_label_toast">Toast</string>
    <string name="button_label_count">Count</string>
    <string name="count_initial_value">1</string>
    <string name="toast_massage">Hello Toast!</string>
    <string name="button_label_restart">Restart</string>
    <string name="enter_fibonacci_limit">Masukkan Angka Limit</string>
    <string name="article_title"> Kasus Sianida</string>
    <string name="article_subtitle">ICE COLD!</string>
    <string name="article_text"> Film dokumenter Ice Cold: Murder, Coffee and Jessica Wongso memaparkan pertanyaan tak terjawab tentang persidangan yang dilalui Jessica Wongso. Dengan menyajikan perspektif baru, film ini hadir bertahun-tahun setelah kematian sahabat Jessica, Wayan Mirna Salihin.
Film ini menggambarkan bagaimana Jessica yang mengajak teman-temannya, termasuk Mirna, untuk bertemu setelah sekian lama tak berjumpa. Pertemuan di salah satu kafe di mal ibu kota tersebut pun berlangsung lancar, sebelum akhirnya Mirna pingsan sesaat setelah meminum kopi yang sebelumnya dipesan Jessica.Dokumenter ini turut menyajikan rekaman CCTV pada waktu kejadian, berbagai footage berita saat persidangan berlangsung, hingga wawancara eksklusif dengan beberapa sumber, termasuk Jessica Wongso.
Persidangan atas dugaan pembunuhan Mirna Salihin digelar lima bulan setelah kematiannya. Sidang tersebut melalui 32 kali persidangan dengan menghadirkan puluhan saksi di pengadilan. Hasilnya, Jessica Wongso divonis bersalah atas kematian Mirna dan dijatuhi hukuman 20 tahun penjara.
Kasus yang berjalan cukup lama tersebut menyita banyak perhatian dari masyarakat Indonesia. Musababnya, banyak misteri tak terjawab selama rangkaian persidangan yang panjang tersebut. Salah satunya adalah mengenai akses untuk mendapatkan bubuk sianida yang tidak bisa didapatkan oleh orang sembarangan. Selain itu, motif Jessica di balik pembunuhan tersebut pun belum menemukan jawabannya.
Film dokumenter buatan Netflix ini menyoroti rangkaian persidangan yang saat itu menjadi sidang pertama yang disiarkan secara langsung di berbagai stasiun televisi Indonesia. Selain itu, kasus ini juga diliput secara intens oleh media massa, baik nasional maupun internasional.Tak hanya itu, pihak rumah produksi Beach House Pictures juga berhasil mendapatkan akses untuk mewawancarai Jessica Wongso secara langsung dari balik tahanan. Dalam video trailer yang diluncurkannya, ditampilkan juga sejumlah wawancara eksklusif yang dilakukan dengan beberapa narasumber. Mulai dari ayah dan saudara kembar  Mirna Salihin, pengacara Jessica Wongso, jurnalis yang mendalami kasus tersebut, hingga bagaimana saat itu kasus ini begitu ramai diberitakan oleh media massa Indonesia dan internasional.</string>
</resources>
```

- `Colors.xml` 
```
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="black">#FF000000</color>
    <color name="white">#FFFFFFFF</color>
    <color name="blue">#3700B3</color>
    <color name="pink">#FFC0CB</color>
    <color name="colorPrimary">#3F5185</color>
    <color name="colorPrimaryDark">#303F9F</color>
    <color name="colorAccent">#FF4081</color>
    <color name="birumuda">#ABCBFA</color>
    <color name="salem">#F8C6E6</color>
    <color name ="purple">#E3A2ED</color>
    <color name="hijau">#92A676</color>
    <color name="biru">#8FC2EA</color>
    <color name="hijaumuda">#C2E69C</color>
    <color name="kuning">#FFEB3B</color>
    <color name="orange">#FF9800</color>
    <color name="cream">#E6C18A</color>
</resources>
```

- `Dimens.xml` 
```
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <dimen name="padding_regular">10dp</dimen>
    <dimen name="line_spacing">5sp</dimen>
</resources>
```

> Pada menu themes :
- `themes.xml`
```
<resources xmlns:tools="http://schemas.android.com/tools">
    <!-- Base application theme. -->
    <style name="SplashScreen" parent="Theme.MaterialComponents.DayNight.NoActionBar">
        <item name="android:windowBackground">@drawable/splashscreen</item>
        <item name="android:statusBarColor">?attr/colorOnPrimary</item>
    </style>
</resources>
```

> Pada menu drawable :
- `backgroundlauncher.xml`
```
<?xml version="1.0" encoding="utf-8"?>
<layer-list xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:drawable="@color/birumuda"/>
    <item>
        <bitmap
            android:src="@drawable/logo"
            android:gravity="center" />
    </item>
</layer-list>
```

***A. Code Project Splash Screen**

> `SplashScreen.java`
```
package com.projectzulaeha;
import android.content.Intent;
import android.os.Bundle;
import android.os.Handler;
import androidx.appcompat.app.AppCompatActivity;
public class SplashScreen extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        new Handler().postDelayed(new Runnable() {
            @Override
            public void run() {
                startActivity(new Intent(SplashScreen.this, MainActivity.class));
                finish();
            }
        }, 2500);
    }
}
```

**B. Code Project Hello World**
> `activity_hello.xml`
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".HelloActivity">
    <ImageView
        android:id="@+id/background"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:background="@drawable/bgcream"
        android:adjustViewBounds="true"
        android:scaleType="centerCrop"/>
    <TextView
        android:id="@+id/txthello"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:gravity="center"
        android:text="Hello World!!"
        android:textColor="@color/coklat"
        android:textSize="20pt"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.503"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.413"
        tools:ignore="TextSizeCheck" />
</androidx.constraintlayout.widget.ConstraintLayout>
```

> `HelloActivity.java`
```
package com.projectzulaeha;
import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
public class HelloActivity extends AppCompatActivity{
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_hello);
    }
}
```

**C. Code Project Count**
> `activity_count.xml`
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:ignore="ExtraText"
    tools:context=".CountActivity">
    <ImageView
        android:id="@+id/background"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:background="@drawable/bgbiru"
        android:adjustViewBounds="true"
        android:scaleType="centerCrop" />
    <Button
        android:id="@+id/button_limit"
        android:layout_width="354dp"
        android:layout_height="76dp"
        android:layout_marginStart="8dp"
        android:layout_marginTop="16dp"
        android:layout_marginEnd="8dp"
        android:background="@color/pastel"
        android:onClick="setLimit"
        android:text="Masukkan Angka Limit"
        android:textColor="@android:color/white"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.507"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        tools:ignore="UsingOnClickInXml,VisualLintButtonSize" />
    <Button
        android:id="@+id/button_count"
        android:layout_width="173dp"
        android:layout_height="70dp"
        android:layout_marginStart="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="24dp"
        android:background="@color/pastel"
        android:onClick="countUp"
        android:text="Count"
        android:textColor="@android:color/white"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.039"
        app:layout_constraintStart_toStartOf="parent"
        tools:ignore="UsingOnClickInXml,VisualLintButtonSize" />
    <Button
        android:id="@+id/button_restart"
        android:layout_width="173dp"
        android:layout_height="72dp"
        android:layout_marginStart="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="24dp"
        android:background="@color/pastel"
        android:onClick="back1"
        android:text="Restart"
        android:textColor="@android:color/white"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.965"
        app:layout_constraintStart_toStartOf="parent"
        tools:ignore="UsingOnClickInXml" />
    <TextView
        android:id="@+id/show_count"
        android:layout_width="305dp"
        android:layout_height="442dp"
        android:layout_marginTop="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="8dp"
        android:gravity="center_vertical"
        android:text="1"
        android:textAlignment="center"
        android:textColor="@color/black"
        android:textSize="160sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toTopOf="@id/button_count"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.505"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@id/button_limit"
        app:layout_constraintVertical_bias="0.51"
        tools:ignore="RtlCompat" />
</androidx.constraintlayout.widget.ConstraintLayout>
```

> `CountActivity.java`
```
package com.projectzulaeha;
import android.annotation.SuppressLint;
import android.app.AlertDialog;
import android.content.DialogInterface;
import android.graphics.Color;
import android.os.Bundle;
import android.view.View;
import android.widget.EditText;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;
public class CountActivity extends AppCompatActivity {
    private TextView show_count;
    private int count = 1;
    private long fibNMinus1 = 1;
    private long fibNMinus2 = 1;
    private int limit = -1; // Inisialisasi limit dengan nilai default
    @SuppressLint("MissingInflatedId")
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_count);
        show_count = findViewById(R.id.show_count);
    }
    public void countUp(View view) {
        if (count == 0) {
            show_count.setText("0");
        }
        else if (count == 1) {
            show_count.setText("1");
        }
        else {
            if (limit != -1 && count > limit) {
                // Jika count melebihi limit, atur ulang perhitungan
                count = 0;
                fibNMinus1 = 1;
                fibNMinus2 = 0;
                show_count.setText(getString(R.string.count_initial_value));
            }
            else {
                long fibCurrent = fibNMinus1 + fibNMinus2;
                fibNMinus2 = fibNMinus1;
                fibNMinus1 = fibCurrent;
                //Mengatur warna teks berdasarkan angka Fibonacci
                int colorResId = R.color.colorAccent; // Warna Default
                switch (count % 11) {
                    case 1:
                        colorResId = R.color.colorAccent; // Warna Pink Tua
                        break;
                    case 2:
                        colorResId = R.color.hijaumuda; // Warna Hijau Muda
                        break;
                    case 3:
                        colorResId = R.color.purple; // Warna Ungu
                        break;
                    case 4:
                        colorResId = R.color.salem; // Warna Salem
                        break;
                    case 5:
                        colorResId = R.color.birumuda; // Warna Biru Muda
                        break;
                    case 6 :
                        colorResId = R.color.kuning; // Warna Kuning
                        break;
                    case 7:
                        colorResId = R.color.hijau; // Warna Hijau
                        break;
                    case 8:
                        colorResId = R.color.cream; // Warna Cream
                        break;
                    case 9:
                        colorResId = R.color.pink; // Warna Pink
                        break;
                    case 10:
                        colorResId = R.color.biru; // Warna Biru
                        break;
                    case 11:
                        colorResId = R.color.orange; // Warna Orange
                        break;
                }
                show_count.setTextColor(getResources().getColor(colorResId));
                show_count.setText(String.valueOf(fibCurrent));
            }
        }
        count++;
    }
    public void back1(View view) {
        count = 1;
        fibNMinus1 = 1;
        fibNMinus2 = 0;
        show_count.setText(getString(R.string.count_initial_value));
    }
    public void setLimit(View view) {
        // Create and display a dialog to set the limit
        AlertDialog.Builder builder = new AlertDialog.Builder(this);
        builder.setTitle("Set Limit");
        final EditText input = new EditText(this);
        input.setInputType(android.text.InputType.TYPE_CLASS_NUMBER);
        builder.setView(input);
        builder.setPositiveButton("OK", new DialogInterface.OnClickListener() {
            @Override
            public void onClick(DialogInterface dialog, int which) {
                // Get the limit from the input and set it for calculations
                String limitStr = input.getText().toString();
                limit = Integer.parseInt(limitStr);
            }
        });
        builder.setNegativeButton("Cancel", new DialogInterface.OnClickListener() {
            @Override
            public void onClick(DialogInterface dialog, int which) {
                dialog.cancel();
            }
        });
        builder.show();
    }
}
```

**D. Code Project Scroll Movie**
> `activity_scrollmovie.xml`
```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    xmlns:tools="http://schemas.android.com/tools"
    tools:context=".SianidaActivity">
    <TextView
        android:id="@+id/article_heading"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:background="@color/abu"
        android:padding="@dimen/padding_regular"
        android:text="@string/article_title"
        android:textAppearance="@android:style/TextAppearance.DeviceDefault.Large"
        android:textColor="@android:color/white"
        android:textStyle="bold" />
    <ScrollView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/article_heading">
        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical">
            <TextView
                android:id="@+id/article_subheading"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:padding="@dimen/padding_regular"
                android:text="@string/article_subtitle"
                android:textAlignment="center"
                android:textAppearance="@android:style/TextAppearance.DeviceDefault"
                android:textColor="@color/colorPrimary" />
            <TextView
                android:id="@+id/article"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:autoLink="web"
                android:lineSpacingExtra="@dimen/line_spacing"
                android:padding="@dimen/padding_regular"
                android:text="@string/article_text"
                tools:ignore="VisualLintLongText" />
        </LinearLayout>
    </ScrollView>
</RelativeLayout>
```

> `SianidaActivity.java`
```
package com.projectzulaeha;
import android.os.Bundle;
import androidx.appcompat.app.AppCompatActivity;
public class SianidaActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState){
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_scrollmovie);
    }
}
```

## E. Code Project Two Activity
> `activity_twoactivity.xml`
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    xmlns:tools="http://schemas.android.com/tools"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    tools:context=".TwoActivity">
    <ImageView
        android:id="@+id/background"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:adjustViewBounds="true"
        android:scaleType="centerCrop"
        android:src="@drawable/bghijau" />
    <TextView
        android:id="@+id/text_header_reply"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginTop="16dp"
        android:text="@string/text_header_reply"
        android:textAppearance="@style/TextAppearance.AppCompat.Medium"
        android:textStyle="bold"
        android:visibility="invisible"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"/>
    <TextView
        android:id="@+id/text_message_reply"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginTop="8dp"
        android:visibility="invisible"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/text_header_reply" />
    <Button
        android:id="@+id/button_main"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="16dp"
        android:layout_marginRight="16dp"
        android:text="@string/button_main"
        android:background="@color/pink"
        android:onClick="LaunchSecondActivity"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        tools:ignore="UsingOnClickInXml"/>
    <EditText
        android:id="@+id/editText_main"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="16dp"
        android:ems="10"
        android:hint="@string/editText_main"
        android:inputType="textLongMessage"
        android:minHeight="48dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toStartOf="@+id/button_main"
        app:layout_constraintStart_toStartOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>
```

> `activity_two2activity.xml`
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    xmlns:tools="http://schemas.android.com/tools"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    tools:context=".Two2Activity">
    <ImageView
        android:id="@+id/background"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:adjustViewBounds="true"
        android:scaleType="centerCrop"
        android:src="@drawable/bghijau" />
    <TextView
        android:id="@+id/text_header"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginTop="16dp"
        android:text="@string/text_header"
        android:textAppearance="@style/TextAppearance.AppCompat.Medium"
        android:textStyle="bold"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />
    <TextView
        android:id="@+id/text_message"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginTop="8dp"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/text_header" />
    <Button
        android:id="@+id/button_second"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="16dp"
        android:layout_marginRight="16dp"
        android:text="@string/buttton_second"
        android:onClick="returnReply"
        android:background="@color/hijaumuda"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        tools:ignore="UsingOnClickInXml" />
    <EditText
        android:id="@+id/editText_second"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="16dp"
        android:ems="10"
        android:hint="@string/editText_second"
        android:inputType="textLongMessage"
        android:minHeight="48dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toStartOf="@+id/button_second"
        app:layout_constraintStart_toStartOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>
```

> `TwoActivity.java`
```
package com.projectzulaeha;
import androidx.appcompat.app.AppCompatActivity;
import android.content.Intent;
import android.os.Bundle;
import android.util.Log;
import android.view.View;
import android.widget.EditText;
import android.widget.TextView;
public class TwoActivity extends AppCompatActivity {
    private static final String LOG_TAG = TwoActivity.class.getSimpleName();
    public static final String EXTRA_MESSAGE = "com.example.android.Two2Activity.extra.MESSAGE";
    public static final int TEXT_REQUEST = 1;
    private EditText mMessageEditText;
    private TextView mReplyHeadTextView;
    private TextView mReplyTextView;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_twoactivity);
        mMessageEditText = findViewById(R.id.editText_main);
        mReplyHeadTextView = findViewById(R.id.text_header_reply);
        mReplyTextView = findViewById(R.id.text_message_reply);
    }
    public void LaunchSecondActivity(View view) {
        Log.d(LOG_TAG, "Button clicked!");
        Intent intent = new Intent(this, Two2Activity.class);
        String message = mMessageEditText.getText().toString();
        intent.putExtra(EXTRA_MESSAGE, message);
        startActivityForResult(intent, TEXT_REQUEST);
    }
    @Override
    public void onActivityResult(int requestCode, int resultCode, Intent data) {
        super.onActivityResult(requestCode, resultCode, data);
        if (requestCode == TEXT_REQUEST) {
            if (resultCode == RESULT_OK) {
                String reply = data.getStringExtra(Two2Activity.EXTRA_REPLY);
                mReplyHeadTextView.setVisibility(View.VISIBLE);
                mReplyTextView.setText(reply);
                mReplyTextView.setVisibility(View.VISIBLE);
            }
        }
    }
}
```

> `Two2Activity.java`
```
package com.projectzulaeha;
import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.EditText;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;
public class Two2Activity extends AppCompatActivity {
    public static final String EXTRA_REPLY ="com.example.android.Two2Activity.extra.REPLY";
    public static final String EXTRA_MESSAGE ="com.example.android.Two2Activity.extra.MESSAGE";
    private EditText mReply;
    @Override
    protected void onCreate(Bundle savedInstanceState){
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_two2activity);
        mReply = findViewById(R.id.editText_second);
        Intent intent = getIntent();
        String message = intent.getStringExtra(Two2Activity.EXTRA_MESSAGE);
        TextView textView = findViewById(R.id.text_message);
        textView.setText(message);
    }
    public void returnReply(View view){
        String reply = mReply.getText().toString();
        Intent replyIntent = new Intent();
        setResult(RESULT_OK, replyIntent);
        finish();
    }
}
```

**Code Project SetAlarm dan Maps**
> Pertama, buatlah ikon tombol terlebih dahulu pada `activity_main.xml`, bersama dengan ikon tombol aplikasi lainnya :
- `Set Alarm`
```
<androidx.cardview.widget.CardView
                android:id="@+id/cdMenu4"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_margin="10dp"
                android:layout_weight="1"
                app:cardCornerRadius="20dp"
                app:cardElevation="7dp">
                <LinearLayout
                    android:layout_width="match_parent"
                    android:layout_height="match_parent"
                    android:orientation="vertical">
                    <ImageView
                        android:id="@+id/imageView3"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:layout_margin="16dp"
                        android:layout_weight="1"
                        app:srcCompat="@drawable/iconalarm" />
                    <TextView
                        android:id="@+id/textView3"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:fontFamily="serif"
                        android:text="Alarm"
                        android:textAlignment="center"
                        android:textSize="18dp"
                        android:textStyle="bold" />
                </LinearLayout>
            </androidx.cardview.widget.CardView>
        </LinearLayout>
```

- `Maps`
```
<androidx.cardview.widget.CardView
                android:id="@+id/cdMenu6"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_margin="10dp"
                android:layout_weight="1"
                app:cardCornerRadius="20dp"
                app:cardElevation="7dp">
                <LinearLayout
                    android:layout_width="match_parent"
                    android:layout_height="match_parent"
                    android:orientation="vertical">
                    <ImageView
                        android:id="@+id/imageView5"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:layout_margin="16dp"
                        android:layout_weight="1"
                        app:srcCompat="@drawable/iconmaps" />
                    <TextView
                        android:id="@+id/textView5"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:fontFamily="serif"
                        android:text="Maps"
                        android:textAlignment="center"
                        android:textSize="18dp"
                        android:textStyle="bold" />
                </LinearLayout>
```

> Lalu tambahkan code Implicit Intent pada `MainActivity.java` :
- `SetAlarm`
```
findViewById(R.id.cdMenu4).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                setAlarm();
            }
        });
private void setAlarm() {
        Intent alarmIntent = new Intent(android.provider.AlarmClock.ACTION_SET_ALARM);
        // Add extra details for the alarm, e.g., alarm time, label, etc.
        // alarmIntent.putExtra(...
        startActivity(alarmIntent);
    }
```

- `Maps`
```
findViewById(R.id.cdMenu6).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Example location: Jakarta, Indonesia
                Uri geoLocation = Uri.parse("geo:-6.2088,106.8456");
                openMaps(geoLocation);
            }
        });
private void openMaps(Uri geoLocation) {
        Intent maps = new Intent(Intent.ACTION_VIEW);
        maps.setData(geoLocation);
        if (maps.resolveActivity(getPackageManager()) != null) {
            startActivity(maps);
        }
    }
```

> Selanjutnya buka `AndroidManifest.xml` dan tambahkan code untuk izin membuka Alarm :
```
<uses-permission android:name="com.android.alarm.permission.SET_ALARM" />
```

> Tambahkan code berikut pada bagian *application* agar set alarm dapat berjalan :
```
<activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.SET_ALARM" />
                <category android:name="android.intent.category.DEFAULT" />
                <action android:name="android.intent.action.VIEW" />
                <data android:scheme="geo" />
                <category android:name="android.intent.category.DEFAULT" />
            </intent-filter>
        </activity>
```

> **Hasil Program Tugas 2 :**
![menupert10](https://github.com/zulaeha168/ProjectUAS_PM1/assets/130324650/7ef23ea3-9101-4943-9d85-480d49edf367)



## Penjelasan & Hasil Program Tugas 3 

## Demo Tugas 1 
https://github.com/zulaeha168/ProjectUAS_PM1/assets/130324650/adbeece7-3d84-4c38-89b5-4c421f6f1033

## Demo Tugas 2
https://github.com/zulaeha168/ProjectUAS_PM1/assets/130324650/95069a47-4ba3-4b11-afb3-99e5e44c43d7
