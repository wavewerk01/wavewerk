<html/>
<html lang="de" data-theme="light">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>WaveWerk – Bootsrestaurierung</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,500;0,600;0,700;1,400;1,600&family=Inter:wght@400;500;600&display=swap" rel="stylesheet">
<style>
*,*::before,*::after{margin:0;padding:0;box-sizing:border-box}
html{scroll-behavior:smooth}
 
[data-theme="light"]{
  --bg:#faf9f7;
  --bg2:#f3f1ed;
  --bg3:#ebe8e2;
  --nav-bg:rgba(250,249,247,0.94);
  --border:#e2ddd6;
  --border2:#c8c2b8;
  --text:#4a4540;
  --muted:#9a9289;
  --heading:#1a1612;
  --gold:#9a7340;
  --gold2:#b8894e;
  --gold-bg:rgba(154,115,64,0.07);
  --gold-line:rgba(154,115,64,0.25);
  --wip-c:#a86800;--wip-bg:rgba(168,104,0,0.07);--wip-bd:rgba(168,104,0,0.2);
  --done-c:#1a6b3a;--done-bg:rgba(26,107,58,0.07);--done-bd:rgba(26,107,58,0.2);
  --plain-c:#7a746e;
  --shadow:0 2px 8px rgba(0,0,0,0.05),0 8px 32px rgba(0,0,0,0.06);
  --shadow-h:0 4px 16px rgba(0,0,0,0.09),0 16px 48px rgba(0,0,0,0.1);
  --lux-accent:#1a1612;
}
[data-theme="dark"]{
  --bg:#111009;
  --bg2:#191610;
  --bg3:#211e16;
  --nav-bg:rgba(17,16,9,0.95);
  --border:#2e2a20;
  --border2:#3e3a2e;
  --text:#b0a898;
  --muted:#6e6860;
  --heading:#f0ece4;
  --gold:#c8a060;
  --gold2:#deb878;
  --gold-bg:rgba(200,160,96,0.08);
  --gold-line:rgba(200,160,96,0.2);
  --wip-c:#d4a030;--wip-bg:rgba(212,160,48,0.08);--wip-bd:rgba(212,160,48,0.22);
  --done-c:#3ecf6e;--done-bg:rgba(62,207,110,0.08);--done-bd:rgba(62,207,110,0.2);
  --plain-c:#666058;
  --shadow:0 2px 8px rgba(0,0,0,0.3),0 8px 32px rgba(0,0,0,0.25);
  --shadow-h:0 4px 16px rgba(0,0,0,0.4),0 16px 48px rgba(0,0,0,0.35);
  --lux-accent:#f0ece4;
}
 
body{
  font-family:'Inter',sans-serif;
  background:var(--bg);color:var(--text);
  overflow-x:hidden;
  transition:background .35s,color .35s;
  -webkit-font-smoothing:antialiased;
}
 
/* ── LUXURY ORNAMENT LINE ── */
.orn{
  display:flex;align-items:center;gap:1rem;
  margin-bottom:1.4rem;
}
.orn-line{flex:1;height:1px;background:var(--gold-line)}
.orn-diamond{
  width:6px;height:6px;background:var(--gold);
  transform:rotate(45deg);flex-shrink:0;
}
.orn-sm .orn-line{max-width:40px}
 
/* ── NAV ── */
nav{
  position:fixed;top:0;left:0;right:0;z-index:200;
  display:flex;align-items:center;justify-content:space-between;
  padding:0 3rem;height:64px;
  background:var(--nav-bg);
  border-bottom:1px solid var(--border);
  backdrop-filter:blur(20px);-webkit-backdrop-filter:blur(20px);
}
.nav-logo{
  font-family:'Cormorant Garamond',serif;
  font-size:1.35rem;font-weight:600;letter-spacing:.06em;
  color:var(--heading);text-decoration:none;
  display:flex;align-items:center;gap:.5rem;
}
.nav-logo-diamond{
  width:5px;height:5px;background:var(--gold);
  transform:rotate(45deg);flex-shrink:0;
}
.nav-c{display:flex;align-items:center;gap:2.2rem}
.nav-c a{
  font-size:.68rem;font-weight:500;letter-spacing:.16em;
  text-transform:uppercase;color:var(--muted);
  text-decoration:none;transition:color .2s;
}
.nav-c a:hover,.nav-c a.on{color:var(--heading)}
.nav-c a.nav-gold{color:var(--gold)}
.nav-c a.nav-gold:hover{color:var(--gold2)}
 
/* theme pill */
.tpill{
  position:relative;width:46px;height:24px;
  background:var(--bg3);border:1px solid var(--border2);
  border-radius:999px;cursor:pointer;flex-shrink:0;
  transition:background .3s;
}
.tknob{
  position:absolute;top:3px;left:3px;
  width:16px;height:16px;border-radius:50%;
  background:var(--gold);
  transition:transform .38s cubic-bezier(.34,1.56,.64,1);
  display:flex;align-items:center;justify-content:center;
  font-size:.6rem;line-height:1;
}
[data-theme="dark"] .tknob{transform:translateX(22px)}
 
