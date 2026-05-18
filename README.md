Anggota Kelompok 
Muhammad Aditya Januar_202412049
Ahdam Ashari_202412039
Ninda Fadillah Heryanuryanti_202412029


source code, penjelasan dan dokumentasi

#Halaman Login 
<!DOCTYPE html> <!-- Menentukan dokumen menggunakan HTML5 -->

<html lang="id"> <!-- Bahasa halaman menggunakan Bahasa Indonesia -->

<head>

<meta charset="UTF-8"> <!-- Agar karakter tampil dengan benar -->

<meta name="viewport" content="width=device-width, initial-scale=1.0">
<!-- Membuat tampilan responsif -->

<title>Login Admin</title> <!-- Judul halaman -->

<style>

/* Mengatur seluruh elemen */
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

/* Mengatur tampilan body */
body{
    font-family:Arial,sans-serif;
    height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
    background:linear-gradient(135deg,#020617,#0f172a);
    overflow:hidden;
}

/* Kotak login */
.login-box{

    width:400px;

    background:#111827;

    padding:40px;

    border-radius:20px;

    box-shadow:
    0 0 25px rgba(59,130,246,.5);

    color:white;
}

/* Judul */
h1{

    text-align:center;

    margin-bottom:10px;
}

/* Paragraf */
p{

    text-align:center;

    color:#94a3b8;

    margin-bottom:30px;
}

/* Input username dan password */
input{

    width:100%;

    padding:15px;

    margin-bottom:20px;

    border:none;

    border-radius:12px;

    background:#020617;

    color:white;

    outline:none;
}

/* Tombol login */
button{

    width:100%;

    padding:15px;

    border:none;

    border-radius:12px;

    background:#2563eb;

    color:white;

    font-size:16px;

    font-weight:bold;

    cursor:pointer;
}

/* Efek hover tombol */
button:hover{

    background:#1d4ed8;
}

/* Pesan error */
#error{

    color:#fca5a5;

    text-align:center;

    margin-top:15px;
}

/* Box akun demo */
.demo{

    margin-top:25px;

    background:#020617;

    padding:15px;

    border-radius:12px;

    text-align:center;

    line-height:1.8;
}

/* Warna username dan password demo */
.demo span{

    color:#38bdf8;

    font-weight:bold;
}

</style>
</head>

<body>

<!-- Container utama login -->
<div class="login-box">

<!-- Judul login -->
<h1>🎓 Login Admin</h1>

<!-- Deskripsi -->
<p>Silakan login terlebih dahulu</p>

<!-- Form login -->
<form id="loginForm">

<!-- Input username -->
<input
type="text"
id="username"
placeholder="Username"
>

<!-- Input password -->
<input
type="password"
id="password"
placeholder="Password"
>

<!-- Tombol login -->
<button type="submit">
🔐 Login
</button>

<!-- Tempat pesan error -->
<div id="error"></div>

</form>

<!-- Informasi akun demo -->
<div class="demo">

<div>
Username :
<span>admin</span>
</div>

<div>
Password :
<span>12345</span>
</div>

</div>

</div>

<script>

/* Mengecek apakah user sudah login */
if(localStorage.getItem("isLogin")=="true"){

    /* Pindah ke dashboard */
    window.location.href="./dashboard.html";
}

/* Event saat form disubmit */
loginForm.onsubmit = function(e){

    /* Mencegah reload halaman */
    e.preventDefault();

    /* Validasi username dan password */
    if(
        username.value=="admin"
        &&
        password.value=="12345"
    ){

        /* Menyimpan status login */
        localStorage.setItem(
        "isLogin",
        "true"
        );

        /* Redirect ke dashboard */
        window.location.href=
        "./dashboard.html";

    }else{

        /* Menampilkan pesan error */
        error.innerHTML=
        "❌ Username atau Password salah!";
    }
}

</script>

</body>
</html>


#Halaman Dashboard 
<!DOCTYPE html> <!-- Menentukan dokumen menggunakan HTML5 -->

<html lang="id"> <!-- Bahasa halaman menggunakan Bahasa Indonesia -->

<head>

<meta charset="UTF-8"> <!-- Agar karakter tampil dengan benar -->

<meta name="viewport" content="width=device-width, initial-scale=1.0">
<!-- Membuat tampilan responsif -->

<title>Dashboard Mahasiswa</title> <!-- Judul halaman -->

<style>

/* Mengatur seluruh elemen */
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

/* Efek scroll halus */
html{
    scroll-behavior:smooth;
}

/* Tampilan utama body */
body{

    font-family:Arial,sans-serif;

    background:
    linear-gradient(135deg,#020617,#0f172a);

    color:white;

    min-height:100vh;

    padding:20px;

    transition:.3s;
}

/* LIGHT MODE */
body.light{

    background:#f1f5f9;

    color:black;
}

/* Card saat light mode */
body.light .card{

    background:white;

    color:black;
}

/* Sidebar saat light mode */
body.light .sidebar{

    background:#e2e8f0;
}

/* Paragraf light mode */
body.light p{

    color:#334155;
}

/* Input dan select light mode */
body.light input,
body.light select{

    background:white;

    color:black;

    border:1px solid #cbd5e1;
}

/* Table light mode */
body.light table{

    background:white;

    color:black;
}

/* Header tabel light mode */
body.light thead{

    background:#cbd5e1;
}

/* Hover tabel light mode */
body.light tbody tr:hover{

    background:#e2e8f0;
}

/* Link sidebar light mode */
body.light .sidebar li a{

    color:black;
}

/* Hamburger light mode */
body.light .hamburger{

    background:#cbd5e1;

    color:black;
}

/* Layout container */
.container{

    display:flex;

    gap:20px;

    align-items:flex-start;
}

/* Sidebar */
.sidebar{

    width:230px;

    background:#020617;

    border-radius:22px;

    padding:20px;

    height:calc(100vh - 40px);

    position:sticky;

    top:20px;

    overflow:hidden;

    transition:.3s;

    flex-shrink:0;
}

/* Sidebar saat disembunyikan */
.sidebar.hide{

    width:80px;
}

/* Menyembunyikan teks sidebar */
.sidebar.hide .menu-text,
.sidebar.hide #logoText{

    display:none;
}

