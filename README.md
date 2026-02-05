<!DOCTYPE html>
<html lang="cs">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Ne pro každého</title>

<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;500;700&display=swap" rel="stylesheet">

<style>
:root {
  --bg-dark: #0b0b0b;
  --glass: rgba(255,255,255,0.08);
  --border: rgba(255,255,255,0.15);
  --text-dim: rgba(255,255,255,0.7);
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  scroll-behavior: smooth;
}

body {
  font-family: 'Inter', sans-serif;
  background: radial-gradient(circle at top, #1a1a1a, #000);
  color: white;
  overflow-x: hidden;
}

/* BACKGROUND ANIMATION */
.bg {
  position: fixed;
  inset: 0;
  background:
    linear-gradient(120deg, #111, #000, #111),
    radial-gradient(circle at 20% 30%, #222, transparent 40%),
    radial-gradient(circle at 80% 70%, #333, transparent 40%);
  animation: bgMove 20s infinite linear;
  z-index: -2;
}

@keyframes bgMove {
  0% { filter: hue-rotate(0deg); }
  100% { filter: hue-rotate(360deg); }
}

/* GRAIN */
.bg::after {
  content: "";
  position: absolute;
  inset: 0;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.8' numOctaves='4'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.05'/%3E%3C/svg%3E");
  pointer-events: none;
}

/* SECTIONS */
section, header {
  padding: 8rem 10%;
  position: relative;
}

.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
}

.hero h1 {
  font-size: clamp(3rem, 6vw, 5rem);
  font-weight: 700;
  line-height: 1.1;
}

.hero h1 span {
  font-weight: 300;
  opacity: 0.7;
}

.hero p {
  margin: 2rem 0;
  max-width: 620px;
  color: var(--text-dim);
}

/* BUTTON */
.btn {
  display: inline-block;
  padding: 1rem 2.2rem;
  border: 1px solid white;
  text-decoration: none;
  color: white;
  transition: all .4s ease;
  backdrop-filter: blur(10px);
}

.btn:hover {
  background: white;
  color: black;
  transform: translateY(-2px);
}

/* GLASS BLOCK */
.glass {
  background: var(--glass);
  backdrop-filter: blur(20px);
  border: 1px solid var(--border);
  border-radius: 18px;
  padding: 4rem;
}

/* TEXT */
h2 {
  font-size: 2.4rem;
  margin-bottom: 1rem;
}

ul {
  list-style: none;
  margin-top: 2rem;
}

ul li {
  margin-bottom: 0.8rem;
}

blockquote {
  margin-top: 2rem;
  font-style: italic;
  opacity: 0.6;
}

/* PRODUCTS */
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  gap: 2rem;
  margin-top: 3rem;
}

.card {
  padding: 3rem;
  border-radius: 20px;
  background: var(--glass);
  backdrop-filter: blur(25px);
  border: 1px solid var(--border);
  transition: transform .4s ease, box-shadow .4s ease;
}

.card:hover {
  transform: translateY(-10px);
  box-shadow: 0 30px 60px rgba(0,0,0,0.5);
}

/* CTA */
.cta {
  text-align: center;
}

/* FOOTER */
footer {
  padding: 3rem 10%;
  border-top: 1px solid var(--border);
  opacity: 0.6;
}

/* SCROLL ANIMATION */
.reveal {
  opacity: 0;
  transform: translateY(60px);
  transition: all 1s cubic-bezier(.2,.7,0,1);
}

.reveal.active {
  opacity: 1;
  transform: translateY(0);
}

@media(max-width:768px){
  section, header {
    padding: 5rem 7%;
  }
}
</style>
</head>

<body>

<div class="bg"></div>

<header class="hero">
  <div class="reveal">
    <h1>Ne pro každého.<br><span>A právě proto funguje.</span></h1>
    <p>Produkty pro lidi, kteří mají vkus, názor a odmítají průměr.</p>
    <a href="#produkty" class="btn">Objevit kolekci</a>
  </div>
</header>

<section class="reveal">
  <div class="glass">
    <h2>Většina věcí dnes vypadá stejně.</h2>
    <p>Generický design. Nulová osobnost. Tohle je reakce na průměr.</p>
  </div>
</section>

<section class="reveal">
  <div class="glass">
    <h2>My to děláme jinak.</h2>
    <ul>
      <li>Žádná výroba bez myšlenky</li>
      <li>Žádné kompromisy v kvalitě</li>
      <li>Žádné produkty pro všechny</li>
    </ul>
    <blockquote>Dobrý design má vyvolat reakci. Ne souhlas.</blockquote>
  </div>
</section>

<section id="produkty" class="reveal">
  <h2>Vybrané kousky</h2>
  <div class="grid">
    <div class="card">Produkt 01</div>
    <div class="card">Produkt 02</div>
    <div class="card">Produkt 03</div>
  </div>
</section>

<section class="cta reveal">
  <h2>Buď součástí.<br>Nebo zůstaň u průměru.</h2>
  <a href="#" class="btn">Chci to vidět</a>
</section>

<footer>
  © 2026 — Ne pro každého
</footer>

<script>
const reveals = document.querySelectorAll('.reveal');

const observer = new IntersectionObserver(entries => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('active');
    }
  });
},{threshold:0.15});

reveals.forEach(el => observer.observe(el));
</script>

</body>
</html>
terab toto