/* hamburger */
.ham{display:none;flex-direction:column;gap:5px;background:none;border:none;cursor:pointer;padding:4px}
.ham span{display:block;width:22px;height:1.5px;background:var(--text);transition:all .25s}
.ham.open span:nth-child(1){transform:rotate(45deg) translate(4.5px,4.5px)}
.ham.open span:nth-child(2){opacity:0}
.ham.open span:nth-child(3){transform:rotate(-45deg) translate(4.5px,-4.5px)}
 
/* mobile overlay */
.mob{display:none;position:fixed;inset:0;z-index:199;background:var(--bg);flex-direction:column;align-items:center;justify-content:center;gap:2.5rem}
.mob.open{display:flex}
.mob a{font-family:'Cormorant Garamond',serif;font-size:2.2rem;font-weight:600;color:var(--heading);text-decoration:none;letter-spacing:.04em}
.mob a:hover{color:var(--gold)}
 
/* pages */
.pg{display:none}.pg.on{display:block}
 
/* ── HERO ── */
.hero{
  min-height:100vh;
  padding:64px 3rem 0;
  display:grid;grid-template-columns:1fr 1fr;
  align-items:center;gap:5rem;
  max-width:1240px;margin:0 auto;
}
.hero-text{padding:5rem 0}
 
.hero-kicker{
  display:flex;align-items:center;gap:.8rem;
  margin-bottom:2rem;
}
.hero-kicker-line{width:32px;height:1px;background:var(--gold)}
.hero-kicker span{
  font-size:.65rem;font-weight:600;letter-spacing:.24em;
  text-transform:uppercase;color:var(--gold);
}
 
.hero h1{
  font-family:'Cormorant Garamond',serif;
  font-size:clamp(3rem,5.5vw,5rem);
  font-weight:600;line-height:1.08;
  color:var(--heading);letter-spacing:-.01em;
  margin-bottom:1.6rem;
}
.hero h1 em{font-style:italic;font-weight:400;color:var(--gold)}
 
.hero-p{
  font-size:.95rem;color:var(--muted);
  line-height:1.8;max-width:400px;margin-bottom:2.6rem;
}
 
.hero-btns{display:flex;gap:1rem;flex-wrap:wrap}
 