/* Posisi icon sidebar */
.sidebar.hide ul li a{

    justify-content:center;
}

/* Bagian atas sidebar */
.top-sidebar{

    display:flex;

    align-items:center;

    gap:12px;

    margin-bottom:30px;
}

/* Tombol hamburger */
.hamburger{

    font-size:24px;

    cursor:pointer;

    background:#1e293b;

    width:42px;

    height:42px;

    display:flex;

    align-items:center;

    justify-content:center;

    border-radius:10px;

    transition:.3s;
}

/* Efek hover hamburger */
.hamburger:hover{

    transform:
    rotate(90deg);

    background:#2563eb;
}

/* Logo sidebar */
.logo{

    font-size:24px;

    font-weight:bold;

    white-space:nowrap;
}

/* Menu sidebar */
.sidebar ul{

    list-style:none;
}

/* Item menu */
.sidebar li{

    margin-bottom:12px;
}

/* Link menu */
.sidebar li a{

    color:white;

    text-decoration:none;

    display:flex;

    align-items:center;

    gap:12px;

    padding:13px 15px;

    border-radius:12px;

    transition:.3s;

    font-size:18px;
}

/* Hover menu */
.sidebar li:hover{

    background:#1e293b;

    transform:translateX(5px);
}

/* Menu aktif */
.active{

    background:#2563eb;
}

/* Card utama */
.card{

    flex:1;

    background:#1230ff;

    padding:35px;

    border-radius:25px;

    min-height:95vh;
}

/* Judul */
h1{

    margin-bottom:10px;
}

/* Paragraf */
p{

    margin-bottom:30px;

    color:#e2e8f0;
}

/* Grid form */
.form-grid{

    display:grid;

    grid-template-columns:
    repeat(2,1fr);

    gap:20px;
}

/* Full column */
.full{

    grid-column:1/-1;
}

/* Input dan select */
input,
select{

    width:100%;

    padding:16px;

    border:none;

    border-radius:14px;

    background:#020617;

    color:white;

    font-size:17px;

    outline:none;

    transition:.3s;
}

/* Efek focus */
input:focus,
select:focus{

    transform:scale(1.02);
}

/* Grup tombol */
.button-group{

    display:flex;

    gap:20px;

    margin-top:25px;

    margin-bottom:30px;
}

/* Tombol */
button{

    flex:1;

    padding:16px;

    border:none;

    border-radius:14px;

    font-size:18px;

    font-weight:bold;

    cursor:pointer;

    transition:.3s;
}

/* Hover tombol */
button:hover{

    transform:
    translateY(-3px);
}

/* Tombol simpan */
.simpan{

    background:#22c55e;

    color:black;
}

/* Tombol reset */
.reset{

    background:#ef4444;

    color:white;
}

/* Search dan sort */
.top-bar{

    display:grid;

    grid-template-columns:
    2fr 1fr;

    gap:20px;

    margin-bottom:25px;
}

/* Box tabel */
.table-box{

    overflow-x:hidden;

    border-radius:20px;
}

/* Tabel */
table{

    width:100%;

    border-collapse:collapse;
}

/* Header tabel */
thead{

    background:#020617;
}

/* Isi tabel */
th,td{

    padding:18px;

    text-align:center;

    border-bottom:
    1px solid rgba(255,255,255,.08);
}

/* Hover baris tabel */
tbody tr{

    transition:.3s;
}

tbody tr:hover{

    background:#1e293b;

    transform:scale(1.01);
}

/* Badge jenis kelamin */
.badge{

    display:inline-block;

    padding:8px 16px;

    border-radius:999px;

    font-size:13px;

    font-weight:bold;

    white-space:nowrap;

    min-width:110px;

    text-align:center;
}

/* Badge laki-laki */
.l{

    background:#2563eb;
}

/* Badge perempuan */
.p{

    background:#db2777;
}

/* Tombol aksi */
.action{

    display:flex;

    justify-content:center;

    gap:10px;
}

/* Tombol edit */
.edit{

    background:#f59e0b;

    color:white;

    padding:10px 16px;

    border:none;

    border-radius:12px;

    cursor:pointer;
}

/* Tombol hapus */
.hapus{

    background:#ef4444;

    color:white;

    padding:10px 16px;

    border:none;

    border-radius:12px;

    cursor:pointer;
}

/* Responsive */
@media(max-width:900px){

    .container{

        flex-direction:column;
    }

    .sidebar{

        width:100%;

        height:auto;

        position:relative;

        top:0;
    }

    .form-grid{

        grid-template-columns:1fr;
    }

    .top-bar{

        grid-template-columns:1fr;
    }

    .full{

        grid-column:auto;
    }
}

</style>
</head>

<body>

<script>

/* Mengecek apakah user sudah login */
if(localStorage.getItem("isLogin")!="true"){

    /* Redirect ke login */
    window.location.href=
    "login.html";
}

/* Mengambil tema dari localStorage */
const theme =
localStorage.getItem("theme");

/* Mengaktifkan light mode */
if(theme=="light"){

    document.body.classList.add(
    "light"
    );
}

</script>

<div class="container">

<!-- Sidebar -->
<div class="sidebar" id="sidebar">

<div class="top-sidebar">

<!-- Tombol sidebar -->
<div class="hamburger"
onclick="toggleSidebar()">
☰
</div>

<!-- Logo -->
<div class="logo" id="logoText">
🎓 MENU
</div>

</div>

<!-- Menu -->
<ul>

<li class="active">
<a href="dashboard.html">
🏠 <span class="menu-text">Dashboard</span>
</a>
</li>

