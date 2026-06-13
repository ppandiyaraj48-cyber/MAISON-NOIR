<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>MAISON NOIR — Private Collection</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;1,400&family=Inter:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root{
    --black:#0A0908;
    --ivory:#F5F0E8;
    --gold:#C9A876;
    --burgundy:#3D1F1F;
    --charcoal:#1C1A18;
  }
  *{margin:0;padding:0;box-sizing:border-box;}
  html{scroll-behavior:smooth;}
  body{
    background:var(--black);
    color:var(--ivory);
    font-family:'Inter',sans-serif;
    font-weight:300;
    overflow-x:hidden;
  }
  ::selection{background:var(--gold);color:var(--black);}

  /* ===== ACCESS GATE ===== */
  #gate{
    position:fixed; inset:0; background:var(--black);
    display:flex; align-items:center; justify-content:center;
    flex-direction:column; z-index:9999;
    transition:opacity 1.2s ease, visibility 1.2s ease;
  }
  #gate.hidden{opacity:0; visibility:hidden;}
  .gate-mark{
    font-family:'Cormorant Garamond',serif;
    font-size:clamp(2.5rem,8vw,5rem);
    letter-spacing:0.35em;
    font-weight:300;
    margin-bottom:1.5rem;
    opacity:0;
    animation:fadeIn 1.5s ease forwards 0.3s;
  }
  .gate-line{
    width:0; height:1px; background:var(--gold);
    animation:lineGrow 1.8s ease forwards 1s;
    margin-bottom:2rem;
  }
  @keyframes lineGrow{ to{ width:160px; } }
  .gate-sub{
    font-size:0.75rem; letter-spacing:0.3em; text-transform:uppercase;
    color:var(--gold); opacity:0;
    animation:fadeIn 1.5s ease forwards 1.8s;
    margin-bottom:3rem;
  }
  .gate-btn{
    opacity:0; animation:fadeIn 1.5s ease forwards 2.4s;
    background:transparent; border:1px solid var(--gold);
    color:var(--ivory); padding:1rem 3rem; font-family:'Inter',sans-serif;
    font-size:0.7rem; letter-spacing:0.25em; text-transform:uppercase;
    cursor:pointer; transition:all 0.4s ease;
  }
  .gate-btn:hover{ background:var(--gold); color:var(--black); }
  @keyframes fadeIn{ to{ opacity:1; } }

  /* ===== NAV ===== */
  header{
    position:fixed; top:0; left:0; right:0; z-index:100;
    display:flex; justify-content:space-between; align-items:center;
    padding:1.8rem 4vw; mix-blend-mode:difference;
    transition:padding 0.4s ease;
  }
  .logo{
    font-family:'Cormorant Garamond',serif; font-size:1.4rem;
    letter-spacing:0.3em; font-weight:400;
  }
  nav a{
    color:var(--ivory); text-decoration:none; font-size:0.7rem;
    letter-spacing:0.2em; text-transform:uppercase; margin-left:2.5rem;
    transition:color 0.3s ease; position:relative;
  }
  nav{display:flex; align-items:center;}
  nav a::after{
    content:''; position:absolute; left:0; bottom:-6px; width:0; height:1px;
    background:var(--gold); transition:width 0.3s ease;
  }
  nav a:hover::after{ width:100%; }
  .nav-toggle{display:none;}

  /* ===== HERO ===== */
  .hero{
    height:100vh; display:flex; flex-direction:column;
    justify-content:center; align-items:center; text-align:center;
    position:relative; padding:0 1.5rem;
    background:radial-gradient(ellipse at center, var(--charcoal) 0%, var(--black) 70%);
  }
  .hero-eyebrow{
    font-size:0.7rem; letter-spacing:0.4em; text-transform:uppercase;
    color:var(--gold); margin-bottom:1.5rem;
    opacity:0; animation:riseIn 1.2s ease forwards 0.4s;
  }
  .hero h1{
    font-family:'Cormorant Garamond',serif;
    font-weight:300; font-style:italic;
    font-size:clamp(3rem,11vw,8rem); line-height:1.05;
    opacity:0; animation:riseIn 1.2s ease forwards 0.7s;
  }
  .hero h1 span{ display:block; font-style:normal; font-weight:300; letter-spacing:0.05em; }
  .hero-sub{
    margin-top:2rem; max-width:480px; font-size:0.95rem;
    line-height:1.9; color:#B8B0A4;
    opacity:0; animation:riseIn 1.2s ease forwards 1s;
  }
  .hero-cta{
    margin-top:2.5rem; opacity:0; animation:riseIn 1.2s ease forwards 1.3s;
  }
  @keyframes riseIn{ from{opacity:0; transform:translateY(30px);} to{opacity:1; transform:translateY(0);} }
  .btn-primary{
    background:var(--gold); color:var(--black); border:none;
    padding:1.1rem 3.2rem; font-size:0.7rem; letter-spacing:0.25em;
    text-transform:uppercase; cursor:pointer; transition:all 0.4s ease;
    text-decoration:none; display:inline-block;
  }
  .btn-primary:hover{ background:var(--ivory); letter-spacing:0.35em; }
  .scroll-cue{
    position:absolute; bottom:2.5rem; left:50%; transform:translateX(-50%);
    font-size:0.65rem; letter-spacing:0.3em; text-transform:uppercase;
    color:#6f6a62; opacity:0; animation:riseIn 1.2s ease forwards 1.6s;
  }
  .scroll-cue::after{
    content:''; display:block; width:1px; height:40px; background:var(--gold);
    margin:0.8rem auto 0; animation:scrollLine 2s ease-in-out infinite;
  }
  @keyframes scrollLine{ 0%,100%{transform:scaleY(0.4); opacity:0.3;} 50%{transform:scaleY(1); opacity:1;} }

  /* ===== SECTION SHARED ===== */
  section{ padding:8rem 6vw; }
  .section-head{ text-align:center; margin-bottom:5rem; }
  .eyebrow{
    font-size:0.7rem; letter-spacing:0.4em; text-transform:uppercase;
    color:var(--gold); margin-bottom:1rem; display:block;
  }
  .section-head h2{
    font-family:'Cormorant Garamond',serif; font-weight:300;
    font-size:clamp(2.2rem,5vw,3.8rem); font-style:italic;
  }

  /* ===== COLLECTION GRID ===== */
  .collection{
    display:grid; grid-template-columns:repeat(3,1fr); gap:2px;
    background:var(--gold);
  }
  .piece{
    background:var(--charcoal); aspect-ratio:3/4; position:relative;
    overflow:hidden; display:flex; align-items:flex-end; padding:2rem;
    cursor:pointer; transition:transform 0.6s ease;
  }
  .piece::before{
    content:''; position:absolute; inset:0;
    background:linear-gradient(160deg, var(--burgundy), var(--black) 70%);
    opacity:0.6; transition:opacity 0.6s ease;
  }
  .piece:hover{ transform:scale(1.02); z-index:2; }
  .piece:hover::before{ opacity:0.85; }
  .piece-info{ position:relative; z-index:1; }
  .piece-num{ font-size:0.7rem; letter-spacing:0.2em; color:var(--gold); }
  .piece-name{
    font-family:'Cormorant Garamond',serif; font-style:italic;
    font-size:1.6rem; margin-top:0.4rem;
  }
  .piece-price{ font-size:0.8rem; letter-spacing:0.1em; color:#B8B0A4; margin-top:0.6rem; }

  /* ===== MANIFESTO ===== */
  .manifesto{
    display:grid; grid-template-columns:1fr 1fr; gap:5rem; align-items:center;
  }
  .manifesto-visual{
    aspect-ratio:4/5; background:linear-gradient(135deg,var(--charcoal),var(--burgundy));
    position:relative; overflow:hidden;
  }
  .manifesto-visual::after{
    content:'MN'; position:absolute; inset:0; display:flex; align-items:center;
    justify-content:center; font-family:'Cormorant Garamond',serif;
    font-size:12rem; font-weight:300; color:rgba(245,240,232,0.05); letter-spacing:0;
  }
  .manifesto-text p{
    font-size:1.05rem; line-height:2; color:#C9C2B6; margin-bottom:1.5rem;
  }
  .manifesto-text p:first-of-type{
    font-family:'Cormorant Garamond',serif; font-size:1.8rem;
    font-style:italic; line-height:1.6; color:var(--ivory); margin-bottom:2rem;
  }

  /* ===== MEMBERSHIP TIERS ===== */
  .tiers{ display:grid; grid-template-columns:repeat(3,1fr); gap:0; border:1px solid #333; }
  .tier{
    padding:3.5rem 2.5rem; border-right:1px solid #333; text-align:center;
    transition:background 0.4s ease;
  }
  .tier:last-child{ border-right:none; }
  .tier:hover{ background:var(--charcoal); }
  .tier.featured{ background:var(--charcoal); position:relative; }
  .tier.featured::before{
    content:'PREFERRED'; position:absolute; top:0; left:50%; transform:translate(-50%,-50%);
    background:var(--gold); color:var(--black); font-size:0.6rem; letter-spacing:0.25em;
    padding:0.4rem 1.2rem;
  }
  .tier-name{
    font-family:'Cormorant Garamond',serif; font-style:italic; font-size:2rem; margin-bottom:0.5rem;
  }
  .tier-price{ font-size:0.9rem; color:var(--gold); letter-spacing:0.15em; margin-bottom:2rem; }
  .tier ul{ list-style:none; text-align:left; font-size:0.85rem; line-height:2.4; color:#B8B0A4; }
  .tier ul li::before{ content:'— '; color:var(--gold); }

  /* ===== FOOTER / CONTACT ===== */
  footer{
    padding:6rem 6vw 3rem; border-top:1px solid #2a2a2a; text-align:center;
  }
  footer .logo{ font-size:1.8rem; margin-bottom:1.5rem; }
  footer p{ font-size:0.8rem; color:#7a756d; letter-spacing:0.1em; margin-bottom:2rem; }
  .footer-links a{
    color:var(--ivory); text-decoration:none; font-size:0.7rem;
    letter-spacing:0.2em; text-transform:uppercase; margin:0 1.2rem;
    transition:color 0.3s ease;
  }
  .footer-links a:hover{ color:var(--gold); }
  .copyright{ margin-top:3rem; font-size:0.65rem; letter-spacing:0.2em; color:#4a4640; }

  /* ===== RESPONSIVE ===== */
  @media (max-width:900px){
    .manifesto{ grid-template-columns:1fr; gap:2.5rem; }
    .collection{ grid-template-columns:repeat(2,1fr); }
    .tiers{ grid-template-columns:1fr; }
    .tier{ border-right:none; border-bottom:1px solid #333; }
    nav{
      position:fixed; top:0; right:-100%; height:100vh; width:70%;
      background:var(--charcoal); flex-direction:column; justify-content:center;
      align-items:flex-start; padding:2rem 3rem; transition:right 0.4s ease;
    }
    nav.open{ right:0; }
    nav a{ margin:1rem 0; }
    .nav-toggle{
      display:block; background:none; border:none; color:var(--ivory);
      font-size:1.5rem; cursor:pointer; z-index:101;
    }
  }
  @media (max-width:600px){
    .collection{ grid-template-columns:1fr; }
  }

  @media (prefers-reduced-motion: reduce){
    *{ animation-duration:0.01ms !important; transition-duration:0.01ms !important; }
  }
</style>
</head>
<body>

<!-- ACCESS GATE -->
<div id="gate">
  <div class="gate-mark">MAISON NOIR</div>
  <div class="gate-line"></div>
  <div class="gate-sub">By Invitation Only</div>
  <button class="gate-btn" onclick="document.getElementById('gate').classList.add('hidden')">Enter the Atelier</button>
</div>

<!-- NAV -->
<header>
  <div class="logo">MAISON NOIR</div>
  <button class="nav-toggle" onclick="document.getElementById('mainnav').classList.toggle('open')" aria-label="Toggle menu">☰</button>
  <nav id="mainnav">
    <a href="#collection">Collection</a>
    <a href="#manifesto">Maison</a>
    <a href="#membership">Membership</a>
    <a href="#contact">Contact</a>
  </nav>
</header>

<!-- HERO -->
<section class="hero">
  <span class="hero-eyebrow">Spring / Summer Capsule</span>
  <h1>Quiet<span>Opulence.</span></h1>
  <p class="hero-sub">A wardrobe assembled for those who have already arrived. Each piece is produced in runs of fewer than twelve, reserved exclusively for members of the Maison.</p>
  <div class="hero-cta"><a href="#membership" class="btn-primary">Request Membership</a></div>
  <div class="scroll-cue">Scroll</div>
</section>

<!-- COLLECTION -->
<section id="collection">
  <div class="section-head">
    <span class="eyebrow">The Capsule</span>
    <h2>Eleven Pieces, No More</h2>
  </div>
  <div class="collection">
    <div class="piece"><div class="piece-info"><div class="piece-num">I</div><div class="piece-name">Cashmere Overcoat, Smoke</div><div class="piece-price">$18,400</div></div></div>
    <div class="piece"><div class="piece-info"><div class="piece-num">II</div><div class="piece-name">Silk Evening Gown, Noir</div><div class="piece-price">$24,900</div></div></div>
    <div class="piece"><div class="piece-info"><div class="piece-num">III</div><div class="piece-name">Hand-Stitched Loafers</div><div class="piece-price">$6,200</div></div></div>
    <div class="piece"><div class="piece-info"><div class="piece-num">IV</div><div class="piece-name">Vicuña Wool Suit</div><div class="piece-price">$32,500</div></div></div>
    <div class="piece"><div class="piece-info"><div class="piece-num">V</div><div class="piece-name">Alligator Tote, Bordeaux</div><div class="piece-price">$41,000</div></div></div>
    <div class="piece"><div class="piece-info"><div class="piece-num">VI</div><div class="piece-name">Tuxedo Jacket, Velvet</div><div class="piece-price">$15,750</div></div></div>
  </div>
</section>

<!-- MANIFESTO -->
<section id="manifesto">
  <div class="manifesto">
    <div class="manifesto-visual"></div>
    <div class="manifesto-text">
      <p>"We do not chase trends. We outlast them."</p>
      <p>Founded in Paris, Maison Noir produces fewer than 400 garments per year, each cut and finished by a single atelier of master tailors. There is no mass production, no seasonal sale, no compromise.</p>
      <p>Membership is the only path to acquisition. We believe true luxury is not what you can buy — it is what others cannot.</p>
    </div>
  </div>
</section>

<!-- MEMBERSHIP -->
<section id="membership">
  <div class="section-head">
    <span class="eyebrow">Access</span>
    <h2>Membership Tiers</h2>
  </div>
  <div class="tiers">
    <div class="tier">
      <div class="tier-name">Noir</div>
      <div class="tier-price">$25,000 / year</div>
      <ul>
        <li>Two capsule pieces annually</li>
        <li>Private viewing appointments</li>
        <li>Complimentary alterations</li>
      </ul>
    </div>
    <div class="tier featured">
      <div class="tier-name">Privé</div>
      <div class="tier-price">$95,000 / year</div>
      <ul>
        <li>Full capsule access, first selection</li>
        <li>Personal stylist on retainer</li>
        <li>Bespoke commissions, 2 per year</li>
        <li>Invitations to Maison events</li>
      </ul>
    </div>
    <div class="tier">
      <div class="tier-name">Sovereign</div>
      <div class="tier-price">By Application</div>
      <ul>
        <li>Unlimited bespoke commissions</li>
        <li>Dedicated atelier liaison</li>
        <li>Archive access &amp; reissues</li>
        <li>Global concierge fittings</li>
      </ul>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer id="contact">
  <div class="logo">MAISON NOIR</div>
  <p>Applications for membership are reviewed by invitation committee.<br>Allow 6–8 weeks for a response.</p>
  <div class="footer-links">
    <a href="#collection">Collection</a>
    <a href="#manifesto">Maison</a>
    <a href="#membership">Membership</a>
    <a href="mailto:atelier@maisonnoir.example">Correspondence</a>
  </div>
  <div class="copyright">© 2026 MAISON NOIR — PARIS · MILAN · KYOTO</div>
</footer>

<script>
  // Close mobile nav on link click
  document.querySelectorAll('nav a').forEach(a=>{
    a.addEventListener('click',()=>document.getElementById('mainnav').classList.remove('open'));
  });

  // Subtle reveal on scroll
  const observer = new IntersectionObserver((entries)=>{
    entries.forEach(entry=>{
      if(entry.isIntersecting){
        entry.target.style.opacity = '1';
        entry.target.style.transform = 'translateY(0)';
      }
    });
  },{threshold:0.15});

  document.querySelectorAll('.piece, .tier, .manifesto-text, .manifesto-visual').forEach(el=>{
    el.style.opacity = '0';
    el.style.transform = 'translateY(40px)';
    el.style.transition = 'opacity 0.8s ease, transform 0.8s ease';
    observer.observe(el);
  });

  // Auto-dismiss gate if user has visited before (still requires click first time)
  // intentionally none — every visit re-asserts exclusivity
</script>
</body>
</html>