.btn-lux{
  font-family:'Inter',sans-serif;font-size:.68rem;
  font-weight:600;letter-spacing:.18em;text-transform:uppercase;
  text-decoration:none;display:inline-flex;align-items:center;gap:.6rem;
  padding:.9rem 2rem;cursor:pointer;border:none;
  transition:all .25s;
}
.btn-lux-fill{background:var(--heading);color:var(--bg)}
.btn-lux-fill:hover{background:var(--gold);color:#fff}
.btn-lux-line{background:transparent;color:var(--text);border:1px solid var(--border2)}
.btn-lux-line:hover{border-color:var(--gold);color:var(--gold)}
.btn-arrow{font-size:.8rem;transition:transform .2s}
.btn-lux:hover .btn-arrow{transform:translateX(3px)}
 
.hero-divider{
  display:flex;align-items:center;gap:1.5rem;
  margin-top:3.5rem;padding-top:2.5rem;border-top:1px solid var(--border);
}
.hero-stat{flex:1}
.hstat-n{
  font-family:'Cormorant Garamond',serif;
  font-size:2.2rem;font-weight:600;color:var(--heading);line-height:1;
}
.hstat-l{
  font-size:.6rem;font-weight:500;letter-spacing:.18em;
  text-transform:uppercase;color:var(--muted);margin-top:.4rem;
}
.hero-divider-sep{width:1px;height:40px;background:var(--border);flex-shrink:0}
 
/* hero visual */
.hero-visual{
  position:relative;width:100%;aspect-ratio:4/3;
  background:var(--bg2);border:1px solid var(--border);
  overflow:hidden;
  display:flex;align-items:center;justify-content:center;
}
.hero-visual::before{
  content:'';position:absolute;inset:0;
  background:linear-gradient(135deg,transparent 60%,rgba(154,115,64,.06));
}
.hv-emoji{font-size:6rem;user-select:none;position:relative;z-index:1}
.hv-corner{
  position:absolute;width:20px;height:20px;
  border-color:var(--gold-line);border-style:solid;
}
.hv-tl{top:12px;left:12px;border-width:1px 0 0 1px}
.hv-tr{top:12px;right:12px;border-width:1px 1px 0 0}
.hv-bl{bottom:12px;left:12px;border-width:0 0 1px 1px}
.hv-br{bottom:12px;right:12px;border-width:0 1px 1px 0}
.hv-label{
  position:absolute;bottom:1.2rem;left:1.2rem;right:1.2rem;
  display:flex;justify-content:space-between;align-items:center;
}
.hv-tag{
  font-size:.58rem;font-weight:600;letter-spacing:.14em;text-transform:uppercase;
  padding:.28rem .75rem;background:var(--bg);border:1px solid var(--border);color:var(--text);
}
.hv-wip{
  font-size:.58rem;font-weight:600;letter-spacing:.14em;text-transform:uppercase;
  padding:.28rem .75rem;
  background:var(--wip-bg);border:1px solid var(--wip-bd);color:var(--wip-c);
}
 
/* ── SECTION BASE ── */
.wrap{max-width:1240px;margin:0 auto}
.sec{padding:7rem 3rem}
.sec-alt{background:var(--bg2);border-top:1px solid var(--border);border-bottom:1px solid var(--border)}
 
.s-eyebrow{
  display:flex;align-items:center;gap:.75rem;margin-bottom:1.4rem;
}
.s-eyebrow-line{width:28px;height:1px;background:var(--gold)}
.s-eyebrow span{
  font-size:.62rem;font-weight:600;letter-spacing:.22em;
  text-transform:uppercase;color:var(--gold);
}
.s-h{
  font-family:'Cormorant Garamond',serif;
  font-size:clamp(2rem,4vw,3rem);font-weight:600;
  color:var(--heading);line-height:1.12;letter-spacing:-.01em;
}
.s-sub{
  font-size:.9rem;color:var(--muted);
  line-height:1.8;max-width:480px;margin-top:.9rem;
}
 
/* ── HOW WE WORK ── */
.how-row{
  display:grid;grid-template-columns:repeat(4,1fr);
  margin-top:4rem;border:1px solid var(--border);
}
.how-item{
  padding:2.2rem 2rem;border-right:1px solid var(--border);
  transition:background .25s;
}
.how-item:last-child{border-right:none}
.how-item:hover{background:var(--bg3)}
.how-n{
  font-family:'Cormorant Garamond',serif;
  font-size:3rem;font-weight:400;color:var(--border2);
  line-height:1;margin-bottom:1.4rem;
}
.how-t{
  font-size:.7rem;font-weight:600;letter-spacing:.16em;
  text-transform:uppercase;color:var(--heading);margin-bottom:.7rem;
}
.how-d{font-size:.84rem;color:var(--muted);line-height:1.8}
 
/* ── BOAT CARD ── */
.boat-wrap{margin-top:4rem}
.boat-lux{
  border:1px solid var(--border);
  box-shadow:var(--shadow);
  display:grid;grid-template-columns:420px 1fr;
  overflow:hidden;transition:box-shadow .3s;
}
.boat-lux:hover{box-shadow:var(--shadow-h)}
.boat-vis{
  background:linear-gradient(160deg,var(--bg2),var(--bg3));
  display:flex;align-items:center;justify-content:center;
  font-size:6rem;position:relative;min-height:380px;
}
.boat-vis::after{
  content:'';position:absolute;inset:0;
  background:linear-gradient(to right,transparent,rgba(0,0,0,.02));
}
/* corner brackets on boat vis */
.bc{position:absolute;width:18px;height:18px;border-color:var(--gold-line);border-style:solid}
.bc-tl{top:14px;left:14px;border-width:1px 0 0 1px}
.bc-tr{top:14px;right:14px;border-width:1px 1px 0 0}
.bc-bl{bottom:14px;left:14px;border-width:0 0 1px 1px}
.bc-br{bottom:14px;right:14px;border-width:0 1px 1px 0}
.boat-vis-tags{
  position:absolute;top:1.2rem;left:1.2rem;
  display:flex;flex-direction:column;gap:.4rem;align-items:flex-start;z-index:1;
}
.btag{
  font-size:.58rem;font-weight:600;letter-spacing:.14em;
  text-transform:uppercase;padding:.28rem .75rem;display:inline-block;
}
.btag-wip{background:var(--wip-bg);color:var(--wip-c);border:1px solid var(--wip-bd)}
.btag-done{background:var(--done-bg);color:var(--done-c);border:1px solid var(--done-bd)}
 
.boat-body{
  padding:3rem;display:flex;flex-direction:column;
  border-left:1px solid var(--border);
}
.boat-eyebrow{
  font-size:.6rem;font-weight:600;letter-spacing:.2em;
  text-transform:uppercase;color:var(--muted);margin-bottom:.7rem;
}
.boat-name{
  font-family:'Cormorant Garamond',serif;
  font-size:2.2rem;font-weight:600;color:var(--heading);
  line-height:1.12;letter-spacing:-.01em;margin-bottom:1.2rem;
}
.boat-desc{font-size:.88rem;color:var(--muted);line-height:1.85;margin-bottom:2rem}
 
/* progress */
.prog-wrap{margin-bottom:2rem}
.prog-head{display:flex;justify-content:space-between;align-items:center;margin-bottom:.7rem}
.prog-head span:first-child{font-size:.62rem;font-weight:600;letter-spacing:.16em;text-transform:uppercase;color:var(--muted)}
.prog-head span:last-child{font-size:.78rem;font-weight:600;color:var(--wip-c)}
.prog-track{height:2px;background:var(--border);overflow:hidden}
.prog-fill{height:100%;width:35%;background:linear-gradient(90deg,var(--gold),var(--gold2))}
 
.boat-specs{
  display:grid;grid-template-columns:repeat(4,1fr);
  gap:1.4rem;margin-top:auto;padding-top:2rem;border-top:1px solid var(--border);
}
.spec-l{font-size:.56rem;font-weight:600;letter-spacing:.18em;text-transform:uppercase;color:var(--muted);margin-bottom:.35rem}
.spec-v{font-size:.92rem;font-weight:600;color:var(--heading)}
.spec-v.wip{color:var(--wip-c)}
 
/* ── SOCIALS BAR ── */
.soc-bar{
  padding:2.8rem 3rem;border-top:1px solid var(--border);
  max-width:1240px;margin:0 auto;
  display:flex;align-items:center;justify-content:space-between;
  gap:2rem;flex-wrap:wrap;
}
.soc-l h3{
  font-family:'Cormorant Garamond',serif;
  font-size:1.3rem;font-weight:600;color:var(--heading);margin-bottom:.2rem;letter-spacing:.02em;
}
.soc-l p{font-size:.82rem;color:var(--muted)}
.soc-links{display:flex;gap:.6rem;flex-wrap:wrap}
.soc-a{
  display:flex;align-items:center;gap:.55rem;
  padding:.65rem 1.25rem;border:1px solid var(--border);
  text-decoration:none;background:var(--bg);transition:all .22s;
}
.soc-a:hover{border-color:var(--gold-line);background:var(--gold-bg)}
.soc-a span{font-size:.7rem;font-weight:600;letter-spacing:.08em;color:var(--text);transition:color .2s}
.soc-a:hover span{color:var(--gold)}
.soc-a svg{flex-shrink:0;transition:opacity .2s}
.soc-a:hover svg{opacity:.7}
 
/* ── CTA ── */
.cta-outer{
  background:var(--heading);
  padding:5.5rem 3rem;
}
.cta-in{
  max-width:1240px;margin:0 auto;
  display:flex;align-items:center;justify-content:space-between;
  gap:2rem;flex-wrap:wrap;
}
.cta-in h2{
  font-family:'Cormorant Garamond',serif;
  font-size:clamp(1.8rem,3.5vw,2.8rem);font-weight:600;
  color:var(--bg);margin-bottom:.4rem;
}
.cta-in p{font-size:.88rem;color:rgba(250,249,247,.45)}
[data-theme="dark"] .cta-in p{color:rgba(17,16,9,.45)}
.btn-cta{
  font-family:'Inter',sans-serif;font-size:.68rem;
  font-weight:600;letter-spacing:.18em;text-transform:uppercase;
  padding:.95rem 2.2rem;background:var(--bg);color:var(--heading);
  text-decoration:none;flex-shrink:0;
  border:none;cursor:pointer;transition:opacity .2s;
  display:inline-block;
}
.btn-cta:hover{opacity:.8}
 
/* ── FOOTER ── */
.foot-outer{border-top:1px solid var(--border)}
.foot-in{
  max-width:1240px;margin:0 auto;
  padding:2.2rem 3rem;
  display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:1rem;
}
.foot-logo{
  font-family:'Cormorant Garamond',serif;
  font-size:1.05rem;font-weight:600;color:var(--heading);
  display:flex;align-items:center;gap:.45rem;
}
.foot-logo-d{width:5px;height:5px;background:var(--gold);transform:rotate(45deg)}
.foot-nav{display:flex;gap:2rem}
.foot-nav a{font-size:.62rem;font-weight:500;letter-spacing:.14em;text-transform:uppercase;color:var(--muted);text-decoration:none;transition:color .2s}
.foot-nav a:hover{color:var(--heading)}
.foot-copy{font-size:.62rem;color:var(--muted);opacity:.6}
 
/* ── ABOUT PAGE ── */
.about-top{
  padding:calc(64px + 5.5rem) 3rem 5.5rem;
  max-width:1240px;margin:0 auto;
  border-bottom:1px solid var(--border);
}
.about-top h1{
  font-family:'Cormorant Garamond',serif;
  font-size:clamp(3rem,7vw,5.5rem);font-weight:600;
  color:var(--heading);line-height:1.06;letter-spacing:-.01em;
  max-width:720px;margin-top:1.2rem;
}
.about-top h1 em{font-style:italic;font-weight:400;color:var(--gold)}
.about-top p{font-size:.95rem;color:var(--muted);max-width:480px;line-height:1.8;margin-top:1.6rem}
 
/* team */
.team-row{display:grid;grid-template-columns:1fr 1fr;gap:1.5rem;margin-top:3.5rem}
.t-card{
  border:1px solid var(--border);padding:2.5rem;
  background:var(--bg2);box-shadow:var(--shadow);transition:box-shadow .25s;
  position:relative;overflow:hidden;
}
.t-card::before{
  content:'';position:absolute;top:0;left:0;right:0;height:2px;
  background:linear-gradient(90deg,var(--gold),transparent);
  opacity:0;transition:opacity .3s;
}
.t-card:hover{box-shadow:var(--shadow-h)}
.t-card:hover::before{opacity:1}
.t-init{
  width:46px;height:46px;
  display:flex;align-items:center;justify-content:center;
  font-family:'Cormorant Garamond',serif;font-size:1.2rem;font-weight:600;
  margin-bottom:1.6rem;border:1px solid var(--gold-line);
  color:var(--gold);background:var(--gold-bg);
}
.t-name{
  font-family:'Cormorant Garamond',serif;
  font-size:1.5rem;font-weight:600;color:var(--heading);margin-bottom:.25rem;
}
.t-role{
  font-size:.6rem;font-weight:600;letter-spacing:.2em;
  text-transform:uppercase;color:var(--gold);margin-bottom:1.2rem;
}
.t-bio{font-size:.86rem;color:var(--muted);line-height:1.82}
.t-tags{display:flex;flex-wrap:wrap;gap:.4rem;margin-top:1.4rem}
.t-tag{
  font-size:.6rem;font-weight:500;padding:.28rem .75rem;
  border:1px solid var(--border);color:var(--muted);background:var(--bg);
  letter-spacing:.04em;
}
 
/* story */
.story-cols{display:grid;grid-template-columns:1fr 1.6fr;gap:6rem;align-items:center}
.story-q{
  border-left:1px solid var(--gold);padding-left:2.2rem;
}
.story-q blockquote{
  font-family:'Cormorant Garamond',serif;
  font-size:1.6rem;font-weight:400;font-style:italic;
  color:var(--heading);line-height:1.45;
}
.story-q cite{
  display:block;margin-top:1.2rem;
  font-size:.6rem;font-weight:600;letter-spacing:.2em;
  text-transform:uppercase;color:var(--muted);font-style:normal;
}
.story-r h2{
  font-family:'Cormorant Garamond',serif;
  font-size:2rem;font-weight:600;color:var(--heading);
  margin-bottom:1.4rem;letter-spacing:-.01em;
}
.story-r p{font-size:.88rem;color:var(--muted);line-height:1.88;margin-bottom:1rem}
 
/* values */
.val-cols{display:grid;grid-template-columns:repeat(3,1fr);margin-top:3.5rem;border:1px solid var(--border)}
.val-item{padding:2.2rem 2rem;border-right:1px solid var(--border)}
.val-item:last-child{border-right:none}
.val-t{
  font-size:.62rem;font-weight:600;letter-spacing:.2em;
  text-transform:uppercase;color:var(--gold);margin-bottom:.9rem;
}
.val-d{font-size:.86rem;color:var(--muted);line-height:1.82}
 
/* contact */
.contact-cols{display:grid;grid-template-columns:1fr 1fr;gap:5rem;align-items:start}
.contact-cols h2{
  font-family:'Cormorant Garamond',serif;
  font-size:2.2rem;font-weight:600;color:var(--heading);
  margin-bottom:.9rem;letter-spacing:-.01em;
}
.contact-cols>div>p{font-size:.88rem;color:var(--muted);line-height:1.82;margin-bottom:2rem}
.c-list{display:flex;flex-direction:column}
.c-row{
  display:flex;justify-content:space-between;align-items:center;
  padding:1.1rem 0;border-bottom:1px solid var(--border);gap:1rem;
}
.c-row:first-child{border-top:1px solid var(--border)}
.c-label{font-size:.6rem;font-weight:600;letter-spacing:.18em;text-transform:uppercase;color:var(--muted)}
.c-val{font-size:.86rem;font-weight:500;color:var(--text)}
.c-val.pending{color:var(--muted);font-style:italic;font-weight:400}
 
/* ── MOBILE ── */
@media(max-width:900px){
  .hero{grid-template-columns:1fr;gap:2rem;padding-top:84px}
  .hero-visual{display:none}
  .hero-text{padding:3rem 0}
  .how-row{grid-template-columns:1fr 1fr}
  .how-item{border-bottom:1px solid var(--border)}
  .how-item:nth-child(odd){border-right:1px solid var(--border)}
  .how-item:nth-child(even){border-right:none}
  .how-item:nth-last-child(-n+2){border-bottom:none}
  .boat-lux{grid-template-columns:1fr}
  .boat-vis{min-height:220px;font-size:5rem}
  .boat-body{border-left:none;border-top:1px solid var(--border);padding:2rem}
  .boat-specs{grid-template-columns:1fr 1fr}
  .story-cols{grid-template-columns:1fr;gap:3rem}
  .team-row{grid-template-columns:1fr}
  .val-cols{grid-template-columns:1fr}
  .val-item{border-right:none;border-bottom:1px solid var(--border)}
  .val-item:last-child{border-bottom:none}
  .contact-cols{grid-template-columns:1fr;gap:3rem}
}
@media(max-width:600px){
  nav{padding:0 1.3rem;height:56px}
  .nav-c a:not(.nav-gold){display:none}
  .nav-c a.nav-gold{display:none}
  .ham{display:flex}
  .hero,.sec,.about-top,.soc-bar,.cta-outer,.foot-in{padding-left:1.3rem;padding-right:1.3rem}
  .sec-alt{padding-left:1.3rem;padding-right:1.3rem}
  .hero-btns{flex-direction:column}
  .btn-lux{width:100%;justify-content:center}
  .how-row{grid-template-columns:1fr}
  .how-item{border-right:none!important}
  .soc-bar{flex-direction:column;align-items:flex-start}
  .cta-in{flex-direction:column}
  .btn-cta{width:100%;text-align:center}
  .foot-in{flex-direction:column;align-items:flex-start}
  .hero-divider{gap:1rem}
  .boat-specs{grid-template-columns:1fr 1fr}
}
</style>
</head>
<body>
 
<!-- MOBILE OVERLAY -->
<div class="mob" id="mob">
  <a href="#" onclick="P('home');CM();return false">Start</a>
  <a href="#" onclick="P('about');CM();return false">Über uns</a>
  <a href="#" onclick="P('home');CM();S('projekte');return false">Projekte</a>
  <a href="#" onclick="P('about');CM();S('kontakt');return false" style="color:var(--gold)">Kontakt</a>
</div>
 
<!-- NAV -->
<nav>
  <a class="nav-logo" href="#" onclick="P('home');return false">
    WaveWerk <div class="nav-logo-diamond"></div>
  </a>
  <div class="nav-c">
    <a href="#" id="nl-home" class="on" onclick="P('home');return false">Start</a>
    <a href="#" id="nl-about" onclick="P('about');return false">Über uns</a>
    <a href="#" onclick="P('home');S('projekte');return false">Projekte</a>
    <a href="#" class="nav-gold" onclick="P('about');S('kontakt');return false">Kontakt</a>
    <button class="tpill" onclick="TT()" aria-label="Theme">
      <div class="tknob" id="knob">☀️</div>
    </button>
    <button class="ham" id="ham" onclick="TM()">
      <span></span><span></span><span></span>
    </button>
  </div>
</nav>
 
 
<!-- ══════════════ START ══════════════ -->
<div id="pg-home" class="pg on">
 
<div class="hero">
  <div class="hero-text">
    <div class="hero-kicker">
      <div class="hero-kicker-line"></div>
      <span>Bootsrestaurierung &amp; Verkauf</span>
    </div>
    <h1>Alte Boote.<br><em>Neu gedacht.</em></h1>
    <p class="hero-p">Wir kaufen vernachlässigte Boote, restaurieren sie von Hand und geben ihnen ein neues Leben. Begonnen mit 15 – angetrieben von Leidenschaft.</p>
    <div class="hero-btns">
      <a class="btn-lux btn-lux-fill" href="#" onclick="S('projekte');return false">Unser Boot <span class="btn-arrow">→</span></a>
      <a class="btn-lux btn-lux-line" href="#" onclick="P('about');return false">Über uns</a>
    </div>
    <div class="hero-divider">
      <div class="hero-stat"><div class="hstat-n">4,2 m</div><div class="hstat-l">Aktuelles Projekt</div></div>
      <div class="hero-divider-sep"></div>
      <div class="hero-stat"><div class="hstat-n">15 PS</div><div class="hstat-l">4-Takt Motor</div></div>
      <div class="hero-divider-sep"></div>
      <div class="hero-stat"><div class="hstat-n">2</div><div class="hstat-l">Macher</div></div>
    </div>
  </div>
  <div class="hero-visual">
    <div class="hv-corner hv-tl"></div>
    <div class="hv-corner hv-tr"></div>
    <div class="hv-corner hv-bl"></div>
    <div class="hv-corner hv-br"></div>
    <div class="hv-emoji">🚤</div>
    <div class="hv-label">
      <span class="hv-tag">Alu · 4,2 m · 15 PS</span>
      <span class="hv-wip">In Restaurierung</span>
    </div>
  </div>
</div>
 
<!-- HOW -->
<div class="sec-alt">
  <div class="sec wrap">
    <div class="s-eyebrow"><div class="s-eyebrow-line"></div><span>Wie wir arbeiten</span></div>
    <h2 class="s-h">Vom vergessenen Boot<br>zum Schmuckstück</h2>
    <div class="how-row">
      <div class="how-item">
        <div class="how-n">01</div>
        <div class="how-t">Aufspüren</div>
        <div class="how-d">Vernachlässigte Boote auf Märkten, Auktionen und von Privat. Je schlechter der Zustand, desto mehr Potenzial.</div>
      </div>
      <div class="how-item">
        <div class="how-n">02</div>
        <div class="how-t">Restaurieren</div>
        <div class="how-d">Rumpf, Deck, Motor – alles wird mit Handwerk und Geduld Schritt für Schritt wieder in Form gebracht.</div>
      </div>
      <div class="how-item">
        <div class="how-n">03</div>
        <div class="how-t">Veredeln</div>
        <div class="how-d">Lackierung, Beschläge, letzter Schliff. Jedes Detail zählt bis zum finalen Pinselstrich.</div>
      </div>
      <div class="how-item">
        <div class="how-n">04</div>
        <div class="how-t">Übergeben</div>
        <div class="how-d">Ehrliche Übergabe mit vollständiger Dokumentation. Qualität, die man sieht und spürt.</div>
      </div>
    </div>
  </div>
</div>
 
<!-- BOOT -->
<div class="sec wrap" id="projekte">
  <div class="s-eyebrow"><div class="s-eyebrow-line"></div><span>Aktuelles Projekt</span></div>
  <h2 class="s-h">Unser Boot</h2>
  <p class="s-sub">Direkt gekauft, direkt an die Arbeit – folge dem Fortschritt.</p>
  <div class="boat-wrap">
    <div class="boat-lux">
      <div class="boat-vis">
        <div class="bc bc-tl"></div><div class="bc bc-tr"></div>
        <div class="bc bc-bl"></div><div class="bc bc-br"></div>
        🚤
        <div class="boat-vis-tags">
          <span class="btag btag-wip">In Restaurierung</span>
        </div>
      </div>
      <div class="boat-body">
        <p class="boat-eyebrow">Aluminium · 4-Takt Außenborder</p>
        <h3 class="boat-name">Alu-Motorboot<br>4,2 Meter</h3>
        <p class="boat-desc">Wir haben dieses 4,2-Meter-Aluboot mit 15-PS-4-Takt-Außenborder in schlechtem Zustand erworben – Rost, ramponiertes Deck, Motor mit Startschwierigkeiten. Genau unser Ding. Aktuell wird der Rumpf geschliffen und versiegelt, das Deck erneuert und der Motor generalüberholt. Updates folgen.</p>
        <div class="prog-wrap">
          <div class="prog-head">
            <span>Restaurierungsfortschritt</span>
            <span>~35%</span>
          </div>
          <div class="prog-track"><div class="prog-fill"></div></div>
        </div>
        <div class="boat-specs">
          <div><div class="spec-l">Länge</div><div class="spec-v">4,2 m</div></div>
          <div><div class="spec-l">Motor</div><div class="spec-v">15 PS / 4-Takt</div></div>
          <div><div class="spec-l">Rumpf</div><div class="spec-v">Aluminium</div></div>
          <div><div class="spec-l">Status</div><div class="spec-v wip">In Arbeit ⚒</div></div>
        </div>
      </div>
    </div>
  </div>
</div>
 
<!-- SOCIALS -->
<div class="soc-bar">
  <div class="soc-l">
    <h3>Folg dem Projekt</h3>
    <p>Updates, Behind-the-Scenes und fertige Boote.</p>
  </div>
  <div class="soc-links">
    <a class="soc-a" href="https://instagram.com/wavewerkboote" target="_blank">
      <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" style="color:var(--muted)"><rect x="2" y="2" width="20" height="20" rx="5"/><circle cx="12" cy="12" r="4"/><circle cx="17.5" cy="6.5" r=".8" fill="currentColor" stroke="none"/></svg>
      <span>Instagram</span>
    </a>
    <a class="soc-a" href="https://youtube.com/@wavewerkboote" target="_blank">
      <svg width="15" height="15" viewBox="0 0 24 24" fill="currentColor" style="color:var(--muted)"><path d="M23 7s-.3-2-1.2-2.8c-1.1-1.2-2.4-1.2-3-1.3C16.6 2.8 12 2.8 12 2.8s-4.6 0-6.8.1c-.6.1-1.9.1-3 1.3C1.3 5 1 7 1 7S.7 9.2.7 11.3v2c0 2.1.3 4.3.3 4.3s.3 2 1.2 2.8c1.1 1.2 2.6 1.1 3.3 1.2C7.5 21.8 12 21.8 12 21.8s4.6 0 6.8-.2c.6-.1 1.9-.1 3-1.3.9-.8 1.2-2.8 1.2-2.8s.3-2.2.3-4.3v-2C23.3 9.2 23 7 23 7zM9.7 15.5V8.4l8.1 3.6-8.1 3.5z"/></svg>
      <span>YouTube</span>
    </a>
  </div>
</div>
 
<!-- CTA -->
<div class="cta-outer">
  <div class="cta-in">
    <div>
      <h2>Boot zu verkaufen?</h2>
      <p>Wir schauen es uns an – egal in welchem Zustand.</p>
    </div>
    <a class="btn-cta" href="#" onclick="P('about');S('kontakt');return false">Kontakt aufnehmen</a>
  </div>
</div>
 
<div class="foot-outer">
  <div class="foot-in">
    <div class="foot-logo">WaveWerk <div class="foot-logo-d"></div></div>
    <nav class="foot-nav">
      <a href="#" onclick="P('home');return false">Start</a>
      <a href="#" onclick="P('about');return false">Über uns</a>
      <a href="#" onclick="S('projekte');return false">Projekte</a>
    </nav>
    <div class="foot-copy">© 2030 WaveWerk</div>
  </div>
</div>
 
</div><!-- /home -->
 
 
<!-- ══════════════ ÜBER UNS ══════════════ -->
<div id="pg-about" class="pg">
 
<div class="about-top">
  <div class="s-eyebrow"><div class="s-eyebrow-line"></div><span>Über uns</span></div>
  <h1>Zwei Freunde.<br><em>Eine Leidenschaft.</em></h1>
  <p>Wir restaurieren Boote, weil wir es lieben. Gestartet mit 15 Jahren, angetrieben von einer verrückten Idee – das ist heute WaveWerk.</p>
</div>
 
<div class="sec wrap">
  <div class="s-eyebrow"><div class="s-eyebrow-line"></div><span>Das Team</span></div>
  <h2 class="s-h">Die Macher</h2>
  <div class="team-row">
 
    <div class="t-card">
      <div class="t-init">F</div>
      <p class="t-name">Finn</p>
      <p class="t-role">CEO · Elektrik · Motor · Webentwicklung</p>
      <p class="t-bio">Finn ist der technische Kopf hinter WaveWerk. Er übernimmt alles rund um Elektrik und Motorüberholung am Boot – und hält gleichzeitig die Website am Laufen. Wenn etwas nicht anspringt, bringt er es zum Laufen.</p>
      <div class="t-tags">
        <span class="t-tag">Elektrik</span>
        <span class="t-tag">Motorüberholung</span>
        <span class="t-tag">Webentwicklung</span>
        <span class="t-tag">Technische Diagnose</span>
        <span class="t-tag">Beschaffung</span>
      </div>
    </div>
 
    <div class="t-card">
      <div class="t-init">B</div>
      <p class="t-name">Bastian</p>
      <p class="t-role">CEO · Content · Marketing · Verkauf &amp; Ankauf · Interiör &amp; Zubehör</p>
      <p class="t-bio">Bastian ist das Gesicht nach außen und der Mann für den letzten Eindruck. Er kümmert sich um Content, Social Media und darum, dass WaveWerk wahrgenommen wird – und um alles was ein Boot innen schön macht.</p>
      <div class="t-tags">
        <span class="t-tag">Content</span>
        <span class="t-tag">Marketing</span>
        <span class="t-tag">Verkauf &amp; Ankauf</span>
        <span class="t-tag">Interiör</span>
        <span class="t-tag">Zubehör</span>
      </div>
    </div>
 
  </div>
</div>
 
<div class="sec-alt">
  <div class="sec wrap">
    <div class="story-cols">
      <div class="story-q">
        <blockquote>„Wir retten Boote, die andere vergessen haben."</blockquote>
        <cite>— Finn &amp; Bastian, WaveWerk</cite>
      </div>
      <div class="story-r">
        <h2>Wie alles begann</h2>
        <p>Wir waren 15 – keine Ahnung von Booten, aber jede Menge Neugierde und Energie. Die Idee war simpel: ein altes Boot kaufen, herrichten, verkaufen. Was als jugendliche Schnapsidee startete, wurde zur echten Leidenschaft.</p>
        <p>Unser aktuelles Projekt: ein Alu-Motorboot in schlechtem Zustand. Wir bauen es komplett auf – nach der Schule, an Wochenenden, mit den Händen die wir haben.</p>
        <p>Was mit 15 startete, ist heute WaveWerk.</p>
      </div>
    </div>
  </div>
</div>
 
<div class="sec wrap">
  <div class="s-eyebrow"><div class="s-eyebrow-line"></div><span>Was uns antreibt</span></div>
  <h2 class="s-h">Unsere Werte</h2>
  <div class="val-cols">
    <div class="val-item"><p class="val-t">Handwerk</p><p class="val-d">Kein schnelles Spray. Jeder Handgriff sitzt. Wir nehmen uns die Zeit, die ein Boot verdient.</p></div>
    <div class="val-item"><p class="val-t">Ehrlichkeit</p><p class="val-d">Jeder Käufer bekommt das Boot, das er sieht – mit der kompletten Geschichte dazu.</p></div>
    <div class="val-item"><p class="val-t">Leidenschaft</p><p class="val-d">Wir tun das, weil wir es lieben. Das merkt man jedem Boot an, das unsere Werkstatt verlässt.</p></div>
  </div>
</div>
 
<div class="sec-alt" id="kontakt">
  <div class="sec wrap">
    <div class="contact-cols">
      <div>
        <div class="s-eyebrow"><div class="s-eyebrow-line"></div><span>Kontakt</span></div>
        <h2>Schreib uns.</h2>
        <p>Boot zu verkaufen? Was Bestimmtes gesucht? Oder einfach mal vorbeikommen? Wir freuen uns.</p>
        <a class="btn-lux btn-lux-fill" href="#" style="display:inline-flex">Nachricht schicken <span class="btn-arrow">→</span></a>
      </div>
      <div class="c-list">
        <div class="c-row"><span class="c-label">E-Mail</span><span class="c-val pending">kommt noch</span></div>
        <div class="c-row"><span class="c-label">Telefon</span><span class="c-val pending">kommt noch</span></div>
        <div class="c-row"><span class="c-label">Standort</span><span class="c-val">Brandenburg</span></div>
        <div class="c-row"><span class="c-label">Instagram</span><span class="c-val pending">kommt noch</span></div>
        <div class="c-row"><span class="c-label">YouTube</span><span class="c-val pending">kommt noch</span></div>
      </div>
    </div>
  </div>
</div>
 
<div class="foot-outer">
  <div class="foot-in">
    <div class="foot-logo">WaveWerk <div class="foot-logo-d"></div></div>
    <nav class="foot-nav">
      <a href="#" onclick="P('home');return false">Start</a>
      <a href="#" onclick="P('about');return false">Über uns</a>
      <a href="#" onclick="P('home');S('projekte');return false">Projekte</a>
    </nav>
    <div class="foot-copy">© 2030 WaveWerk</div>
  </div>
</div>
 
</div><!-- /about -->
 
<script>
var dark=false;
function TT(){
  dark=!dark;
  document.documentElement.setAttribute('data-theme',dark?'dark':'light');
  document.getElementById('knob').textContent=dark?'🌙':'☀️';
}
function P(p){
  document.querySelectorAll('.pg').forEach(e=>e.classList.remove('on'));
  document.getElementById('pg-'+p).classList.add('on');
  ['home','about'].forEach(k=>{
    var e=document.getElementById('nl-'+k);
    if(e)e.classList.toggle('on',k===p);
  });
  window.scrollTo({top:0,behavior:'smooth'});
}
function S(id){
  setTimeout(()=>{var e=document.getElementById(id);if(e)e.scrollIntoView({behavior:'smooth'})},80);
}
function TM(){
  document.getElementById('mob').classList.toggle('open');
  document.getElementById('ham').classList.toggle('open');
}
function CM(){
  document.getElementById('mob').classList.remove('open');
  document.getElementById('ham').classList.remove('open');
}
</script>
</body>
</html>