<li>
<a href="mahasiswa.html">
👨‍🎓 <span class="menu-text">Mahasiswa</span>
</a>
</li>

<li>
<a href="statistik.html">
📊 <span class="menu-text">Statistik</span>
</a>
</li>

<li>
<a href="pengaturan.html">
⚙️ <span class="menu-text">Pengaturan</span>
</a>
</li>

<!-- Tombol logout -->
<li onclick="logout()">
<a href="#">
🚪 <span class="menu-text">Logout</span>
</a>
</li>

</ul>

</div>

<!-- Content utama -->
<div class="card">

<h1>
🎓 Dashboard Mahasiswa
</h1>

<p>
Sistem manajemen mahasiswa modern.
</p>

<!-- Form input -->
<div class="form-grid">

<input type="text" id="nim" placeholder="NIM">

<input type="text" id="nama" placeholder="Nama Lengkap">

<input type="text" id="alamat" placeholder="Alamat Lengkap" class="full">

<select id="jk">

<option value="">-- Pilih Jenis Kelamin --</option>
<option value="L">Laki-laki</option>
<option value="P">Perempuan</option>

</select>

<input type="password" id="password" placeholder="Password">

</div>

<!-- Tombol aksi -->
<div class="button-group">

<button class="simpan" onclick="simpanData()">💾 Simpan</button>

<button class="reset" onclick="resetForm()">🔄 Reset</button>

</div>

<!-- Search dan sort -->
<div class="top-bar">

<input type="text" id="search" placeholder="🔍 Cari Nama / NIM">

<select id="sort">

<option value="baru">📌 Data Terbaru</option>
<option value="lama">📂 Data Terlama</option>
<option value="az">🔤 Nama A-Z</option>
<option value="za">🔠 Nama Z-A</option>
<option value="nim_asc">🔢 NIM Kecil → Besar</option>
<option value="nim_desc">🔢 NIM Besar → Kecil</option>

</select>

</div>

<!-- Tabel data -->
<div class="table-box">

<table>

<thead>

<tr>

<th>No</th>
<th>NIM</th>
<th>Nama</th>
<th>Alamat</th>
<th>JK</th>
<th>Aksi</th>

</tr>

</thead>

<!-- Isi tabel -->
<tbody id="tbody"></tbody>

</table>

</div>

</div>

</div>

<script>

/* Mengambil data mahasiswa dari localStorage */
let data =
JSON.parse(localStorage.getItem("mahasiswa")) || [];

/* Penanda edit data */
let editIndex = -1;

/* Menampilkan dan menyembunyikan sidebar */
function toggleSidebar(){

    document.getElementById("sidebar").classList.toggle("hide");
}

/* Menyimpan data */
function simpanData(){

    /* Validasi input */
    if(nim.value=="" || nama.value=="" || alamat.value=="" || jk.value==""){

        alert("Lengkapi semua data!");
        return;
    }

    /* Object data mahasiswa */
    const mahasiswa = {

        nim:nim.value,
        nama:nama.value,
        alamat:alamat.value,
        jk:jk.value,
        password:password.value
    };

    /* Tambah data baru */
    if(editIndex==-1){

        data.push(mahasiswa);

    }else{

        /* Update data */
        data[editIndex]=mahasiswa;
        editIndex=-1;
    }

    /* Simpan ke localStorage */
    localStorage.setItem("mahasiswa", JSON.stringify(data));

    /* Menampilkan ulang tabel */
    render();

    /* Reset form */
    resetForm();
}

/* Menampilkan data ke tabel */
function render(){

    /* Mengambil keyword pencarian */
    const q = search.value.toLowerCase();

    /* Filter data */
    let filtered = data.filter(d =>
        d.nama.toLowerCase().includes(q) ||
        d.nim.toLowerCase().includes(q)
    );

    /* Mengosongkan tabel */
    tbody.innerHTML = "";

    /* Menampilkan data */
    filtered.forEach((m,i)=>{

        tbody.innerHTML += `

        <tr>

        <td>${i+1}</td>
        <td>${m.nim}</td>
        <td>${m.nama}</td>
        <td>${m.alamat}</td>

        <td>
        <span class="badge ${m.jk=='L'?'l':'p'}">
        ${m.jk=='L'?'Laki-laki':'Perempuan'}
        </span>
        </td>

        <td>

        <div class="action">

        <button class="edit" onclick="editData(${i})">✏️ Edit</button>

        <button class="hapus" onclick="hapusData(${i})">🗑 Hapus</button>

        </div>

        </td>

        </tr>

        `;
    });
}

/* Reset form */
function resetForm(){

    nim.value="";
    nama.value="";
    alamat.value="";
    jk.value="";
    password.value="";
}

/* Logout */
function logout(){

    if(confirm("Yakin logout?")){

        localStorage.removeItem("isLogin");

        window.location.href="login.html";
    }
}

/* Edit data */
function editData(i){

    nim.value=data[i].nim;
    nama.value=data[i].nama;
    alamat.value=data[i].alamat;
    jk.value=data[i].jk;
    password.value=data[i].password;

    editIndex=i;
}

/* Hapus data */
function hapusData(i){

    if(confirm("Hapus data?")){

        data.splice(i,1);

        localStorage.setItem("mahasiswa", JSON.stringify(data));

        render();
    }
}

/* Event search */
search.oninput = render;

/* Event sort */
sort.onchange = render;

/* Menampilkan data pertama kali */
render();

</script>

</body>
</html>


#Halaman Mahasiswa 
<!DOCTYPE html> <!-- Menentukan dokumen menggunakan HTML5 -->

<html lang="id"> <!-- Bahasa halaman menggunakan Bahasa Indonesia -->

<head>

<meta charset="UTF-8"> <!-- Agar karakter tampil dengan benar -->

<meta name="viewport" content="width=device-width, initial-scale=1.0">
<!-- Membuat tampilan responsif -->

<title>Data Mahasiswa</title> <!-- Judul halaman -->

<style>

