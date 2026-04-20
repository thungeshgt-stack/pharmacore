<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>PharmaCore — Your Complete Health Solution</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:ital,wght@0,300;0,400;0,500;0,600;1,400&display=swap" rel="stylesheet"/>
<style>
*{margin:0;padding:0;box-sizing:border-box;}
:root{
  --p1:#7B2FBE;--p2:#9B59B6;--p3:#E8D5F5;--p4:#F5EEFF;
  --dark:#1a1a2e;--dark2:#2d1b69;--white:#fff;--gray:#6c757d;
  --success:#27ae60;--danger:#e74c3c;--warn:#f39c12;
  --font-head:'Syne',sans-serif;--font-body:'DM Sans',sans-serif;
}
html{scroll-behavior:smooth;}
body{font-family:var(--font-body);background:var(--white);color:var(--dark);overflow-x:hidden;}

/* ---- 3D FLOATING PARTICLES CANVAS ---- */
#particles-canvas{position:fixed;top:0;left:0;width:100%;height:100%;pointer-events:none;z-index:0;opacity:0.4;}

/* ---- NAVIGATION ---- */
.nav{background:rgba(255,255,255,0.92);backdrop-filter:blur(20px);border-bottom:1px solid rgba(123,47,190,0.12);padding:0 2.5rem;display:flex;align-items:center;justify-content:space-between;height:72px;position:sticky;top:0;z-index:1000;transition:all 0.3s;}
.nav.scrolled{box-shadow:0 4px 30px rgba(123,47,190,0.08);}
.logo{display:flex;align-items:center;gap:12px;text-decoration:none;}
.logo-cube{width:44px;height:44px;perspective:200px;cursor:pointer;}
.cube-inner{width:100%;height:100%;position:relative;transform-style:preserve-3d;animation:rotateCube 8s linear infinite;}
.cube-face{position:absolute;width:44px;height:44px;border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:20px;backface-visibility:hidden;}
.cube-f{background:linear-gradient(135deg,#7B2FBE,#9B59B6);transform:translateZ(22px);}
.cube-b{background:linear-gradient(135deg,#9B59B6,#C39BD3);transform:rotateY(180deg) translateZ(22px);}
.cube-l{background:linear-gradient(135deg,#6C3483,#7B2FBE);transform:rotateY(-90deg) translateZ(22px);}
.cube-r{background:linear-gradient(135deg,#A569BD,#C39BD3);transform:rotateY(90deg) translateZ(22px);}
@keyframes rotateCube{0%{transform:rotateX(0) rotateY(0)}100%{transform:rotateX(360deg) rotateY(360deg)}}
.logo-text-wrap .logo-name{font-family:var(--font-head);font-size:20px;font-weight:800;color:var(--p1);line-height:1;}
.logo-text-wrap .logo-tagline{font-size:10px;color:var(--gray);letter-spacing:2px;text-transform:uppercase;}
.nav-links{display:flex;gap:4px;list-style:none;}
.nav-links a{text-decoration:none;color:var(--dark);font-size:14px;font-weight:500;padding:7px 16px;border-radius:25px;transition:all 0.25s;cursor:pointer;font-family:var(--font-body);}
.nav-links a:hover,.nav-links a.active{background:var(--p1);color:white;transform:translateY(-1px);}
.nav-right{display:flex;gap:10px;align-items:center;}
.btn{padding:9px 22px;border-radius:25px;border:none;cursor:pointer;font-weight:600;font-size:13px;transition:all 0.25s;font-family:var(--font-body);}
.btn-outline{background:white;border:1.5px solid var(--p1);color:var(--p1);}
.btn-primary{background:linear-gradient(135deg,var(--p1),var(--p2));color:white;box-shadow:0 4px 15px rgba(123,47,190,0.25);}
.btn:hover{transform:translateY(-2px);box-shadow:0 8px 20px rgba(123,47,190,0.2);}
.cart-badge{background:var(--danger);color:white;border-radius:50%;width:16px;height:16px;font-size:9px;display:inline-flex;align-items:center;justify-content:center;vertical-align:top;margin-left:-4px;margin-top:-4px;}

/* ---- PAGES ---- */
.page{display:none;position:relative;z-index:1;}
.page.active{display:block;}

/* ---- 3D HERO ---- */
.hero{background:linear-gradient(135deg,#0f0c29,#302b63,#24243e);min-height:92vh;display:flex;align-items:center;padding:4rem 5rem;position:relative;overflow:hidden;}
.hero-bg-orb{position:absolute;border-radius:50%;filter:blur(80px);animation:orbFloat 6s ease-in-out infinite;}
.orb1{width:500px;height:500px;background:rgba(123,47,190,0.2);top:-100px;right:-100px;}
.orb2{width:300px;height:300px;background:rgba(100,149,237,0.1);bottom:50px;left:100px;animation-delay:-3s;}
@keyframes orbFloat{0%,100%{transform:translateY(0) scale(1);}50%{transform:translateY(-30px) scale(1.05);}}
.hero-content{max-width:52%;z-index:2;animation:fadeSlideUp 1s ease forwards;}
@keyframes fadeSlideUp{from{opacity:0;transform:translateY(40px);}to{opacity:1;transform:translateY(0);}}
.hero-badge{display:inline-flex;align-items:center;gap:8px;background:rgba(155,89,182,0.2);border:1px solid rgba(155,89,182,0.4);color:#d7b8f3;padding:7px 18px;border-radius:25px;font-size:12px;margin-bottom:2rem;font-weight:500;letter-spacing:0.5px;}
.pulse-dot{width:8px;height:8px;background:#27ae60;border-radius:50%;animation:pulseDot 2s infinite;}
@keyframes pulseDot{0%,100%{box-shadow:0 0 0 0 rgba(39,174,96,0.4);}50%{box-shadow:0 0 0 8px rgba(39,174,96,0);}}
.hero h1{font-family:var(--font-head);font-size:3.4rem;font-weight:800;color:white;line-height:1.15;margin-bottom:1.2rem;}
.hero h1 .accent{background:linear-gradient(135deg,#c89ef2,#7ec8e3);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;}
.hero p{font-size:1.05rem;color:rgba(255,255,255,0.65);margin-bottom:2.5rem;line-height:1.8;max-width:480px;}
.hero-btns{display:flex;gap:1rem;flex-wrap:wrap;}
.hero-btn-main{background:linear-gradient(135deg,var(--p1),#c39bd3);color:white;padding:15px 36px;border-radius:35px;border:none;font-size:15px;font-weight:700;cursor:pointer;transition:all 0.3s;font-family:var(--font-head);letter-spacing:0.5px;box-shadow:0 8px 30px rgba(123,47,190,0.4);}
.hero-btn-main:hover{transform:translateY(-3px) scale(1.02);box-shadow:0 15px 40px rgba(123,47,190,0.5);}
.hero-btn-sec{background:transparent;color:white;padding:15px 36px;border-radius:35px;border:1.5px solid rgba(255,255,255,0.25);font-size:15px;font-weight:600;cursor:pointer;transition:all 0.3s;font-family:var(--font-body);}
.hero-btn-sec:hover{background:rgba(255,255,255,0.08);transform:translateY(-2px);}

/* 3D FLOATING CARD CLUSTER */
.hero-3d-cluster{position:absolute;right:4rem;top:50%;transform:translateY(-50%);width:340px;perspective:800px;}
.floating-card{background:rgba(255,255,255,0.06);backdrop-filter:blur(20px);border:1px solid rgba(255,255,255,0.1);border-radius:20px;padding:1.2rem 1.5rem;margin-bottom:14px;color:white;transform-style:preserve-3d;transition:transform 0.3s;animation:floatCard 4s ease-in-out infinite;}
.floating-card:nth-child(1){animation-delay:0s;}
.floating-card:nth-child(2){animation-delay:-1.3s;}
.floating-card:nth-child(3){animation-delay:-2.6s;}
@keyframes floatCard{0%,100%{transform:translateY(0) rotateX(2deg);}50%{transform:translateY(-12px) rotateX(-2deg);}}
.floating-card:hover{transform:translateY(-8px) rotateY(5deg) scale(1.02);}
.fc-label{font-size:11px;color:rgba(255,255,255,0.5);text-transform:uppercase;letter-spacing:1.5px;margin-bottom:4px;}
.fc-value{font-family:var(--font-head);font-size:1.8rem;font-weight:800;color:#c89ef2;}
.fc-sub{font-size:12px;color:rgba(255,255,255,0.6);margin-top:2px;}
.fc-icon{font-size:28px;float:right;margin-top:-10px;}

/* ---- TRUST BAR ---- */
.trust-bar{background:var(--p4);padding:1.8rem 4rem;display:flex;justify-content:space-around;align-items:center;flex-wrap:wrap;gap:1rem;border-bottom:1px solid var(--p3);}
.trust-item{text-align:center;}
.trust-num{font-family:var(--font-head);font-size:1.8rem;font-weight:800;color:var(--p1);}
.trust-label{font-size:12px;color:var(--gray);margin-top:2px;}

/* ---- SECTIONS ---- */
.section{padding:5rem 4rem;}
.section-title{text-align:center;margin-bottom:3.5rem;}
.section-title h2{font-family:var(--font-head);font-size:2.2rem;font-weight:800;color:var(--dark);}
.section-title h2 span{color:var(--p1);}
.section-title p{color:var(--gray);margin-top:10px;font-size:15px;max-width:500px;margin-left:auto;margin-right:auto;}
.underline-bar{width:50px;height:4px;background:linear-gradient(90deg,var(--p1),var(--p2));border-radius:2px;margin:14px auto 0;}

/* ---- SERVICES GRID ---- */
.services-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:1.8rem;}
.service-card{background:var(--white);border:1px solid var(--p3);border-radius:24px;padding:2.2rem;text-align:center;cursor:pointer;transition:all 0.4s;position:relative;overflow:hidden;transform-style:preserve-3d;}
.service-card::after{content:'';position:absolute;inset:0;background:linear-gradient(135deg,rgba(123,47,190,0.04),transparent);opacity:0;transition:opacity 0.3s;}
.service-card:hover{transform:translateY(-10px) rotateX(5deg);box-shadow:0 25px 50px rgba(123,47,190,0.14);border-color:var(--p2);}
.service-card:hover::after{opacity:1;}
.svc-icon{width:72px;height:72px;border-radius:22px;margin:0 auto 1.2rem;display:flex;align-items:center;justify-content:center;font-size:30px;transition:transform 0.3s;}
.service-card:hover .svc-icon{transform:scale(1.1) rotateY(15deg);}
.ic-purple{background:linear-gradient(135deg,#e8d5f5,#d7b3ef);}
.ic-green{background:linear-gradient(135deg,#d5f5e3,#a9dfbf);}
.ic-blue{background:linear-gradient(135deg,#d6eaf8,#a9cce3);}
.ic-orange{background:linear-gradient(135deg,#fdebd0,#f5cba7);}
.ic-pink{background:linear-gradient(135deg,#fce4ec,#f8bbd9);}
.ic-teal{background:linear-gradient(135deg,#d1f2eb,#a2d9cc);}
.service-card h3{font-family:var(--font-head);font-size:16px;font-weight:700;color:var(--dark);margin-bottom:10px;}
.service-card p{font-size:13.5px;color:var(--gray);line-height:1.65;}
.arrow-btn{margin-top:1.2rem;background:var(--p3);color:var(--p1);border:none;border-radius:25px;padding:7px 18px;font-size:12px;font-weight:700;cursor:pointer;transition:all 0.2s;font-family:var(--font-body);}
.arrow-btn:hover{background:var(--p1);color:white;}

/* ---- MEDICINE SEARCH ---- */
.search-hero{background:linear-gradient(135deg,var(--dark),var(--dark2));padding:3.5rem 4rem;color:white;position:relative;overflow:hidden;}
.search-hero::before{content:'';position:absolute;right:-50px;top:-50px;width:300px;height:300px;border:1px solid rgba(155,89,182,0.15);border-radius:50%;animation:spinRing 20s linear infinite;}
.search-hero::after{content:'';position:absolute;right:-80px;top:-80px;width:400px;height:400px;border:1px solid rgba(155,89,182,0.08);border-radius:50%;animation:spinRing 30s linear infinite reverse;}
@keyframes spinRing{0%{transform:rotate(0)}100%{transform:rotate(360deg)}}
.search-hero h2{font-family:var(--font-head);font-size:2rem;font-weight:800;margin-bottom:.7rem;}
.search-box{display:flex;gap:12px;max-width:620px;margin-top:1.2rem;}
.search-box input{flex:1;padding:14px 22px;border-radius:35px;border:none;font-size:15px;outline:none;font-family:var(--font-body);box-shadow:0 4px 20px rgba(0,0,0,0.2);}
.search-box button{background:linear-gradient(135deg,var(--p1),var(--p2));color:white;border:none;padding:14px 32px;border-radius:35px;font-weight:700;cursor:pointer;font-family:var(--font-head);transition:all 0.2s;}
.search-box button:hover{transform:scale(1.03);}
.filter-row{display:flex;gap:8px;margin-top:1.2rem;flex-wrap:wrap;}
.filter-chip{background:rgba(255,255,255,0.1);border:1px solid rgba(255,255,255,0.2);color:rgba(255,255,255,0.8);padding:6px 18px;border-radius:25px;font-size:12px;cursor:pointer;transition:all 0.2s;font-weight:500;}
.filter-chip:hover,.filter-chip.active{background:var(--p1);color:white;border-color:var(--p1);}
.medicine-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:1.2rem;padding:2.5rem 4rem;}
.med-card{border:1px solid var(--p3);border-radius:20px;padding:1.3rem;cursor:pointer;transition:all 0.3s;background:white;transform-style:preserve-3d;}
.med-card:hover{border-color:var(--p2);transform:translateY(-6px) rotateX(3deg);box-shadow:0 20px 40px rgba(123,47,190,0.12);}
.med-img{width:100%;height:100px;background:linear-gradient(135deg,var(--p4),#ede4ff);border-radius:14px;display:flex;align-items:center;justify-content:center;font-size:40px;margin-bottom:12px;transition:transform 0.3s;}
.med-card:hover .med-img{transform:scale(1.05) rotateY(10deg);}
.med-name{font-family:var(--font-head);font-weight:700;font-size:14px;color:var(--dark);}
.med-brand{font-size:11px;color:var(--gray);margin-top:2px;}
.med-price{font-family:var(--font-head);font-size:17px;font-weight:800;color:var(--p1);margin-top:8px;}
.med-price .old-price{font-size:12px;color:var(--gray);font-weight:400;text-decoration:line-through;margin-left:4px;}
.med-stock{font-size:11px;padding:3px 10px;border-radius:10px;margin-top:4px;display:inline-block;font-weight:600;}
.in-stock{background:#d5f5e3;color:#1a7a3f;}
.low-stock{background:#fef9e7;color:#8b6914;}
.add-cart{width:100%;margin-top:10px;background:linear-gradient(135deg,var(--p1),var(--p2));color:white;border:none;padding:9px;border-radius:12px;font-size:13px;font-weight:700;cursor:pointer;transition:all 0.25s;font-family:var(--font-body);}
.add-cart:hover{transform:scale(1.02);box-shadow:0 6px 15px rgba(123,47,190,0.3);}

/* ---- DOCTORS ---- */
.doc-hero{background:linear-gradient(135deg,#0f0c29,#302b63);padding:3.5rem 4rem;color:white;position:relative;overflow:hidden;}
.doc-hero h2{font-family:var(--font-head);font-size:2rem;font-weight:800;}
.doc-hero p{opacity:0.65;margin-top:8px;font-size:15px;}
.spec-tabs{display:flex;gap:10px;padding:1.8rem 4rem 0;flex-wrap:wrap;}
.spec-tab{padding:8px 22px;border-radius:25px;border:1px solid var(--p3);font-size:13px;font-weight:600;cursor:pointer;background:white;transition:all 0.2s;font-family:var(--font-body);}
.spec-tab:hover,.spec-tab.active{background:linear-gradient(135deg,var(--p1),var(--p2));color:white;border-color:var(--p1);box-shadow:0 4px 15px rgba(123,47,190,0.3);}
.doctors-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:1.8rem;padding:2.5rem 4rem;}
.doc-card{border:1px solid var(--p3);border-radius:24px;overflow:hidden;background:white;transition:all 0.35s;transform-style:preserve-3d;}
.doc-card:hover{box-shadow:0 20px 50px rgba(123,47,190,0.15);transform:translateY(-8px) rotateX(3deg);}
.doc-banner{height:90px;display:flex;align-items:flex-end;justify-content:center;position:relative;}
.doc-avatar{width:86px;height:86px;border-radius:50%;border:4px solid white;position:absolute;bottom:-43px;font-size:32px;display:flex;align-items:center;justify-content:center;box-shadow:0 8px 20px rgba(0,0,0,0.1);}
.doc-info{padding:3.5rem 1.8rem 1.8rem;text-align:center;}
.doc-name{font-family:var(--font-head);font-size:16px;font-weight:800;color:var(--dark);}
.doc-spec{font-size:12px;color:var(--p1);font-weight:700;margin:4px 0;letter-spacing:0.5px;text-transform:uppercase;}
.doc-rating{display:flex;align-items:center;justify-content:center;gap:5px;font-size:13px;margin:8px 0;}
.stars{color:#f39c12;font-size:14px;}
.doc-meta{display:flex;justify-content:space-around;margin:14px 0;padding:14px;background:var(--p4);border-radius:14px;}
.doc-meta-item{text-align:center;}
.doc-meta-num{font-family:var(--font-head);font-weight:800;font-size:15px;color:var(--p1);}
.doc-meta-label{font-size:10px;color:var(--gray);margin-top:2px;}
.doc-btns{display:flex;gap:8px;margin:10px 0;}
.doc-btns button{flex:1;background:var(--p4);color:var(--p1);border:none;padding:9px;border-radius:12px;font-size:12px;font-weight:700;cursor:pointer;transition:all 0.2s;}
.doc-btns button:hover{background:var(--p3);}
.consult-btn{width:100%;background:linear-gradient(135deg,var(--p1),var(--p2));color:white;border:none;padding:11px;border-radius:14px;font-weight:700;cursor:pointer;font-size:14px;font-family:var(--font-head);transition:all 0.2s;}
.consult-btn:hover{box-shadow:0 8px 20px rgba(123,47,190,0.35);transform:scale(1.01);}

/* ---- HEALTH RECORDS ---- */
.records-layout{display:grid;grid-template-columns:270px 1fr;min-height:82vh;}
.sidebar{background:linear-gradient(180deg,#1a1a2e,#2d1b69);padding:2.5rem 1.5rem;color:white;}
.sidebar h3{font-family:var(--font-head);font-size:11px;text-transform:uppercase;letter-spacing:2.5px;opacity:0.4;margin-bottom:1rem;}
.sidebar-item{display:flex;align-items:center;gap:12px;padding:11px 16px;border-radius:14px;cursor:pointer;font-size:14px;margin-bottom:4px;transition:all 0.2s;font-weight:500;}
.sidebar-item:hover,.sidebar-item.active{background:rgba(155,89,182,0.25);border:1px solid rgba(155,89,182,0.2);}
.sicon{font-size:16px;width:22px;text-align:center;}
.records-main{padding:3rem;}
.records-header{display:flex;justify-content:space-between;align-items:center;margin-bottom:2.5rem;}
.records-header h2{font-family:var(--font-head);font-size:1.6rem;font-weight:800;}
.health-cards{display:grid;grid-template-columns:repeat(4,1fr);gap:1rem;margin-bottom:2.5rem;}
.health-metric{border:1px solid var(--p3);border-radius:18px;padding:1.3rem;background:white;transition:transform 0.3s;}
.health-metric:hover{transform:translateY(-4px);box-shadow:0 10px 25px rgba(123,47,190,0.1);}
.metric-label{font-size:12px;color:var(--gray);display:flex;align-items:center;gap:6px;font-weight:500;}
.metric-val{font-family:var(--font-head);font-size:1.7rem;font-weight:800;color:var(--dark);margin:8px 0;}
.metric-unit{font-size:13px;color:var(--gray);font-weight:400;}
.metric-status{font-size:11px;padding:3px 12px;border-radius:12px;font-weight:700;}
.normal{background:#d5f5e3;color:#1a7a3f;}
.high{background:#fdedec;color:#a93226;}
.rx-table{width:100%;border-collapse:collapse;font-size:14px;}
.rx-table th{background:var(--p4);padding:13px 18px;text-align:left;font-size:11px;text-transform:uppercase;letter-spacing:1.5px;color:var(--gray);font-weight:700;}
.rx-table td{padding:14px 18px;border-bottom:1px solid var(--p3);}
.rx-table tr:hover td{background:var(--p4);}
.status-badge{padding:4px 14px;border-radius:20px;font-size:11px;font-weight:700;}
.active-badge{background:#d5f5e3;color:#1a7a3f;}
.expired-badge{background:#fde8d8;color:#8b2500;}

/* ---- REMINDER ---- */
.reminder-layout{display:grid;grid-template-columns:1fr 400px;min-height:82vh;}
.reminder-main{padding:3rem;}
.reminder-top{display:flex;justify-content:space-between;align-items:center;margin-bottom:2rem;}
.reminder-top h2{font-family:var(--font-head);font-size:1.6rem;font-weight:800;}
.compliance-card{background:linear-gradient(135deg,var(--p1),var(--p2));border-radius:18px;padding:14px 20px;text-align:center;color:white;}
.compliance-card .c-label{font-size:11px;opacity:0.8;text-transform:uppercase;letter-spacing:1px;}
.compliance-card .c-val{font-family:var(--font-head);font-size:2rem;font-weight:800;}
.reminder-sidebar{background:var(--p4);padding:2.5rem;border-left:1px solid var(--p3);}
.timeline{position:relative;margin-top:1.5rem;}
.timeline::before{content:'';position:absolute;left:19px;top:0;bottom:0;width:2px;background:linear-gradient(180deg,var(--p3),transparent);}
.tl-item{display:flex;gap:18px;margin-bottom:1.8rem;position:relative;}
.tl-dot{width:42px;height:42px;border-radius:50%;border:3px solid var(--p3);background:white;display:flex;align-items:center;justify-content:center;font-size:16px;flex-shrink:0;z-index:1;box-shadow:0 4px 10px rgba(0,0,0,0.08);}
.tl-dot.taken{border-color:var(--success);background:linear-gradient(135deg,var(--success),#2ecc71);}
.tl-dot.upcoming{border-color:var(--p1);background:linear-gradient(135deg,var(--p4),var(--p3));}
.tl-dot.missed{border-color:var(--danger);background:linear-gradient(135deg,#fdedec,#f5b7b1);}
.tl-content{background:white;border:1px solid var(--p3);border-radius:18px;padding:1rem 1.3rem;flex:1;transition:all 0.25s;}
.tl-content:hover{box-shadow:0 8px 20px rgba(123,47,190,0.08);transform:translateX(4px);}
.tl-time{font-size:11px;color:var(--gray);font-weight:500;}
.tl-med{font-family:var(--font-head);font-weight:700;font-size:14px;color:var(--dark);}
.tl-dose{font-size:12px;color:var(--gray);margin-top:2px;}
.tl-header{display:flex;justify-content:space-between;align-items:start;}
.tl-tag{font-size:11px;padding:3px 12px;border-radius:12px;font-weight:700;white-space:nowrap;}
.tag-taken{background:#d5f5e3;color:#1a7a3f;}
.tag-upcoming{background:var(--p3);color:var(--p1);}
.tag-missed{background:#fdedec;color:#a93226;}
.add-reminder-form{background:white;border:1px solid var(--p3);border-radius:22px;padding:1.8rem;}
.add-reminder-form h4{font-family:var(--font-head);font-size:15px;font-weight:800;margin-bottom:1.2rem;color:var(--dark);}
.form-row{margin-bottom:14px;}
.form-row label{font-size:12px;color:var(--gray);display:block;margin-bottom:5px;font-weight:600;text-transform:uppercase;letter-spacing:0.5px;}
.form-row input,.form-row select{width:100%;padding:11px 16px;border:1.5px solid var(--p3);border-radius:12px;font-size:13px;outline:none;font-family:var(--font-body);transition:border-color 0.2s;}
.form-row input:focus,.form-row select:focus{border-color:var(--p1);}
.weekly-summary{margin-top:1.5rem;background:white;border:1px solid var(--p3);border-radius:18px;padding:1.3rem;}
.weekly-summary h4{font-family:var(--font-head);font-size:14px;font-weight:800;margin-bottom:12px;color:var(--dark);}
.weekly-grid{display:grid;grid-template-columns:1fr 1fr 1fr;gap:8px;text-align:center;}
.w-item{border-radius:12px;padding:10px 6px;}
.w-item .w-num{font-family:var(--font-head);font-size:1.4rem;font-weight:800;}
.w-item .w-label{font-size:10px;color:var(--gray);margin-top:2px;}
.w-taken{background:var(--p4);}
.w-taken .w-num{color:var(--p1);}
.w-missed{background:#fdedec;}
.w-missed .w-num{color:var(--danger);}
.w-pending{background:#fef9e7;}
.w-pending .w-num{color:var(--warn);}

/* ---- ABOUT ---- */
.about-hero{background:linear-gradient(135deg,#0f0c29,#302b63,#4a1b8a);padding:5rem 4rem;color:white;text-align:center;position:relative;overflow:hidden;}
.about-hero h1{font-family:var(--font-head);font-size:2.8rem;font-weight:800;margin-bottom:1.2rem;}
.about-hero p{font-size:1.1rem;opacity:0.7;max-width:580px;margin:0 auto;line-height:1.7;}
.about-grid{display:grid;grid-template-columns:1fr 1fr;gap:5rem;padding:5rem 4rem;align-items:center;}
.about-visual{border-radius:28px;height:400px;background:linear-gradient(135deg,var(--p4),#ede4ff);display:flex;align-items:center;justify-content:center;font-size:100px;border:2px dashed var(--p3);position:relative;overflow:hidden;}
.about-visual::before{content:'';position:absolute;inset:0;background:linear-gradient(135deg,rgba(123,47,190,0.05),transparent);}
.about-content h2{font-family:var(--font-head);font-size:1.9rem;font-weight:800;color:var(--dark);margin-bottom:1.2rem;}
.about-content h2 span{color:var(--p1);}
.about-content p{color:var(--gray);line-height:1.85;margin-bottom:1rem;font-size:15px;}
.feature-list{list-style:none;margin-top:1.2rem;}
.feature-list li{display:flex;align-items:center;gap:12px;font-size:14px;color:var(--dark);padding:7px 0;font-weight:500;}
.fc-check{width:22px;height:22px;background:linear-gradient(135deg,var(--p1),var(--p2));border-radius:50%;display:flex;align-items:center;justify-content:center;color:white;font-size:11px;flex-shrink:0;}
.team-section{padding:5rem 4rem;background:var(--p4);}
.team-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:1.5rem;margin-top:2.5rem;}
.team-card{background:white;border-radius:22px;padding:1.8rem;text-align:center;border:1px solid var(--p3);transition:all 0.3s;}
.team-card:hover{transform:translateY(-8px);box-shadow:0 20px 40px rgba(123,47,190,0.12);}
.team-avatar{width:80px;height:80px;border-radius:50%;margin:0 auto 14px;font-size:32px;display:flex;align-items:center;justify-content:center;border:3px solid var(--p3);}
.team-name{font-family:var(--font-head);font-weight:800;font-size:15px;color:var(--dark);}
.team-role{font-size:12px;color:var(--p1);font-weight:600;margin-top:3px;}
.team-bio{font-size:12px;color:var(--gray);margin-top:8px;line-height:1.5;}
.contact-section{padding:5rem 4rem;display:grid;grid-template-columns:1fr 1fr;gap:4rem;}
.contact-form-wrap h2{font-family:var(--font-head);font-size:1.6rem;font-weight:800;margin-bottom:1.8rem;}
.contact-input{width:100%;padding:13px 18px;border:1.5px solid var(--p3);border-radius:14px;font-size:14px;margin-bottom:14px;outline:none;font-family:var(--font-body);transition:border-color 0.2s;}
.contact-input:focus{border-color:var(--p1);}
.contact-textarea{height:130px;resize:none;}
.contact-info h2{font-family:var(--font-head);font-size:1.6rem;font-weight:800;margin-bottom:1.8rem;}
.contact-item{display:flex;align-items:flex-start;gap:16px;margin-bottom:1.8rem;}
.cicon{width:48px;height:48px;border-radius:14px;background:linear-gradient(135deg,var(--p3),var(--p4));display:flex;align-items:center;justify-content:center;font-size:20px;flex-shrink:0;}
.cdetail-title{font-family:var(--font-head);font-weight:700;font-size:14px;color:var(--dark);}
.cdetail-sub{font-size:13px;color:var(--gray);margin-top:3px;line-height:1.6;}
.map-placeholder{background:linear-gradient(135deg,var(--p4),#ede4ff);border-radius:20px;height:180px;margin-top:1.5rem;display:flex;align-items:center;justify-content:center;font-size:44px;border:2px dashed var(--p3);}

/* ---- FOOTER ---- */
.footer{background:linear-gradient(135deg,#0f0c29,#1a1a2e);color:rgba(255,255,255,0.65);padding:4rem;display:grid;grid-template-columns:2fr 1fr 1fr 1fr;gap:3rem;}
.footer-brand h3{font-family:var(--font-head);font-size:20px;color:white;font-weight:800;margin-bottom:10px;}
.footer-brand p{font-size:13px;line-height:1.8;}
.social-row{display:flex;gap:10px;margin-top:1.5rem;}
.social-btn{background:rgba(255,255,255,0.08);border:1px solid rgba(255,255,255,0.1);padding:7px 14px;border-radius:20px;font-size:12px;color:rgba(255,255,255,0.7);cursor:pointer;transition:all 0.2s;}
.social-btn:hover{background:rgba(155,89,182,0.3);}
.footer-col h4{font-family:var(--font-head);font-size:12px;color:white;font-weight:700;text-transform:uppercase;letter-spacing:2px;margin-bottom:16px;}
.footer-col ul{list-style:none;}
.footer-col ul li{font-size:13px;margin-bottom:9px;cursor:pointer;transition:color 0.2s;}
.footer-col ul li:hover{color:white;}
.footer-bottom{background:#0a0a1a;color:rgba(255,255,255,0.35);padding:1.2rem 4rem;display:flex;justify-content:space-between;font-size:12px;align-items:center;}

/* ---- TOAST ---- */
.toast{position:fixed;bottom:2rem;right:2rem;background:linear-gradient(135deg,var(--p1),var(--p2));color:white;padding:12px 24px;border-radius:35px;font-size:14px;font-weight:600;z-index:9999;transform:translateY(100px);opacity:0;transition:all 0.35s;box-shadow:0 10px 30px rgba(123,47,190,0.4);font-family:var(--font-body);}
.toast.show{transform:translateY(0);opacity:1;}

/* ---- WHY SECTION ---- */
.why-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:1.5rem;margin-top:2rem;}
.why-item{text-align:center;padding:2rem;border:1px solid var(--p3);border-radius:20px;background:white;transition:all 0.3s;}
.why-item:hover{transform:translateY(-6px);box-shadow:0 15px 35px rgba(123,47,190,0.1);}
.why-icon{font-size:44px;margin-bottom:14px;}
.why-title{font-family:var(--font-head);font-weight:700;font-size:15px;color:var(--dark);}
.why-desc{font-size:13px;color:var(--gray);margin-top:8px;line-height:1.6;}

/* CTA SECTION */
.cta-section{background:linear-gradient(135deg,var(--p1),var(--dark2));padding:5rem 4rem;text-align:center;color:white;}
.cta-section h2{font-family:var(--font-head);font-size:2.2rem;font-weight:800;margin-bottom:12px;}
.cta-section p{opacity:0.75;font-size:15px;margin-bottom:2.5rem;}
.cta-btns{display:flex;gap:1rem;justify-content:center;flex-wrap:wrap;}
.cta-btn1{background:white;color:var(--p1);padding:15px 36px;border-radius:35px;border:none;font-size:15px;font-weight:700;cursor:pointer;font-family:var(--font-head);transition:all 0.3s;}
.cta-btn1:hover{transform:translateY(-3px);box-shadow:0 10px 25px rgba(0,0,0,0.2);}
.cta-btn2{background:transparent;color:white;padding:15px 36px;border-radius:35px;border:2px solid rgba(255,255,255,0.3);font-size:15px;font-weight:600;cursor:pointer;font-family:var(--font-body);transition:all 0.3s;}
.cta-btn2:hover{background:rgba(255,255,255,0.1);}
</style>
</head>
<body>

<canvas id="particles-canvas"></canvas>
<div class="toast" id="toast"></div>

<!-- NAV -->
<nav class="nav" id="navbar">
  <a class="logo" href="#">
    <div class="logo-cube">
      <div class="cube-inner">
        <div class="cube-face cube-f">💊</div>
        <div class="cube-face cube-b">⚕</div>
        <div class="cube-face cube-l">🏥</div>
        <div class="cube-face cube-r">💉</div>
      </div>
    </div>
    <div class="logo-text-wrap">
      <div class="logo-name">PharmaCore</div>
      <div class="logo-tagline">Your Health, Our Priority</div>
    </div>
  </a>
  <ul class="nav-links">
    <li><a onclick="showPage('home')" class="active" id="nav-home">Home</a></li>
    <li><a onclick="showPage('medicines')" id="nav-medicines">Medicines</a></li>
    <li><a onclick="showPage('doctors')" id="nav-doctors">Doctors</a></li>
    <li><a onclick="showPage('records')" id="nav-records">Health Records</a></li>
    <li><a onclick="showPage('reminder')" id="nav-reminder">Reminders</a></li>
    <li><a onclick="showPage('about')" id="nav-about">About & Contact</a></li>
  </ul>
  <div class="nav-right">
    <button class="btn btn-outline" onclick="showPage('medicines')">🛒 Cart <span class="cart-badge" id="cart-count">0</span></button>
    <button class="btn btn-primary">Sign In</button>
  </div>
</nav>

<!-- =================== HOME PAGE =================== -->
<div class="page active" id="page-home">
  <div class="hero">
    <div class="hero-bg-orb orb1"></div>
    <div class="hero-bg-orb orb2"></div>
    <div class="hero-content">
      <div class="hero-badge"><span class="pulse-dot"></span> India's Trusted Digital Pharmacy Platform</div>
      <h1>Your Complete <span class="accent">Health Solution</span>, All in One Place</h1>
      <p>Order medicines, consult certified doctors, track your health records, and never miss a dose — all from PharmaCore, your intelligent pharmacy companion.</p>
      <div class="hero-btns">
        <button class="hero-btn-main" onclick="showPage('medicines')">🔍 Search Medicines</button>
        <button class="hero-btn-sec" onclick="showPage('doctors')">👨‍⚕️ Consult a Doctor</button>
      </div>
    </div>
    <div class="hero-3d-cluster">
      <div class="floating-card">
        <div class="fc-label">Medicines Available</div>
        <div class="fc-value">50,000+</div>
        <div class="fc-sub">Genuine & licensed</div>
        <span class="fc-icon">💊</span>
      </div>
      <div class="floating-card">
        <div class="fc-label">Verified Doctors</div>
        <div class="fc-value">1,200+</div>
        <div class="fc-sub">Available 24/7</div>
        <span class="fc-icon">🩺</span>
      </div>
      <div class="floating-card">
        <div class="fc-label">Happy Patients</div>
        <div class="fc-value">2M+</div>
        <div class="fc-sub">98% satisfaction rate</div>
        <span class="fc-icon">💚</span>
      </div>
    </div>
  </div>

  <div class="trust-bar">
    <div class="trust-item"><div class="trust-num">50K+</div><div class="trust-label">Medicines</div></div>
    <div class="trust-item"><div class="trust-num">1,200+</div><div class="trust-label">Doctors</div></div>
    <div class="trust-item"><div class="trust-num">2M+</div><div class="trust-label">Patients</div></div>
    <div class="trust-item"><div class="trust-num">24/7</div><div class="trust-label">Support</div></div>
    <div class="trust-item"><div class="trust-num">100%</div><div class="trust-label">Genuine</div></div>
    <div class="trust-item"><div class="trust-num">2–4hr</div><div class="trust-label">Delivery</div></div>
  </div>

  <div class="section">
    <div class="section-title">
      <h2>Our <span>Services</span></h2>
      <p>Everything you need for your health journey — all in one platform</p>
      <div class="underline-bar"></div>
    </div>
    <div class="services-grid">
      <div class="service-card" onclick="showPage('medicines')">
        <div class="svc-icon ic-purple">💊</div>
        <h3>Medicine Ordering</h3>
        <p>Search from 50,000+ genuine medicines with 2-hour express doorstep delivery.</p>
        <button class="arrow-btn">Explore →</button>
      </div>
      <div class="service-card" onclick="showPage('doctors')">
        <div class="svc-icon ic-green">🩺</div>
        <h3>Doctor Consultation</h3>
        <p>Connect with 1200+ certified specialists via video, audio, or chat — instantly.</p>
        <button class="arrow-btn">Consult →</button>
      </div>
      <div class="service-card" onclick="showPage('records')">
        <div class="svc-icon ic-blue">📋</div>
        <h3>Health Records</h3>
        <p>Store all prescriptions, lab reports, and vitals securely in one place.</p>
        <button class="arrow-btn">View →</button>
      </div>
      <div class="service-card" onclick="showPage('reminder')">
        <div class="svc-icon ic-orange">⏰</div>
        <h3>Medicine Reminders</h3>
        <p>Smart daily reminders and compliance tracking — never miss a dose again.</p>
        <button class="arrow-btn">Set Reminder →</button>
      </div>
      <div class="service-card">
        <div class="svc-icon ic-pink">🧪</div>
        <h3>Lab Tests</h3>
        <p>Book 500+ lab tests at home with certified collection agents and online reports.</p>
        <button class="arrow-btn">Book Test →</button>
      </div>
      <div class="service-card">
        <div class="svc-icon ic-teal">🏥</div>
        <h3>Health Packages</h3>
        <p>Comprehensive annual health packages for individuals and families at best prices.</p>
        <button class="arrow-btn">View Packages →</button>
      </div>
    </div>
  </div>

  <div class="section" style="background:var(--p4);padding-top:4rem;padding-bottom:4rem;">
    <div class="section-title">
      <h2>Why Choose <span>PharmaCore?</span></h2>
      <div class="underline-bar"></div>
    </div>
    <div class="why-grid">
      <div class="why-item"><div class="why-icon">✅</div><div class="why-title">100% Genuine</div><div class="why-desc">All medicines sourced directly from licensed manufacturers with full quality checks.</div></div>
      <div class="why-item"><div class="why-icon">🔒</div><div class="why-title">Secure & Private</div><div class="why-desc">Your health data is HIPAA-compliant, encrypted end-to-end, and never shared.</div></div>
      <div class="why-item"><div class="why-icon">⚡</div><div class="why-title">Fast Delivery</div><div class="why-desc">Express 2-hour delivery available in 100+ cities across India.</div></div>
      <div class="why-item"><div class="why-icon">💬</div><div class="why-title">24/7 Support</div><div class="why-desc">Expert pharmacists and customer support available round the clock.</div></div>
    </div>
  </div>

  <div class="cta-section">
    <h2>Ready to Take Control of Your Health?</h2>
    <p>Join 2 million+ patients who trust PharmaCore for their healthcare needs</p>
    <div class="cta-btns">
      <button class="cta-btn1" onclick="showPage('medicines')">Start Ordering Medicines</button>
      <button class="cta-btn2" onclick="showPage('doctors')">Book a Consultation</button>
    </div>
  </div>
</div>

<!-- =================== MEDICINES PAGE =================== -->
<div class="page" id="page-medicines">
  <div class="search-hero">
    <h2>🔍 Search & Order Medicines</h2>
    <p style="opacity:0.7;margin-top:6px;">50,000+ genuine medicines — delivered in 2–4 hours</p>
    <div class="search-box">
      <input type="text" id="med-search" placeholder="Search medicines, brands, compositions..." oninput="filterMeds()"/>
      <button onclick="filterMeds()">Search</button>
    </div>
    <div class="filter-row">
      <span class="filter-chip active" onclick="setFilter('All',this)">All Categories</span>
      <span class="filter-chip" onclick="setFilter('Antibiotic',this)">💉 Antibiotics</span>
      <span class="filter-chip" onclick="setFilter('Painkiller',this)">💊 Painkillers</span>
      <span class="filter-chip" onclick="setFilter('Vitamin',this)">☀️ Vitamins</span>
      <span class="filter-chip" onclick="setFilter('Cardiac',this)">❤️ Cardiac</span>
      <span class="filter-chip" onclick="setFilter('Diabetes',this)">🩺 Diabetes</span>
      <span class="filter-chip" onclick="setFilter('Antiallergy',this)">🌸 Antiallergy</span>
    </div>
  </div>
  <div class="medicine-grid" id="med-grid"></div>
</div>

<!-- =================== DOCTORS PAGE =================== -->
<div class="page" id="page-doctors">
  <div class="doc-hero">
    <h2>👨‍⚕️ Consult Certified Doctors</h2>
    <p>Instant consultations with 1200+ verified specialists — video, audio, or chat</p>
  </div>
  <div class="spec-tabs">
    <span class="spec-tab active" onclick="setDocFilter('All',this)">All Specialists</span>
    <span class="spec-tab" onclick="setDocFilter('Cardiologist',this)">❤️ Cardiology</span>
    <span class="spec-tab" onclick="setDocFilter('Dermatologist',this)">🧴 Dermatology</span>
    <span class="spec-tab" onclick="setDocFilter('Neurologist',this)">🧠 Neurology</span>
    <span class="spec-tab" onclick="setDocFilter('Orthopedic',this)">🦴 Orthopedic</span>
    <span class="spec-tab" onclick="setDocFilter('Pediatrician',this)">👶 Pediatrics</span>
  </div>
  <div class="doctors-grid" id="doc-grid"></div>
</div>

<!-- =================== HEALTH RECORDS PAGE =================== -->
<div class="page" id="page-records">
  <div class="records-layout">
    <div class="sidebar">
      <h3>My Health</h3>
      <div class="sidebar-item active"><span class="sicon">📊</span> Overview</div>
      <div class="sidebar-item"><span class="sicon">💊</span> Prescriptions</div>
      <div class="sidebar-item"><span class="sicon">🧪</span> Lab Reports</div>
      <div class="sidebar-item"><span class="sicon">🩺</span> Consultations</div>
      <div class="sidebar-item"><span class="sicon">📁</span> Documents</div>
      <div style="margin-top:3rem;">
        <h3>Settings</h3>
        <div class="sidebar-item"><span class="sicon">👤</span> Profile</div>
        <div class="sidebar-item"><span class="sicon">🔔</span> Notifications</div>
        <div class="sidebar-item"><span class="sicon">🔒</span> Privacy</div>
        <div class="sidebar-item"><span class="sicon">🚪</span> Sign Out</div>
      </div>
    </div>
    <div class="records-main">
      <div class="records-header">
        <div>
          <h2>Health Overview</h2>
          <p style="color:var(--gray);font-size:13px;margin-top:4px;">Last updated: April 8, 2026</p>
        </div>
        <button class="btn btn-primary">+ Upload Record</button>
      </div>
      <div class="health-cards">
        <div class="health-metric"><div class="metric-label">❤️ Blood Pressure</div><div class="metric-val">120<span class="metric-unit">/80</span></div><span class="metric-status normal">Normal</span></div>
        <div class="health-metric"><div class="metric-label">🩸 Blood Sugar</div><div class="metric-val">145<span class="metric-unit">mg/dL</span></div><span class="metric-status high">Elevated</span></div>
        <div class="health-metric"><div class="metric-label">⚖️ BMI</div><div class="metric-val">24.2</div><span class="metric-status normal">Normal</span></div>
        <div class="health-metric"><div class="metric-label">💊 Active Rx</div><div class="metric-val">3</div><span class="metric-status normal">On Track</span></div>
      </div>
      <h3 style="font-family:var(--font-head);font-size:15px;font-weight:800;margin-bottom:1.2rem;color:var(--dark);">Active Prescriptions</h3>
      <table class="rx-table">
        <thead><tr><th>Medicine</th><th>Prescribed By</th><th>Dosage</th><th>Duration</th><th>Status</th></tr></thead>
        <tbody>
          <tr><td><strong>Metformin 500mg</strong><br><span style="font-size:11px;color:var(--gray);">Diabetes</span></td><td>Dr. Priya Sharma</td><td>Twice daily</td><td>3 months</td><td><span class="status-badge active-badge">Active</span></td></tr>
          <tr><td><strong>Amlodipine 5mg</strong><br><span style="font-size:11px;color:var(--gray);">Hypertension</span></td><td>Dr. Rajan Mehta</td><td>Once daily</td><td>Ongoing</td><td><span class="status-badge active-badge">Active</span></td></tr>
          <tr><td><strong>Atorvastatin 20mg</strong><br><span style="font-size:11px;color:var(--gray);">Cholesterol</span></td><td>Dr. Priya Sharma</td><td>Once nightly</td><td>6 months</td><td><span class="status-badge active-badge">Active</span></td></tr>
          <tr><td><strong>Amoxicillin 500mg</strong><br><span style="font-size:11px;color:var(--gray);">Antibiotic</span></td><td>Dr. Kavita Nair</td><td>Thrice daily</td><td>7 days</td><td><span class="status-badge expired-badge">Completed</span></td></tr>
        </tbody>
      </table>
    </div>
  </div>
</div>

<!-- =================== REMINDER PAGE =================== -->
<div class="page" id="page-reminder">
  <div class="reminder-layout">
    <div class="reminder-main">
      <div class="reminder-top">
        <div><h2>⏰ Medicine Reminders</h2><p style="color:var(--gray);font-size:13px;margin-top:5px;">Wednesday, April 8, 2026</p></div>
        <div class="compliance-card"><div class="c-label">Compliance</div><div class="c-val">87%</div></div>
      </div>
      <div class="timeline">
        <div class="tl-item">
          <div class="tl-dot taken" style="color:white;font-weight:700;">✓</div>
          <div class="tl-content"><div class="tl-header"><div><div class="tl-time">06:00 AM — Morning</div><div class="tl-med">Metformin 500mg</div><div class="tl-dose">1 tablet with breakfast</div></div><span class="tl-tag tag-taken">Taken</span></div></div>
        </div>
        <div class="tl-item">
          <div class="tl-dot taken" style="color:white;font-weight:700;">✓</div>
          <div class="tl-content"><div class="tl-header"><div><div class="tl-time">08:00 AM — Morning</div><div class="tl-med">Amlodipine 5mg</div><div class="tl-dose">1 tablet with water</div></div><span class="tl-tag tag-taken">Taken</span></div></div>
        </div>
        <div class="tl-item">
          <div class="tl-dot upcoming">⏰</div>
          <div class="tl-content"><div class="tl-header"><div><div class="tl-time">02:00 PM — Afternoon</div><div class="tl-med">Metformin 500mg</div><div class="tl-dose">1 tablet after lunch</div></div><span class="tl-tag tag-upcoming">Upcoming</span></div></div>
        </div>
        <div class="tl-item">
          <div class="tl-dot missed" style="color:#a93226;font-weight:700;">!</div>
          <div class="tl-content"><div class="tl-header"><div><div class="tl-time">Yesterday 10:00 PM</div><div class="tl-med">Atorvastatin 20mg</div><div class="tl-dose">1 tablet at bedtime</div></div><span class="tl-tag tag-missed">Missed</span></div></div>
        </div>
        <div class="tl-item">
          <div class="tl-dot upcoming">🌙</div>
          <div class="tl-content"><div class="tl-header"><div><div class="tl-time">10:00 PM — Night</div><div class="tl-med">Atorvastatin 20mg</div><div class="tl-dose">1 tablet at bedtime</div></div><span class="tl-tag tag-upcoming">Tonight</span></div></div>
        </div>
      </div>
    </div>
    <div class="reminder-sidebar">
      <div class="add-reminder-form">
        <h4>+ Add New Reminder</h4>
        <div class="form-row"><label>Medicine Name</label><input type="text" placeholder="e.g. Paracetamol 500mg"/></div>
        <div class="form-row"><label>Dosage</label><input type="text" placeholder="e.g. 1 tablet"/></div>
        <div class="form-row"><label>Frequency</label><select><option>Once daily</option><option>Twice daily</option><option>Thrice daily</option><option>Weekly</option></select></div>
        <div class="form-row"><label>First Reminder Time</label><input type="time" value="08:00"/></div>
        <div class="form-row"><label>Start Date</label><input type="date" value="2026-04-08"/></div>
        <button class="btn btn-primary" style="width:100%;padding:13px;font-size:14px;" onclick="showToast('✅ Reminder set successfully!')">Set Reminder</button>
      </div>
      <div class="weekly-summary">
        <h4>📅 This Week Summary</h4>
        <div class="weekly-grid">
          <div class="w-item w-taken"><div class="w-num">18</div><div class="w-label">Taken</div></div>
          <div class="w-item w-missed"><div class="w-num">2</div><div class="w-label">Missed</div></div>
          <div class="w-item w-pending"><div class="w-num">3</div><div class="w-label">Pending</div></div>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- =================== ABOUT PAGE =================== -->
<div class="page" id="page-about">
  <div class="about-hero">
    <h1>About PharmaCore</h1>
    <p>Revolutionizing healthcare access with technology, compassion, and trust since 2020.</p>
  </div>
  <div class="about-grid">
    <div class="about-visual">🏥</div>
    <div class="about-content">
      <h2>Transforming <span>Healthcare</span> in India</h2>
      <p>PharmaCore was founded with a singular vision: to make quality healthcare accessible to every Indian, regardless of geography or economic status. We combine AI-driven technology with genuine medical expertise.</p>
      <p>From remote villages to metro cities, PharmaCore ensures you have access to genuine medicines, expert doctors, and complete health management — all at your fingertips.</p>
      <ul class="feature-list">
        <li><span class="fc-check">✔</span> Licensed by Central Drugs Standard Control Organization (CDSCO)</li>
        <li><span class="fc-check">✔</span> ISO 9001:2015 Certified Quality Management</li>
        <li><span class="fc-check">✔</span> HIPAA-compliant health data security</li>
        <li><span class="fc-check">✔</span> Partnered with 500+ hospitals and clinics nationwide</li>
        <li><span class="fc-check">✔</span> 1200+ verified and licensed medical professionals</li>
      </ul>
    </div>
  </div>
  <div class="team-section">
    <div class="section-title">
      <h2>Meet Our <span>Leadership</span></h2>
      <div class="underline-bar"></div>
    </div>
    <div class="team-grid">
      <div class="team-card"><div class="team-avatar" style="background:var(--p3);">👨‍💼</div><div class="team-name">Arjun Krishnamurthy</div><div class="team-role">CEO & Co-Founder</div><div class="team-bio">15+ years in healthcare technology and digital health innovation.</div></div>
      <div class="team-card"><div class="team-avatar" style="background:#d5f5e3;">👩‍⚕️</div><div class="team-name">Dr. Priya Venkataraman</div><div class="team-role">Chief Medical Officer</div><div class="team-bio">MBBS, MD — 20 years clinical experience in internal medicine.</div></div>
      <div class="team-card"><div class="team-avatar" style="background:#d6eaf8;">👨‍💻</div><div class="team-name">Karthik Sundaram</div><div class="team-role">CTO & Co-Founder</div><div class="team-bio">Ex-Google engineer, IIT Madras alumnus, AI/ML specialist.</div></div>
      <div class="team-card"><div class="team-avatar" style="background:#fde8d8;">👩‍💼</div><div class="team-name">Meena Raghunathan</div><div class="team-role">Chief Pharmacist</div><div class="team-bio">PharmD, 18 years in pharmacy management and drug safety.</div></div>
    </div>
  </div>
  <div class="contact-section">
    <div class="contact-form-wrap">
      <h2>Get in Touch</h2>
      <input class="contact-input" type="text" placeholder="Your Full Name"/>
      <input class="contact-input" type="email" placeholder="Email Address"/>
      <input class="contact-input" type="tel" placeholder="Phone Number"/>
      <select class="contact-input"><option>General Inquiry</option><option>Medicine Order Support</option><option>Doctor Consultation</option><option>Technical Issue</option><option>Partnership</option></select>
      <textarea class="contact-input contact-textarea" placeholder="Write your message here..."></textarea>
      <button class="btn btn-primary" style="padding:13px 36px;font-size:15px;" onclick="showToast('✅ Message sent! We will respond within 24 hours.')">Send Message →</button>
    </div>
    <div class="contact-info">
      <h2>Contact Information</h2>
      <div class="contact-item"><div class="cicon">📍</div><div><div class="cdetail-title">Head Office</div><div class="cdetail-sub">No. 42, Anna Salai, Chennai, Tamil Nadu 600002</div></div></div>
      <div class="contact-item"><div class="cicon">📞</div><div><div class="cdetail-title">Customer Support</div><div class="cdetail-sub">1800-PH-CORE (Toll Free)<br>Mon–Sun, 6 AM – 12 AM</div></div></div>
      <div class="contact-item"><div class="cicon">✉️</div><div><div class="cdetail-title">Email</div><div class="cdetail-sub">support@pharmacore.in<br>partnerships@pharmacore.in</div></div></div>
      <div class="contact-item"><div class="cicon">🚑</div><div><div class="cdetail-title">Emergency Helpline</div><div class="cdetail-sub">+91-44-9999-0000 (24/7)</div></div></div>
      <div class="map-placeholder">🗺️</div>
    </div>
  </div>
  <div class="footer">
    <div class="footer-brand">
      <h3>🏥 PharmaCore</h3>
      <p>India's most trusted digital pharmacy and healthcare platform. Genuine medicines, certified doctors, and complete health management at your fingertips.</p>
      <div class="social-row">
        <span class="social-btn">📘 Facebook</span>
        <span class="social-btn">🐦 Twitter</span>
        <span class="social-btn">📸 Instagram</span>
      </div>
    </div>
    <div class="footer-col"><h4>Services</h4><ul><li onclick="showPage('medicines')">Buy Medicines</li><li onclick="showPage('doctors')">Consult Doctor</li><li>Lab Tests</li><li onclick="showPage('reminder')">Reminders</li><li>Health Packages</li></ul></div>
    <div class="footer-col"><h4>Company</h4><ul><li onclick="showPage('about')">About Us</li><li>Careers</li><li>Press</li><li>Blog</li><li>Investors</li></ul></div>
    <div class="footer-col"><h4>Support</h4><ul><li>Help Center</li><li>Track Order</li><li>Return Policy</li><li>Privacy Policy</li><li onclick="showPage('about')">Contact Us</li></ul></div>
  </div>
  <div class="footer-bottom">
    <span>© 2026 PharmaCore Pvt. Ltd. All rights reserved. Licensed by CDSCO.</span>
    <span>🔒 SSL Secured &nbsp;|&nbsp; ✅ ISO Certified &nbsp;|&nbsp; 🏥 CDSCO Licensed</span>
  </div>
</div>

<script>
// ---- DATA ----
let cartCount = 0;
let currentMedFilter = 'All';
let currentDocFilter = 'All';

const medicines = [
  {name:'Paracetamol 500mg',brand:'Calpol',price:32,cat:'Painkiller',emoji:'💊',stock:'in-stock',label:'In Stock'},
  {name:'Amoxicillin 500mg',brand:'Mox 500',price:89,cat:'Antibiotic',emoji:'💉',stock:'in-stock',label:'In Stock'},
  {name:'Cetirizine 10mg',brand:'Zyrtec',price:45,cat:'Antiallergy',emoji:'🌿',stock:'in-stock',label:'In Stock'},
  {name:'Metformin 500mg',brand:'Glucophage',price:65,cat:'Diabetes',emoji:'🩺',stock:'in-stock',label:'In Stock'},
  {name:'Vitamin D3 60K',brand:'D-Rise',price:120,cat:'Vitamin',emoji:'☀️',stock:'low-stock',label:'Low Stock'},
  {name:'Amlodipine 5mg',brand:'Amlode',price:78,cat:'Cardiac',emoji:'❤️',stock:'in-stock',label:'In Stock'},
  {name:'Aspirin 75mg',brand:'Ecosprin',price:28,cat:'Cardiac',emoji:'🫀',stock:'in-stock',label:'In Stock'},
  {name:'Pantoprazole 40mg',brand:'Pan-D',price:95,cat:'Painkiller',emoji:'💊',stock:'in-stock',label:'In Stock'},
  {name:'Vitamin B12',brand:'Neurobion',price:145,cat:'Vitamin',emoji:'🧴',stock:'in-stock',label:'In Stock'},
  {name:'Azithromycin 500mg',brand:'Azee',price:110,cat:'Antibiotic',emoji:'💉',stock:'low-stock',label:'Low Stock'},
  {name:'Glimepiride 2mg',brand:'Amaryl',price:88,cat:'Diabetes',emoji:'🩺',stock:'in-stock',label:'In Stock'},
  {name:'Montelukast 10mg',brand:'Montair',price:135,cat:'Antiallergy',emoji:'🌸',stock:'in-stock',label:'In Stock'},
];

const doctors = [
  {name:'Dr. Priya Sharma',spec:'Cardiologist',exp:'12 yrs',patients:'4.2K',rating:'4.9',fee:'₹499',emoji:'👩‍⚕️',banner:'#e8d5f5'},
  {name:'Dr. Rajan Mehta',spec:'Neurologist',exp:'15 yrs',patients:'5.1K',rating:'4.8',fee:'₹599',emoji:'👨‍⚕️',banner:'#d5e8f5'},
  {name:'Dr. Kavita Nair',spec:'Dermatologist',exp:'8 yrs',patients:'3.8K',rating:'4.7',fee:'₹399',emoji:'👩‍⚕️',banner:'#fce4ec'},
  {name:'Dr. Suresh Patel',spec:'Orthopedic',exp:'20 yrs',patients:'7.2K',rating:'4.9',fee:'₹649',emoji:'👨‍⚕️',banner:'#d5f5e3'},
  {name:'Dr. Ananya Roy',spec:'Pediatrician',exp:'10 yrs',patients:'6.5K',rating:'4.8',fee:'₹449',emoji:'👩‍⚕️',banner:'#fde8d8'},
  {name:'Dr. Vikram Singh',spec:'Cardiologist',exp:'18 yrs',patients:'8.1K',rating:'5.0',fee:'₹799',emoji:'👨‍⚕️',banner:'#f0e8fe'},
];

// ---- RENDER MEDICINES ----
function renderMeds(){
  const q = document.getElementById('med-search').value.toLowerCase();
  const grid = document.getElementById('med-grid');
  const filtered = medicines.filter(m=>{
    const mc = currentMedFilter==='All'||m.cat===currentMedFilter;
    const mq = !q||m.name.toLowerCase().includes(q)||m.brand.toLowerCase().includes(q)||m.cat.toLowerCase().includes(q);
    return mc&&mq;
  });
  if(filtered.length===0){grid.innerHTML='<div style="grid-column:1/-1;text-align:center;padding:4rem;color:var(--gray);font-size:16px;">No medicines found. Try a different search.</div>';return;}
  grid.innerHTML = filtered.map(m=>`
    <div class="med-card">
      <div class="med-img">${m.emoji}</div>
      <div class="med-name">${m.name}</div>
      <div class="med-brand">${m.brand}</div>
      <div class="med-price">₹${m.price} <span class="old-price">₹${m.price+Math.floor(m.price*0.2)}</span></div>
      <span class="med-stock ${m.stock}">${m.label}</span>
      <button class="add-cart" onclick="addToCart()">Add to Cart 🛒</button>
    </div>
  `).join('');
}

// ---- RENDER DOCTORS ----
function renderDoctors(){
  const grid = document.getElementById('doc-grid');
  const filtered = doctors.filter(d=>currentDocFilter==='All'||d.spec===currentDocFilter);
  if(filtered.length===0){grid.innerHTML='<div style="grid-column:1/-1;text-align:center;padding:4rem;color:var(--gray);">No doctors found for this specialty.</div>';return;}
  grid.innerHTML = filtered.map(d=>`
    <div class="doc-card">
      <div class="doc-banner" style="background:${d.banner};">
        <div class="doc-avatar" style="background:${d.banner};">${d.emoji}</div>
      </div>
      <div class="doc-info">
        <div class="doc-name">${d.name}</div>
        <div class="doc-spec">${d.spec}</div>
        <div class="doc-rating"><span class="stars">★★★★★</span> ${d.rating} (${Math.floor(Math.random()*400+150)} reviews)</div>
        <div class="doc-meta">
          <div class="doc-meta-item"><div class="doc-meta-num">${d.exp}</div><div class="doc-meta-label">Experience</div></div>
          <div class="doc-meta-item"><div class="doc-meta-num">${d.patients}</div><div class="doc-meta-label">Patients</div></div>
          <div class="doc-meta-item"><div class="doc-meta-num">${d.fee}</div><div class="doc-meta-label">Consult Fee</div></div>
        </div>
        <div class="doc-btns">
          <button>📹 Video</button>
          <button>💬 Chat</button>
          <button>📞 Audio</button>
        </div>
        <button class="consult-btn" onclick="showToast('📅 Booking with ${d.name}...')">Book Appointment</button>
      </div>
    </div>
  `).join('');
}

// ---- NAVIGATION ----
function showPage(page){
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.nav-links a').forEach(a=>a.classList.remove('active'));
  document.getElementById('page-'+page).classList.add('active');
  const navEl = document.getElementById('nav-'+page);
  if(navEl) navEl.classList.add('active');
  window.scrollTo({top:0,behavior:'smooth'});
}

function filterMeds(){renderMeds();}
function setFilter(cat,el){
  currentMedFilter=cat;
  document.querySelectorAll('.filter-chip').forEach(c=>c.classList.remove('active'));
  el.classList.add('active');
  renderMeds();
}
function setDocFilter(spec,el){
  currentDocFilter=spec;
  document.querySelectorAll('.spec-tab').forEach(t=>t.classList.remove('active'));
  el.classList.add('active');
  renderDoctors();
}
function addToCart(){
  cartCount++;
  document.getElementById('cart-count').textContent=cartCount;
  showToast('✅ Item added to cart!');
}
function showToast(msg){
  const t=document.getElementById('toast');
  t.textContent=msg;
  t.classList.add('show');
  setTimeout(()=>t.classList.remove('show'),2800);
}

// ---- SCROLL EFFECT ----
window.addEventListener('scroll',()=>{
  document.getElementById('navbar').classList.toggle('scrolled',window.scrollY>20);
});

// ---- 3D PARTICLES ----
const canvas = document.getElementById('particles-canvas');
const ctx = canvas.getContext('2d');
let particles = [];
function resizeCanvas(){canvas.width=window.innerWidth;canvas.height=window.innerHeight;}
resizeCanvas();
window.addEventListener('resize',resizeCanvas);

class Particle{
  constructor(){
    this.x=Math.random()*canvas.width;
    this.y=Math.random()*canvas.height;
    this.z=Math.random()*800+200;
    this.vx=(Math.random()-0.5)*0.4;
    this.vy=(Math.random()-0.5)*0.4;
    this.vz=-0.5-Math.random()*0.5;
    this.r=Math.random()*2+1;
    this.color=`hsla(${260+Math.random()*60},70%,70%,`;
  }
  update(){
    this.x+=this.vx;this.y+=this.vy;this.z+=this.vz;
    if(this.z<1){this.x=Math.random()*canvas.width;this.y=Math.random()*canvas.height;this.z=800;}
    if(this.x<0)this.x=canvas.width;if(this.x>canvas.width)this.x=0;
    if(this.y<0)this.y=canvas.height;if(this.y>canvas.height)this.y=0;
  }
  draw(){
    const scale=600/this.z;
    const sx=this.x*scale+canvas.width/2*(1-scale);
    const sy=this.y*scale+canvas.height/2*(1-scale);
    const alpha=Math.min(1,(800-this.z)/600);
    ctx.beginPath();
    ctx.arc(sx,sy,this.r*scale,0,Math.PI*2);
    ctx.fillStyle=this.color+alpha+')';
    ctx.fill();
  }
}

for(let i=0;i<120;i++) particles.push(new Particle());

function animateParticles(){
  ctx.clearRect(0,0,canvas.width,canvas.height);
  particles.forEach(p=>{p.update();p.draw();});
  requestAnimationFrame(animateParticles);
}
animateParticles();

// ---- INIT ----
renderMeds();
renderDoctors();
</script>
</body>
</html>