/* Mengatur seluruh elemen */
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

/* Efek scroll halus */
html{
    scroll-behavior:smooth;
}

/* Tampilan utama body */
body{

    font-family:Arial,sans-serif;

    background:
    linear-gradient(135deg,#020617,#0f172a);

    color:white;

    min-height:100vh;

    padding:20px;

    transition:.3s;

    animation:
    fadeBody 1s ease;
}

/* LIGHT MODE */
body.light{

    background:#f1f5f9;

    color:black;
}

/* Card saat light mode */
body.light .card{

    background:white;

    color:black;
}

/* Sidebar saat light mode */
body.light .sidebar{

    background:#e2e8f0;
}

/* Paragraf light mode */
body.light p{

    color:#334155;
}

/* Input light mode */
body.light input{

    background:white;

    color:black;

    border:1px solid #cbd5e1;
}

/* Table light mode */
body.light table{

    background:white;

    color:black;
}

/* Header tabel light mode */
body.light thead{

    background:#cbd5e1;
}

/* Hover tabel light mode */
body.light tbody tr:hover{

    background:#e2e8f0;
}

/* Link sidebar light mode */
body.light .sidebar a{

    color:black;
}

/* Hamburger light mode */
body.light .hamburger{

    background:#cbd5e1;

    color:black;
}

/* Animasi body */
@keyframes fadeBody{

    from{
        opacity:0;
        transform:translateY(15px);
    }

    to{
        opacity:1;
        transform:translateY(0);
    }
}

/* Layout utama */
.container{

    display:flex;

    gap:20px;

    align-items:flex-start;
}

/* Sidebar */
.sidebar{

    width:230px;

    background:#020617;

    border-radius:22px;

    padding:20px;

    height:calc(100vh - 40px);

    position:sticky;

    top:20px;

    overflow:hidden;

    transition:.3s;

    flex-shrink:0;
}

/* Sidebar hide */
.sidebar.hide{

    width:80px;
}

/* Menyembunyikan teks sidebar */
.sidebar.hide .menu-text,
.sidebar.hide #logoText{

    display:none;
}

/* Posisi menu saat hide */
.sidebar.hide ul li a{

    justify-content:center;
}

/* Top sidebar */
.top-sidebar{

    display:flex;

    align-items:center;

    gap:12px;

    margin-bottom:30px;
}

/* Tombol hamburger */
.hamburger{

    font-size:24px;

    cursor:pointer;

    background:#1e293b;

    width:42px;

    height:42px;

    display:flex;

    align-items:center;

    justify-content:center;

    border-radius:10px;

    transition:.3s;
}

/* Hover hamburger */
.hamburger:hover{

    transform:
    rotate(90deg);

    background:#2563eb;
}

/* Logo */
.logo{

    font-size:24px;

    font-weight:bold;

    white-space:nowrap;
}

/* Menu sidebar */
.sidebar ul{

    list-style:none;
}

/* Item menu */
.sidebar li{

    margin-bottom:12px;
}

/* Link menu */
.sidebar li a{

    color:white;

    text-decoration:none;

    display:flex;

    align-items:center;

    gap:12px;

    padding:13px 15px;

    border-radius:12px;

    transition:.3s;

    font-size:18px;
}

/* Hover menu */
.sidebar li:hover{

    background:#1e293b;

    transform:translateX(5px);
}

/* Menu aktif */
.active{

    background:#2563eb;
}

/* Card content */
.card{

    flex:1;

    background:#1230ff;

    padding:35px;

    border-radius:25px;

    min-height:95vh;

    transition:.3s;
}

/* Judul */
h1{

    margin-bottom:10px;
}

/* Paragraf */
p{

    margin-bottom:30px;

    color:#e2e8f0;
}

/* Search box */
.search-box{

    margin-bottom:20px;
}

/* Input search */
.search-box input{

    width:100%;

    padding:15px;

    border:none;

    border-radius:14px;

    background:#020617;

    color:white;

    outline:none;

    font-size:16px;
}

/* Box tabel */
.table-box{

    overflow-x:auto;
}

/* Tabel */
table{

    width:100%;

    border-collapse:collapse;
}

/* Header tabel */
thead{

    background:#020617;
}

/* Isi tabel */
th,td{

    padding:16px;

    text-align:center;

    border-bottom:
    1px solid rgba(255,255,255,.08);
}

/* Hover baris tabel */
tbody tr{

    transition:.3s;
}

tbody tr:hover{

    background:#1e293b;
}

/* Badge jenis kelamin */
.badge{

    display:inline-block;

    padding:8px 16px;

    border-radius:999px;

    font-size:13px;

    font-weight:bold;

    min-width:110px;

    white-space:nowrap;
}

/* Badge laki-laki */
.l{

    background:#2563eb;
}

/* Badge perempuan */
.p{

    background:#db2777;
}

/* Tampilan data kosong */
.empty{

    padding:25px;

    color:#cbd5e1;
}

/* Responsive */
@media(max-width:900px){

    .container{

        flex-direction:column;
    }

    .sidebar{

        width:100%;

        height:auto;

        position:relative;

        top:0;
    }
}

</style>
</head>

<body>

<script>

/* Mengecek apakah user sudah login */
if(localStorage.getItem("isLogin")!="true"){

    /* Redirect ke login */
    window.location.href=
    "login.html";
}

/* Mengambil tema dari localStorage */
const theme =
localStorage.getItem("theme");

/* Mengaktifkan light mode */
if(theme=="light"){

    document.body.classList.add(
    "light"
    );
}

</script>

<div class="container">

<!-- Sidebar -->
<div class="sidebar" id="sidebar">

<div class="top-sidebar">

<!-- Tombol sidebar -->
<div class="hamburger"
onclick="toggleSidebar()">
☰
</div>

<!-- Logo -->
<div class="logo" id="logoText">
🎓 MENU
</div>

</div>

<!-- Menu -->
<ul>

<li>
<a href="dashboard.html">
🏠 <span class="menu-text">Dashboard</span>
</a>
</li>

<li class="active">
<a href="mahasiswa.html">
👨‍🎓 <span class="menu-text">Mahasiswa</span>
</a>
</li>

<li>
<a href="statistik.html">
📊 <span class="menu-text">Statistik</span>
</a>
</li>

<li>
<a href="pengaturan.html">
⚙️ <span class="menu-text">Pengaturan</span>
</a>
</li>

<!-- Tombol logout -->
<li onclick="logout()">
<a href="#">
🚪 <span class="menu-text">Logout</span>
</a>
</li>

</ul>

</div>

<!-- Content -->
<div class="card">

<h1>
👨‍🎓 Data Mahasiswa
</h1>

<p>
Semua data mahasiswa tersimpan akan tampil di sini.
</p>

<!-- Search -->
<div class="search-box">

<input
type="text"
id="search"
placeholder="🔍 Cari Nama atau NIM"
>

</div>

<!-- Tabel -->
<div class="table-box">

<table>

<thead>

<tr>

<th>No</th>
<th>NIM</th>
<th>Nama</th>
<th>Alamat</th>
<th>JK</th>

</tr>

</thead>

<!-- Isi tabel -->
<tbody id="tbody"></tbody>

</table>

</div>

</div>

</div>

<script>

/* Mengambil data mahasiswa dari localStorage */
let data =
JSON.parse(
localStorage.getItem("mahasiswa")
) || [];

/* Toggle sidebar */
function toggleSidebar(){

    document
    .getElementById("sidebar")
    .classList
    .toggle("hide");
}

/* Menampilkan data */
function render(){

    /* Mengambil keyword pencarian */
    const q =
    search.value.toLowerCase();

    /* Filter data */
    const filtered =
    data.filter(d=>

        d.nama.toLowerCase().includes(q)
        ||
        d.nim.toLowerCase().includes(q)
    );

    /* Mengosongkan tabel */
    tbody.innerHTML = "";

    /* Jika data kosong */
    if(filtered.length==0){

        tbody.innerHTML = `

        <tr>

        <td colspan="5" class="empty">

        Data mahasiswa tidak ditemukan

        </td>

        </tr>
        `;

        return;
    }

    /* Menampilkan data */
    filtered.forEach((m,i)=>{

        tbody.innerHTML += `

        <tr>

        <td>${i+1}</td>

        <td>${m.nim}</td>

        <td>${m.nama}</td>

        <td>${m.alamat}</td>

        <td>

        <span class="
        badge
        ${m.jk=="L"?"l":"p"}
        ">

        ${m.jk=="L"
        ?"Laki-laki"
        :"Perempuan"}

        </span>

        </td>

        </tr>
        `;
    });
}

/* Event search */
search.oninput = render;

/* Logout */
function logout(){

    if(confirm(
    "Yakin ingin logout?"
    )){

        /* Menghapus status login */
        localStorage.removeItem(
        "isLogin"
        );

        /* Redirect ke login */
        window.location.href=
        "login.html";
    }
}

/* Menampilkan data pertama kali */
render();

</script>

</body>
</html>


#Halaman Pengaturan
<!DOCTYPE html> <!-- Menentukan dokumen menggunakan HTML5 -->

<html lang="id"> <!-- Bahasa halaman menggunakan Bahasa Indonesia -->

<head>

<meta charset="UTF-8"> <!-- Agar karakter tampil dengan benar -->

<meta name="viewport" content="width=device-width, initial-scale=1.0">
<!-- Membuat tampilan responsif -->

<title>Pengaturan Admin</title> <!-- Judul halaman -->

<style>

/* Mengatur seluruh elemen */
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

/* Root warna utama */
:root{

    --bg:#0f172a;
    --card:#1230ff;
    --sidebar:#020617;
    --text:white;
    --box:#020617;
}

/* Light mode */
.light{

    --bg:#f1f5f9;
    --card:white;
    --sidebar:#dbeafe;
    --text:#0f172a;
    --box:#e2e8f0;
}

/* Tampilan body */
body{

    font-family:Poppins,Arial,sans-serif;

    background:
    linear-gradient(
    135deg,
    var(--bg),
    #1e293b
    );

    color:var(--text);

    min-height:100vh;

    padding:20px;

    transition:.3s;
}

/* Tombol hamburger */
.hamburger{

    position:fixed;

    top:20px;

    left:20px;

    width:50px;

    height:50px;

    background:var(--sidebar);

    border-radius:12px;

    display:flex;

    justify-content:center;

    align-items:center;

    cursor:pointer;

    z-index:1000;

    font-size:24px;

    box-shadow:
    0 0 15px rgba(0,0,0,.4);
}

/* Layout utama */
.container{

    display:flex;

    gap:20px;
}

/* Sidebar */
.sidebar{

    width:260px;

    background:var(--sidebar);

    border-radius:25px;

    padding:25px;

    min-height:95vh;

    transition:.3s;
}

/* Sidebar disembunyikan */
.sidebar.hide{

    margin-left:-280px;
}

/* Logo */
.logo{

    text-align:center;

    font-size:30px;

    font-weight:bold;

    margin-bottom:40px;
}

/* Menu sidebar */
.sidebar ul{

    list-style:none;
}

/* Item menu */
.sidebar li{

    padding:16px;

    margin-bottom:12px;

    border-radius:14px;

    cursor:pointer;

    transition:.3s;
}

/* Hover menu */
.sidebar li:hover{

    background:#2563eb;
}

/* Link sidebar */
.sidebar a{

    color:var(--text);

    text-decoration:none;

    display:block;
}

/* Menu aktif */
.active{

    background:#2563eb;
}

/* Card content */
.card{

    flex:1;

    background:var(--card);

    padding:35px;

    border-radius:25px;

    transition:.3s;
}

/* Card full */
.card.full{

    width:100%;
}

/* Judul */
h1{

    margin-bottom:10px;
}

/* Paragraf */
p{

    margin-bottom:25px;
}

/* Box pengaturan */
.setting-box{

    background:var(--box);

    padding:25px;

    border-radius:20px;

    margin-bottom:20px;
}

/* Judul box */
.setting-box h2{

    margin-bottom:15px;
}

/* Tombol */
button{

    padding:15px 20px;

    border:none;

    border-radius:14px;

    cursor:pointer;

    font-weight:bold;

    transition:.3s;
}

/* Hover tombol */
button:hover{

    transform:scale(1.03);
}

/* Tombol mode */
.mode-btn{

    background:#f59e0b;

    color:white;
}

/* Tombol hapus */
.delete{

    background:#ef4444;

    color:white;
}

/* Tombol logout */
.logout{

    background:#2563eb;

    color:white;
}

/* Notifikasi toast */
.toast{

    position:fixed;

    top:20px;

    right:20px;

    background:#22c55e;

    color:white;

    padding:16px 22px;

    border-radius:14px;

    font-weight:bold;

    opacity:0;

    transform:translateY(-20px);

    transition:.4s;

    z-index:9999;
}

/* Toast aktif */
.toast.show{

    opacity:1;

    transform:translateY(0);
}

/* Responsive */
@media(max-width:900px){

    .container{
        flex-direction:column;
    }

    .sidebar{
        width:100%;
        min-height:auto;
    }
}

</style>
</head>

<body>

<!-- Mengambil mode tema -->
<script>

const mode =
localStorage.getItem("theme");

/* Mengaktifkan light mode */
if(mode=="light"){

    document.body.classList.add(
    "light"
    );
}

/* Mengecek login */
if(localStorage.getItem("isLogin")!="true"){

    window.location.href=
    "login.html";
}

</script>

<!-- Notifikasi -->
<div class="toast" id="toast">
✅ Berhasil
</div>

<!-- Tombol sidebar -->
<div
class="hamburger"
onclick="toggleSidebar()"
>
☰
</div>

<div class="container">

<!-- Sidebar -->
<div
class="sidebar"
id="sidebar"
>

<div class="logo">
🎓 ADMIN
</div>

<ul>

<li>
<a href="dashboard.html">
🏠 Dashboard
</a>
</li>

<li>
<a href="mahasiswa.html">
👨‍🎓 Mahasiswa
</a>
</li>

<li>
<a href="statistik.html">
📊 Statistik
</a>
</li>

<li class="active">
<a href="pengaturan.html">
⚙️ Pengaturan
</a>
</li>

<!-- Logout -->
<li onclick="logout()">
🚪 Logout
</li>

</ul>

</div>

<!-- Content -->
<div
class="card"
id="card"
>

<h1>
⚙️ Pengaturan Admin
</h1>

<p>
Kelola sistem dashboard mahasiswa modern.
</p>

<!-- Pengaturan mode -->
<div class="setting-box">

<h2>
🌙 Dark / ☀️ Light Mode
</h2>

<p>
Ubah tampilan dashboard menjadi terang atau gelap.
</p>

<button
class="mode-btn"
onclick="toggleMode()"
>
🌙 / ☀️ Ubah Mode
</button>

</div>

<!-- Hapus data -->
<div class="setting-box">

<h2>
🗑️ Hapus Semua Data
</h2>

<p>
Semua data mahasiswa akan dihapus permanen.
</p>

<button
class="delete"
onclick="hapusSemuaData()"
>
🗑️ Hapus Semua
</button>

</div>

<!-- Logout -->
<div class="setting-box">

<h2>
🚪 Logout Sistem
</h2>

<p>
Keluar dari dashboard admin.
</p>

<button
class="logout"
onclick="logout()"
>
🚪 Logout
</button>

</div>

</div>

</div>

<script>

/* Toggle sidebar */
function toggleSidebar(){

    sidebar.classList.toggle(
    "hide"
    );

    card.classList.toggle(
    "full"
    );
}

/* Mengubah mode tema */
function toggleMode(){

    document.body.classList.toggle(
    "light"
    );

    /* Jika light mode aktif */
    if(
        document.body.classList.contains(
        "light"
        )
    ){

        localStorage.setItem(
        "theme",
        "light"
        );

        showToast(
        "Light mode aktif"
        );

    }else{

        /* Menyimpan dark mode */
        localStorage.setItem(
        "theme",
        "dark"
        );

        showToast(
        "Dark mode aktif"
        );
    }
}

/* Menghapus semua data */
function hapusSemuaData(){

    if(confirm(
    "Yakin ingin menghapus semua data?"
    )){

        localStorage.removeItem(
        "mahasiswa"
        );

        showToast(
        "Semua data berhasil dihapus"
        );
    }
}

/* Logout */
function logout(){

    if(confirm(
    "Yakin ingin logout?"
    )){

        /* Menghapus status login */
        localStorage.removeItem(
        "isLogin"
        );

        /* Redirect login */
        window.location.href=
        "login.html";
    }
}

/* Menampilkan notifikasi */
function showToast(text){

    toast.innerHTML =
    "✅ " + text;

    toast.classList.add(
    "show"
    );

    /* Menghilangkan toast */
    setTimeout(()=>{

        toast.classList.remove(
        "show"
        );

    },3000);
}

/* Notifikasi awal */
showToast(
"Pengaturan berhasil dimuat"
);

</script>

</body>
</html>


#Halaman Statistik
<!DOCTYPE html> <!-- Menentukan dokumen menggunakan HTML5 -->

<html lang="id"> <!-- Bahasa halaman menggunakan Bahasa Indonesia -->

<head>

<meta charset="UTF-8"> <!-- Agar karakter tampil dengan benar -->

<meta name="viewport" content="width=device-width, initial-scale=1.0">
<!-- Membuat tampilan responsif -->

<title>Statistik Mahasiswa</title> <!-- Judul halaman -->

<!-- Library Chart.js untuk membuat grafik -->
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<!-- Library XLSX untuk export Excel -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js"></script>

<!-- Library jsPDF untuk export PDF -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>

<style>

/* Mengatur seluruh elemen */
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

/* Root warna utama */
:root{

    --bg:#0f172a;
    --card:#1230ff;
    --sidebar:#020617;
    --text:white;
    --box:#020617;
}

/* Light mode */
body.light{

    --bg:#f1f5f9;
    --card:white;
    --sidebar:#dbeafe;
    --text:#0f172a;
    --box:#e2e8f0;
}

/* Tampilan body */
body{

    font-family:Poppins,Arial,sans-serif;

    background:
    linear-gradient(
    135deg,
    var(--bg),
    #1e293b
    );

    color:var(--text);

    min-height:100vh;

    padding:20px;

    transition:.3s;
}

/* Tombol hamburger */
.hamburger{

    position:fixed;

    top:20px;

    left:20px;

    width:50px;

    height:50px;

    background:var(--sidebar);

    border-radius:12px;

    display:flex;

    justify-content:center;

    align-items:center;

    cursor:pointer;

    z-index:1000;

    font-size:25px;

    color:white;
}

/* Layout utama */
.container{

    display:flex;

    gap:20px;

    align-items:flex-start;
}

/* Sidebar */
.sidebar{

    width:230px;

    background:var(--sidebar);

    border-radius:25px;

    padding:20px;

    height:calc(100vh - 40px);

    position:sticky;

    top:20px;

    overflow:hidden;

    flex-shrink:0;

    transition:.3s;
}

/* Sidebar disembunyikan */
.sidebar.hide{

    width:0;

    padding:0;

    opacity:0;
}

/* Logo */
.logo{

    text-align:center;

    font-size:30px;

    font-weight:bold;

    margin-top:40px;

    margin-bottom:40px;
}

/* Menu sidebar */
.sidebar ul{

    list-style:none;
}

/* Item menu */
.sidebar li{

    margin-bottom:15px;
}

/* Link sidebar */
.sidebar a{

    display:block;

    padding:15px;

    border-radius:14px;

    color:white;

    text-decoration:none;

    transition:.3s;
}

/* Hover menu */
.sidebar a:hover{

    background:#2563eb;
}

/* Menu aktif */
.active{

    background:#2563eb;
}

/* Card utama */
.card{

    flex:1;

    background:var(--card);

    border-radius:25px;

    padding:30px;

    min-height:100vh;
}

/* Bagian atas */
.top h1{

    font-size:40px;

    margin-bottom:10px;
}

/* Paragraf */
.top p{

    font-size:18px;
}

/* Box statistik */
.stats{

    display:grid;

    grid-template-columns:
    repeat(3,1fr);

    gap:18px;

    margin-top:25px;
}

/* Card statistik */
.box{

    background:var(--box);

    padding:25px;

    border-radius:18px;

    text-align:center;
}

/* Angka statistik */
.box h2{

    font-size:45px;

    margin-bottom:8px;
}

/* Text statistik */
.box p{

    font-size:17px;
}

/* Box chart */
.chart-box{

    margin-top:30px;

    background:var(--box);

    padding:22px;

    border-radius:20px;
}

/* Judul chart */
.chart-box h2{

    text-align:center;

    margin-bottom:20px;
}

/* Container pie chart */
.pie-container{

    width:100%;

    max-width:320px;

    height:320px;

    margin:20px auto;
}

/* Container bar chart */
.bar-container{

    width:100%;

    max-width:700px;

    height:320px;

    margin:20px auto;
}

/* Canvas chart */
canvas{

    background:white;

    border-radius:14px;

    padding:10px;
}

/* Tombol export */
.export{

    display:flex;

    gap:15px;

    margin-top:30px;

    flex-wrap:wrap;
}

/* Tombol */
.export button{

    border:none;

    padding:14px 22px;

    border-radius:14px;

    font-weight:bold;

    cursor:pointer;

    transition:.3s;
}

/* Hover tombol */
.export button:hover{

    transform:scale(1.05);
}

/* Tombol Excel */
.excel{

    background:#22c55e;

    color:black;
}

/* Tombol PDF */
.pdf{

    background:#ef4444;

    color:white;
}

/* Notifikasi */
.notif{

    margin-top:25px;

    background:#22c55e;

    color:black;

    padding:15px;

    border-radius:14px;

    font-weight:bold;

    display:none;
}

/* Responsive */
@media(max-width:900px){

    .container{

        flex-direction:column;
    }

    .sidebar{

        position:relative;

        width:100%;

        height:auto;
    }

    .stats{

        grid-template-columns:1fr;
    }

    .pie-container{

        max-width:260px;

        height:260px;
    }

    .bar-container{

        height:260px;
    }
}

</style>
</head>

<body>

<script>

/* Mengambil tema dari localStorage */
const theme =
localStorage.getItem("theme");

/* Mengaktifkan light mode */
if(theme=="light"){

    document.body.classList.add(
    "light"
    );
}

/* Mengecek login */
if(localStorage.getItem("isLogin")!="true"){

    window.location.href=
    "./login.html";
}

</script>

<!-- Tombol sidebar -->
<div
class="hamburger"
onclick="toggleSidebar()"
>
☰
</div>

<div class="container">

<!-- Sidebar -->
<div
class="sidebar"
id="sidebar"
>

<div class="logo">
🎓 ADMIN
</div>

<ul>

<li>
<a href="dashboard.html">
🏠 Dashboard
</a>
</li>

<li>
<a href="mahasiswa.html">
👨‍🎓 Mahasiswa
</a>
</li>

<li>
<a
href="statistik.html"
class="active"
>
📊 Statistik
</a>
</li>

<li>
<a href="pengaturan.html">
⚙️ Pengaturan
</a>
</li>

<li>
<a
href="#"
onclick="logout()"
>
🚪 Logout
</a>
</li>

</ul>

</div>

<!-- Content -->
<div class="card">

<div class="top">

<h1>
📊 Statistik Mahasiswa
</h1>

<p>
Dashboard statistik modern dengan grafik interaktif
</p>

</div>

<!-- Statistik -->
<div class="stats">

<div class="box">

<h2 id="total">
0
</h2>

<p>
Total Mahasiswa
</p>

</div>

<div class="box">

<h2 id="lk">
0
</h2>

<p>
Laki-laki
</p>

</div>

<div class="box">

<h2 id="pr">
0
</h2>

<p>
Perempuan
</p>

</div>

</div>

<!-- Pie chart -->
<div class="chart-box">

<h2>
📈 Pie Chart Jenis Kelamin
</h2>

<div class="pie-container">

<canvas id="pieChart"></canvas>

</div>

</div>

<!-- Bar chart -->
<div class="chart-box">

<h2>
📊 Bar Chart Mahasiswa
</h2>

<div class="bar-container">

<canvas id="barChart"></canvas>

</div>

</div>

<!-- Tombol export -->
<div class="export">

<button
class="excel"
onclick="exportExcel()"
>

📗 Export Excel

</button>

<button
class="pdf"
onclick="exportPDF()"
>

📕 Export PDF

</button>

</div>

<!-- Notifikasi -->
<div
class="notif"
id="notif"
>

✅ Export berhasil

</div>

</div>

</div>

<script>

/* Mengambil data mahasiswa */
let data =
JSON.parse(
localStorage.getItem("mahasiswa")
) || [];

/* Menghitung total mahasiswa */
let total =
data.length;

/* Menghitung laki-laki */
let laki =
data.filter(
d=>d.jk=="L"
).length;

/* Menghitung perempuan */
let perempuan =
data.filter(
d=>d.jk=="P"
).length;

/* Menampilkan total mahasiswa */
document.getElementById(
"total"
).innerText = total;

/* Menampilkan total laki-laki */
document.getElementById(
"lk"
).innerText = laki;

/* Menampilkan total perempuan */
document.getElementById(
"pr"
).innerText = perempuan;

/* Membuat pie chart */
new Chart(

document.getElementById(
"pieChart"
),

{

type:"pie",

data:{

labels:[
"Laki-laki",
"Perempuan"
],

datasets:[{

data:[
laki,
perempuan
],

backgroundColor:[
"#2563eb",
"#db2777"
]

}]
},

options:{

responsive:true,

maintainAspectRatio:false

}

});

/* Membuat bar chart */
new Chart(

document.getElementById(
"barChart"
),

{

type:"bar",

data:{

labels:[
"Total",
"Laki-laki",
"Perempuan"
],

datasets:[{

label:"Jumlah Mahasiswa",

data:[
total,
laki,
perempuan
],

backgroundColor:[
"#22c55e",
"#2563eb",
"#db2777"
],

borderRadius:10

}]
},

options:{

responsive:true,

maintainAspectRatio:false

}

});

/* Toggle sidebar */
function toggleSidebar(){

document
.getElementById("sidebar")
.classList.toggle("hide");
}

/* Logout */
function logout(){

if(confirm("Yakin logout?")){

localStorage.removeItem(
"isLogin"
);

window.location.href=
"./login.html";
}
}

/* Menampilkan notifikasi */
function showNotif(text){

let notif =
document.getElementById(
"notif"
);

notif.innerHTML = text;

notif.style.display = "block";

/* Menghilangkan notifikasi */
setTimeout(()=>{

notif.style.display = "none";

},2500);
}

/* Export Excel */
function exportExcel(){

/* Jika data kosong */
if(data.length==0){

alert("Data kosong!");

return;
}

/* Membuat sheet Excel */
const ws =
XLSX.utils.json_to_sheet(
data
);

/* Membuat workbook */
const wb =
XLSX.utils.book_new();

/* Menambahkan sheet */
XLSX.utils.book_append_sheet(
wb,
ws,
"Mahasiswa"
);

/* Download file Excel */
XLSX.writeFile(
wb,
"data_mahasiswa.xlsx"
);

/* Menampilkan notifikasi */
showNotif(
"✅ Export Excel berhasil"
);

}

/* Export PDF */
async function exportPDF(){

/* Mengambil jsPDF */
const { jsPDF } =
window.jspdf;

/* Membuat file PDF */
const pdf =
new jsPDF();

/* Menambahkan text PDF */
pdf.text(
"Data Statistik Mahasiswa",
20,
20
);

pdf.text(
"Total Mahasiswa : "+total,
20,
40
);

pdf.text(
"Laki-laki : "+laki,
20,
55
);

pdf.text(
"Perempuan : "+perempuan,
20,
70
);

/* Download PDF */
pdf.save(
"statistik_mahasiswa.pdf"
);

/* Menampilkan notifikasi */
showNotif(
"✅ Export PDF berhasil"
);

}

</script>

</body>
</html>



# Dokumentasi UTS Pemrograman Web

## Halaman Login

![Login](dokumentasi%20UTS/Login.png)

Halaman login digunakan untuk masuk ke sistem dashboard admin menggunakan username dan password.

---

## Halaman Dashboard

![Dashboard](dokumentasi%20UTS/Dashboard.png)

Halaman dashboard digunakan untuk mengelola data mahasiswa seperti menambah, mengedit, dan menghapus data.

---

## Halaman Data Mahasiswa

![Mahasiswa](dokumentasi%20UTS/Mahasiswa.png)

Halaman mahasiswa digunakan untuk menampilkan seluruh data mahasiswa yang tersimpan.

---

## Halaman Statistik

![Statistik](dokumentasi%20UTS/Statistik.png)

Halaman statistik digunakan untuk menampilkan grafik dan jumlah data mahasiswa.

---

## Halaman Logout

![Logout](dokumentasi%20UTS/PengaturandanLogout.png)

Halaman logout digunakan untuk keluar dari sistem dashboard admin.

