<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Scrubs & Beyond</title>
  <link href="https://fonts.googleapis.com/css2?family=Lora:ital,wght@0,400;0,600;0,700;1,400;1,600&family=Nunito:wght@300;400;500;600;700&display=swap" rel="stylesheet"/>
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    :root {
      --cream: #FDF6EC; --cream-deep: #F5EBD8; --parchment: #EFE2C8;
      --warm-white: #FFFBF4; --sage: #7A9E7E; --sage-pale: #E8F0E8;
      --rust: #C4613A; --rust-light: #E08B6A; --rust-pale: #FBEEE8;
      --honey: #D4903C; --honey-pale: #FDF3E3;
      --brown: #5C3D2E; --brown-mid: #8B6348;
      --text: #3A2A1E; --text-mid: #6B4F3A; --text-light: #A08060;
    }
    html { scroll-behavior: smooth; }
    body { font-family: 'Nunito', sans-serif; background: var(--cream); color: var(--text); overflow-x: hidden; }

    /* NAV */
    nav {
      position: fixed; top: 0; left: 0; right: 0; z-index: 100;
      display: flex; align-items: center; justify-content: space-between;
      padding: 1.1rem 3rem;
      background: rgba(253,246,236,0.93); backdrop-filter: blur(14px);
      border-bottom: 1.5px solid var(--parchment);
    }
    .nav-logo { font-family: 'Lora', serif; font-size: 1.45rem; font-weight: 700; color: var(--brown); text-decoration: none; }
    .nav-logo span { color: var(--rust); font-style: italic; }
    .nav-links { display: flex; gap: 2rem; list-style: none; }
    .nav-links a { text-decoration: none; font-size: 0.9rem; font-weight: 600; color: var(--text-mid); transition: color 0.2s; }
    .nav-links a:hover { color: var(--rust); }
    .nav-cta { background: var(--rust) !important; color: white !important; padding: 0.5rem 1.3rem; border-radius: 100px; transition: background 0.2s !important; }
    .nav-cta:hover { background: var(--rust-light) !important; }

    /* HERO */
    .hero { min-height: 100vh; display: flex; align-items: center; padding: 8rem 3rem 5rem; background: var(--cream); position: relative; overflow: hidden; }
    .deco { position: absolute; pointer-events: none; border-radius: 50%; filter: blur(60px); opacity: 0.5; }
    .deco1 { width: 600px; height: 600px; background: var(--parchment); top: -150px; right: -150px; }
    .deco2 { width: 400px; height: 400px; background: #EEDAD0; bottom: -100px; left: -100px; }
    .deco3 { width: 250px; height: 250px; background: var(--rust-pale); top: 35%; left: 38%; opacity: 0.6; }
    .hero-inner { max-width: 1200px; margin: 0 auto; width: 100%; display: grid; grid-template-columns: 1fr 1fr; gap: 4rem; align-items: center; position: relative; z-index: 1; }
    .hero-tag {
      display: inline-flex; align-items: center; gap: 0.5rem;
      background: var(--honey-pale); color: var(--honey);
      font-size: 0.78rem; font-weight: 700; letter-spacing: 0.09em; text-transform: uppercase;
      padding: 0.45rem 1.1rem; border-radius: 100px; margin-bottom: 1.6rem;
      border: 1.5px solid #F0D9B5; animation: fadeUp 0.6s ease both;
    }
    h1 { font-family: 'Lora', serif; font-size: clamp(2.8rem, 5vw, 4rem); font-weight: 700; line-height: 1.12; letter-spacing: -0.02em; color: var(--text); animation: fadeUp 0.6s 0.1s ease both; }
    h1 em { font-style: italic; color: var(--rust); }
    .hero-sub { margin-top: 1.4rem; font-size: 1.05rem; line-height: 1.8; color: var(--text-mid); max-width: 480px; animation: fadeUp 0.6s 0.2s ease both; }
    .hero-actions { margin-top: 2.5rem; display: flex; gap: 1rem; flex-wrap: wrap; animation: fadeUp 0.6s 0.3s ease both; }

    /* 3D BUTTONS */
    .btn-primary {
      background: var(--rust); color: white; border: none; cursor: pointer;
      padding: 0.9rem 2.1rem; border-radius: 100px;
      font-family: 'Nunito', sans-serif; font-size: 0.95rem; font-weight: 700; text-decoration: none;
      box-shadow: 0 6px 0 #8B3A1E, 0 10px 22px rgba(196,97,58,0.38);
      transition: transform 0.12s, box-shadow 0.12s; position: relative; top: 0; display: inline-block;
    }
    .btn-primary:hover { transform: translateY(3px); box-shadow: 0 3px 0 #8B3A1E, 0 6px 14px rgba(196,97,58,0.3); }
    .btn-primary:active { transform: translateY(6px); box-shadow: 0 0px 0 #8B3A1E, 0 2px 8px rgba(196,97,58,0.2); }
    .btn-secondary {
      background: var(--warm-white); color: var(--brown);
      border: 2px solid var(--parchment); padding: 0.88rem 2.1rem; border-radius: 100px;
      font-family: 'Nunito', sans-serif; font-size: 0.95rem; font-weight: 700; text-decoration: none;
      box-shadow: 0 5px 0 var(--parchment), 0 8px 18px rgba(92,61,46,0.1);
      transition: transform 0.12s, box-shadow 0.12s; position: relative; top: 0; display: inline-block;
    }
    .btn-secondary:hover { transform: translateY(3px); box-shadow: 0 2px 0 var(--parchment), 0 4px 10px rgba(92,61,46,0.08); }

    /* HERO CARDS 3D */
    .hero-visual { display: flex; flex-direction: column; gap: 1.2rem; animation: fadeUp 0.7s 0.25s ease both; }
    .hcard {
      background: var(--warm-white); border-radius: 22px; padding: 1.5rem 1.7rem;
      border: 1.5px solid var(--parchment);
      box-shadow: 0 4px 0 var(--parchment), 0 9px 0 #D5C4A8, 0 16px 30px rgba(92,61,46,0.15);
      transition: transform 0.25s, box-shadow 0.25s;
      transform: perspective(700px) rotateX(2deg); position: relative; overflow: hidden;
    }
    .hcard:hover { transform: perspective(700px) rotateX(0deg) translateY(-6px); box-shadow: 0 6px 0 var(--parchment), 0 12px 0 #D5C4A8, 0 26px 45px rgba(92,61,46,0.2); }
    .hcard::before { content: ''; position: absolute; top: 0; left: 0; width: 5px; height: 100%; border-radius: 22px 0 0 22px; }
    .hcard.accent-rust::before { background: var(--rust); }
    .hcard.accent-sage::before { background: var(--sage); }
    .hcard.accent-honey::before { background: var(--honey); }
    .hcard.offset { margin-left: 2rem; }
    .hcard.offset2 { margin-right: 1.5rem; }
    .hcard-emoji { font-size: 1.6rem; margin-bottom: 0.6rem; display: block; }
    .hcard-label { font-size: 0.7rem; font-weight: 700; letter-spacing: 0.1em; text-transform: uppercase; color: var(--text-light); margin-bottom: 0.35rem; }
    .hcard-title { font-family: 'Lora', serif; font-size: 1.05rem; font-weight: 600; color: var(--text); margin-bottom: 0.35rem; }
    .hcard-desc { font-size: 0.85rem; color: var(--text-mid); line-height: 1.6; }
    .hcard-pill { display: inline-block; margin-top: 0.8rem; font-size: 0.75rem; font-weight: 700; padding: 0.28rem 0.8rem; border-radius: 100px; }
    .pill-rust { background: var(--rust-pale); color: var(--rust); }
    .pill-sage { background: var(--sage-pale); color: var(--sage); }
    .pill-honey { background: var(--honey-pale); color: var(--honey); }

    /* STATS */
    .stats-strip { background: var(--brown); padding: 2.2rem 3rem; display: flex; justify-content: center; gap: 5rem; flex-wrap: wrap; }
    .stat { text-align: center; }
    .stat-num { font-family: 'Lora', serif; font-size: 2.4rem; font-weight: 700; color: var(--rust-light); display: block; }
    .stat-label { font-size: 0.85rem; color: rgba(255,255,255,0.65); }

    /* SECTIONS */
    section { padding: 6rem 3rem; }
    .section-inner { max-width: 1200px; margin: 0 auto; }
    .section-tag { font-size: 0.75rem; font-weight: 700; letter-spacing: 0.12em; text-transform: uppercase; color: var(--rust); margin-bottom: 0.9rem; display: block; }
    h2 { font-family: 'Lora', serif; font-size: clamp(2rem, 3.5vw, 2.8rem); font-weight: 700; letter-spacing: -0.02em; line-height: 1.15; color: var(--text); margin-bottom: 1rem; }
    h2 em { font-style: italic; color: var(--rust); }
    .section-sub { font-size: 1rem; color: var(--text-mid); line-height: 1.8; max-width: 540px; margin-bottom: 3rem; }

    /* 3D GUIDE CARDS */
    .guides-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 2rem; }
    .guide-card {
      background: var(--warm-white); border-radius: 24px; padding: 2rem;
      border: 1.5px solid var(--parchment);
      box-shadow: 0 4px 0 var(--parchment), 0 9px 0 #D5C4A8, 0 18px 35px rgba(92,61,46,0.14);
      text-decoration: none; display: block; color: inherit; cursor: pointer;
      transition: transform 0.2s, box-shadow 0.2s;
      transform: perspective(800px) rotateX(2deg) rotateY(-0.5deg);
    }
    .guide-card:hover {
      transform: perspective(800px) rotateX(0deg) rotateY(0deg) translateY(-8px);
      box-shadow: 0 6px 0 var(--parchment), 0 12px 0 #D5C4A8, 0 30px 50px rgba(92,61,46,0.2);
    }
    .guide-card:active { transform: translateY(4px); box-shadow: 0 2px 0 var(--parchment), 0 4px 0 #D5C4A8, 0 8px 18px rgba(92,61,46,0.12); }
    .guide-card.featured {
      background: linear-gradient(140deg, var(--rust) 0%, #A84A2A 100%); border-color: transparent;
      box-shadow: 0 4px 0 #7A2A10, 0 9px 0 #4A1200, 0 20px 40px rgba(196,97,58,0.4);
    }
    .guide-card.featured:hover { box-shadow: 0 6px 0 #7A2A10, 0 12px 0 #4A1200, 0 32px 55px rgba(196,97,58,0.5); }
    .guide-card.featured .guide-name,
    .guide-card.featured .guide-desc,
    .guide-card.featured .guide-arrow { color: white; }
    .guide-card.featured .guide-desc { opacity: 0.85; }
    .guide-icon-wrap { width: 58px; height: 58px; border-radius: 16px; display: flex; align-items: center; justify-content: center; font-size: 1.5rem; margin-bottom: 1.2rem; border: 1.5px solid transparent; }
    .gi-rust { background: var(--rust-pale); border-color: #F0C9B8; }
    .gi-sage { background: var(--sage-pale); border-color: #C5DBC5; }
    .gi-honey { background: var(--honey-pale); border-color: #F0D9A0; }
    .gi-parch { background: var(--cream-deep); border-color: var(--parchment); }
    .gi-white { background: rgba(255,255,255,0.2); border-color: rgba(255,255,255,0.3); }
    .guide-name { font-family: 'Lora', serif; font-size: 1.15rem; font-weight: 600; margin-bottom: 0.5rem; color: var(--text); }
    .guide-desc { font-size: 0.875rem; color: var(--text-mid); line-height: 1.65; }
    .guide-arrow { display: inline-flex; align-items: center; gap: 0.4rem; margin-top: 1.2rem; font-size: 0.82rem; font-weight: 700; color: var(--rust); }

    /* CALLOUT SECTION */
    .callout-section { background: var(--cream); }
    .callout-grid { display: grid; grid-template-columns: repeat(3,1fr); gap: 1.5rem; margin-top: 3rem; }
    .callout-card {
      border-radius: 28px; overflow: hidden; position: relative; min-height: 320px;
      display: flex; flex-direction: column; justify-content: flex-end;
      box-shadow: 0 6px 0 rgba(0,0,0,0.15), 0 14px 0 rgba(0,0,0,0.08), 0 24px 50px rgba(92,61,46,0.22);
      transition: transform 0.3s, box-shadow 0.3s; cursor: pointer;
      transform: perspective(900px) rotateX(3deg);
    }
    .callout-card:hover {
      transform: perspective(900px) rotateX(0deg) translateY(-10px);
      box-shadow: 0 8px 0 rgba(0,0,0,0.18), 0 18px 0 rgba(0,0,0,0.08), 0 38px 65px rgba(92,61,46,0.28);
    }
    .cc-bg { position: absolute; inset: 0; z-index: 0; display: flex; align-items: center; justify-content: center; }
    .cc-emoji-big { font-size: 7rem; opacity: 0.18; }
    .cc1 { background: linear-gradient(145deg, #8B3A1E, #C4613A); }
    .cc2 { background: linear-gradient(145deg, #4A6B4E, #7A9E7E); }
    .cc3 { background: linear-gradient(145deg, #8B6000, #D4903C); }
    .cc-body { position: relative; z-index: 1; padding: 1.8rem; background: linear-gradient(to top, rgba(0,0,0,0.55) 0%, transparent 100%); }
    .cc-tag { display: inline-block; font-size: 0.7rem; font-weight: 700; letter-spacing: 0.1em; text-transform: uppercase; background: rgba(255,255,255,0.2); color: white; padding: 0.25rem 0.75rem; border-radius: 100px; margin-bottom: 0.7rem; backdrop-filter: blur(4px); }
    .cc-title { font-family: 'Lora', serif; font-size: 1.35rem; font-weight: 700; color: white; line-height: 1.25; margin-bottom: 0.5rem; }
    .cc-sub { font-size: 0.82rem; color: rgba(255,255,255,0.8); line-height: 1.55; }
    .cc-link { display: inline-flex; align-items: center; gap: 0.35rem; margin-top: 1rem; font-size: 0.8rem; font-weight: 700; color: white; opacity: 0.85; }

    /* TIPS */
    .tips-section { background: var(--cream-deep); }
    .tips-layout { display: grid; grid-template-columns: 1fr 1.2fr; gap: 5rem; align-items: center; }
    .tips-list { display: flex; flex-direction: column; gap: 1.2rem; }
    .tip-item {
      background: var(--warm-white); border-radius: 18px; padding: 1.4rem 1.6rem;
      border: 1.5px solid var(--parchment);
      box-shadow: 0 4px 0 var(--parchment), 0 8px 0 #D5C4A8, 0 14px 22px rgba(92,61,46,0.1);
      display: flex; gap: 1rem; align-items: flex-start;
      transition: transform 0.2s, box-shadow 0.2s;
      transform: perspective(600px) rotateY(-1deg);
    }
    .tip-item:hover { transform: perspective(600px) rotateY(0deg) translateX(6px); box-shadow: 0 6px 0 var(--parchment), 0 10px 0 #D5C4A8, 0 20px 30px rgba(92,61,46,0.14); }
    .tip-num { min-width: 34px; height: 34px; border-radius: 10px; display: flex; align-items: center; justify-content: center; font-family: 'Lora', serif; font-weight: 700; font-size: 0.85rem; flex-shrink: 0; }
    .tn-rust { background: var(--rust-pale); color: var(--rust); }
    .tn-sage { background: var(--sage-pale); color: var(--sage); }
    .tn-honey { background: var(--honey-pale); color: var(--honey); }
    .tn-parch { background: var(--parchment); color: var(--brown-mid); }
    .tip-heading { font-weight: 700; font-size: 0.95rem; margin-bottom: 0.3rem; }
    .tip-text { font-size: 0.85rem; color: var(--text-mid); line-height: 1.65; }

    /* COMMUNITY */
    .community-section { background: var(--brown); }
    .community-section h2 { color: var(--cream); }
    .community-section .section-tag { color: var(--rust-light); }
    .community-section .section-sub { color: rgba(253,246,236,0.65); }
    .community-grid { display: grid; grid-template-columns: repeat(3,1fr); gap: 1.5rem; }
    .community-card {
      background: rgba(253,246,236,0.07); border: 1.5px solid rgba(253,246,236,0.12);
      border-radius: 24px; padding: 2rem;
      box-shadow: 0 5px 0 rgba(0,0,0,0.2), 0 10px 25px rgba(0,0,0,0.18);
      transition: transform 0.25s, box-shadow 0.25s;
      transform: perspective(700px) rotateX(2deg);
    }
    .community-card:hover { transform: perspective(700px) rotateX(0deg) translateY(-6px); background: rgba(253,246,236,0.12); box-shadow: 0 8px 0 rgba(0,0,0,0.22), 0 18px 35px rgba(0,0,0,0.22); }
    .cc-icon { font-size: 2rem; margin-bottom: 1rem; }
    .community-card h3 { font-family: 'Lora', serif; font-size: 1.15rem; font-weight: 600; color: var(--cream); margin-bottom: 0.6rem; }
    .community-card p { font-size: 0.875rem; color: rgba(253,246,236,0.6); line-height: 1.65; }

    /* FOUNDER */
    .founder-section { background: var(--rust-pale); padding: 5rem 3rem; position: relative; overflow: hidden; }
    .founder-deco { position: absolute; font-family: 'Lora', serif; font-size: 20rem; font-style: italic; color: var(--rust); opacity: 0.05; top: -3rem; left: -1rem; pointer-events: none; line-height: 1; }
    .founder-inner { max-width: 720px; margin: 0 auto; text-align: center; position: relative; z-index: 1; }
    blockquote { font-family: 'Lora', serif; font-size: clamp(1.4rem, 2.5vw, 1.9rem); font-style: italic; color: var(--text); line-height: 1.55; margin-bottom: 1.5rem; }
    blockquote span { color: var(--rust); }
    .founder-name { color: var(--text-mid); font-size: 0.9rem; font-weight: 600; }

    /* MISSION */
    .mission-layout { display: grid; grid-template-columns: 1.1fr 1fr; gap: 5rem; align-items: center; }
    .phones-wrap { display: flex; gap: 1rem; justify-content: center; align-items: flex-start; }
    .phone-mock {
      width: 130px; border-radius: 26px;
      box-shadow: 0 6px 0 rgba(92,61,46,0.25), 0 14px 0 rgba(92,61,46,0.12), 0 24px 40px rgba(92,61,46,0.2);
      overflow: hidden; position: relative; flex-shrink: 0;
      transform: perspective(600px) rotateY(4deg) rotateX(2deg);
      transition: transform 0.3s, box-shadow 0.3s;
    }
    .phone-mock:nth-child(2) { margin-top: 2.5rem; transform: perspective(600px) rotateY(-2deg) rotateX(1deg); }
    .phone-mock:nth-child(3) { margin-top: 0.8rem; transform: perspective(600px) rotateY(3deg) rotateX(2deg); }
    .phone-mock:hover { transform: perspective(600px) rotateY(0deg) rotateX(0deg) translateY(-6px); box-shadow: 0 10px 0 rgba(92,61,46,0.2), 0 20px 50px rgba(92,61,46,0.28); }
    .phone-screen { padding-top: 130%; position: relative; }
    .phone-fill { position: absolute; inset: 0; display: flex; flex-direction: column; justify-content: space-between; padding: 1.2rem 0.9rem; }
    .pf1 { background: linear-gradient(160deg, #8B3A1E, #E08B6A); }
    .pf2 { background: linear-gradient(160deg, #4A6B4E, #A8C5A0); }
    .pf3 { background: linear-gradient(160deg, #7A5A00, #D4903C); }
    .phone-top { display: flex; justify-content: space-between; align-items: center; }
    .phone-dot { width: 28px; height: 28px; border-radius: 50%; background: rgba(255,255,255,0.25); display: flex; align-items: center; justify-content: center; font-size: 0.75rem; }
    .phone-likes { font-size: 0.65rem; color: white; opacity: 0.8; font-weight: 700; }
    .phone-center-emoji { font-size: 2.5rem; text-align: center; margin: auto; }
    .phone-bottom-text { font-size: 0.62rem; color: white; font-weight: 700; line-height: 1.4; opacity: 0.92; }

    /* ── AI CHAT SECTION ── */
    .ai-section { background: var(--cream-deep); padding: 6rem 3rem; }
    .ai-inner { max-width: 800px; margin: 0 auto; }

    .ai-card {
      background: var(--warm-white);
      border-radius: 32px;
      border: 1.5px solid var(--parchment);
      box-shadow: 0 6px 0 var(--parchment), 0 14px 0 #D5C4A8, 0 28px 60px rgba(92,61,46,0.18);
      overflow: hidden;
      transform: perspective(1000px) rotateX(2deg);
      transition: transform 0.4s, box-shadow 0.4s;
    }
    .ai-card:focus-within {
      transform: perspective(1000px) rotateX(0deg);
      box-shadow: 0 8px 0 var(--parchment), 0 16px 0 #D5C4A8, 0 36px 70px rgba(92,61,46,0.22);
    }

    .ai-header {
      background: linear-gradient(135deg, var(--rust) 0%, #A84A2A 100%);
      padding: 1.4rem 1.8rem;
      display: flex; align-items: center; gap: 1rem;
    }
    .ai-avatar {
      width: 44px; height: 44px; border-radius: 14px;
      background: rgba(255,255,255,0.2);
      display: flex; align-items: center; justify-content: center;
      font-size: 1.4rem;
      box-shadow: 0 3px 0 rgba(0,0,0,0.2), 0 6px 14px rgba(0,0,0,0.15);
    }
    .ai-header-text h3 { font-family: 'Lora', serif; font-size: 1.1rem; font-weight: 700; color: white; }
    .ai-header-text p { font-size: 0.78rem; color: rgba(255,255,255,0.75); margin-top: 0.1rem; }
    .ai-status { width: 9px; height: 9px; background: #6EE7A0; border-radius: 50%; display: inline-block; margin-right: 0.4rem; box-shadow: 0 0 0 2px rgba(110,231,160,0.3); animation: pulse 2s infinite; }

    /* MESSAGES */
    .ai-messages {
      height: 380px; overflow-y: auto;
      padding: 1.5rem 1.8rem;
      display: flex; flex-direction: column; gap: 1rem;
      background: var(--warm-white);
      scroll-behavior: smooth;
    }
    .ai-messages::-webkit-scrollbar { width: 6px; }
    .ai-messages::-webkit-scrollbar-track { background: transparent; }
    .ai-messages::-webkit-scrollbar-thumb { background: var(--parchment); border-radius: 10px; }

    .msg { display: flex; gap: 0.75rem; align-items: flex-start; animation: msgIn 0.3s ease; }
    .msg.user { flex-direction: row-reverse; }

    .msg-avatar {
      width: 34px; height: 34px; border-radius: 11px; flex-shrink: 0;
      display: flex; align-items: center; justify-content: center; font-size: 1rem;
      box-shadow: 0 3px 0 rgba(92,61,46,0.15), 0 5px 12px rgba(92,61,46,0.1);
    }
    .msg-avatar.bot { background: linear-gradient(135deg, var(--rust), #A84A2A); }
    .msg-avatar.user-av { background: linear-gradient(135deg, var(--honey), #B07020); }

    .msg-bubble {
      max-width: 75%; padding: 0.85rem 1.1rem; border-radius: 18px;
      font-size: 0.88rem; line-height: 1.65; position: relative;
    }
    .msg.bot .msg-bubble {
      background: var(--cream); border: 1.5px solid var(--parchment); color: var(--text);
      border-radius: 4px 18px 18px 18px;
      box-shadow: 0 3px 0 var(--parchment), 0 6px 16px rgba(92,61,46,0.08);
    }
    .msg.user .msg-bubble {
      background: linear-gradient(135deg, var(--rust), #A84A2A); color: white;
      border-radius: 18px 4px 18px 18px;
      box-shadow: 0 3px 0 #7A2A10, 0 6px 16px rgba(196,97,58,0.3);
    }

    /* SUGGESTIONS */
    .ai-suggestions {
      padding: 0.8rem 1.8rem 0;
      display: flex; gap: 0.6rem; flex-wrap: wrap;
    }
    .suggestion-btn {
      background: var(--cream); border: 1.5px solid var(--parchment); color: var(--text-mid);
      padding: 0.4rem 0.9rem; border-radius: 100px; font-family: 'Nunito', sans-serif;
      font-size: 0.78rem; font-weight: 600; cursor: pointer;
      box-shadow: 0 3px 0 var(--parchment), 0 5px 10px rgba(92,61,46,0.07);
      transition: transform 0.12s, box-shadow 0.12s, background 0.15s;
    }
    .suggestion-btn:hover { background: var(--rust-pale); border-color: #F0C9B8; color: var(--rust); transform: translateY(-2px); box-shadow: 0 5px 0 var(--parchment), 0 8px 14px rgba(92,61,46,0.1); }
    .suggestion-btn:active { transform: translateY(2px); box-shadow: 0 1px 0 var(--parchment); }

    /* INPUT */
    .ai-input-area {
      padding: 1rem 1.4rem 1.4rem;
      display: flex; gap: 0.75rem; align-items: center;
    }
    .ai-input {
      flex: 1; background: var(--cream); border: 1.5px solid var(--parchment);
      border-radius: 100px; padding: 0.75rem 1.2rem;
      font-family: 'Nunito', sans-serif; font-size: 0.9rem; color: var(--text);
      outline: none; transition: border-color 0.2s, box-shadow 0.2s;
      box-shadow: 0 3px 0 var(--parchment) inset;
    }
    .ai-input:focus { border-color: var(--rust); box-shadow: 0 0 0 3px rgba(196,97,58,0.12); }
    .ai-input::placeholder { color: var(--text-light); }

    .ai-send {
      width: 44px; height: 44px; border-radius: 14px;
      background: var(--rust); border: none; cursor: pointer;
      display: flex; align-items: center; justify-content: center;
      font-size: 1.1rem; color: white; flex-shrink: 0;
      box-shadow: 0 4px 0 #8B3A1E, 0 7px 16px rgba(196,97,58,0.35);
      transition: transform 0.12s, box-shadow 0.12s;
    }
    .ai-send:hover { transform: translateY(2px); box-shadow: 0 2px 0 #8B3A1E, 0 4px 10px rgba(196,97,58,0.25); }
    .ai-send:active { transform: translateY(4px); box-shadow: 0 0px 0 #8B3A1E; }

    /* typing dots */
    .typing { display: flex; gap: 4px; align-items: center; padding: 0.2rem 0; }
    .typing span {
      width: 7px; height: 7px; border-radius: 50%; background: var(--text-light);
      animation: bounce 1.2s infinite ease-in-out;
    }
    .typing span:nth-child(2) { animation-delay: 0.2s; }
    .typing span:nth-child(3) { animation-delay: 0.4s; }

    /* FLOATING BUBBLE */
    .chat-bubble {
      position: fixed; bottom: 2rem; right: 2rem; z-index: 200;
      width: 62px; height: 62px; border-radius: 50%;
      background: linear-gradient(135deg, var(--rust), #A84A2A);
      border: none; cursor: pointer;
      display: flex; align-items: center; justify-content: center;
      font-size: 1.5rem;
      box-shadow: 0 6px 0 #7A2A10, 0 12px 30px rgba(196,97,58,0.45);
      transition: transform 0.15s, box-shadow 0.15s;
      animation: fadeUp 1s 0.5s ease both;
    }
    .chat-bubble:hover { transform: translateY(3px) scale(1.05); box-shadow: 0 3px 0 #7A2A10, 0 8px 20px rgba(196,97,58,0.35); }
    .chat-bubble:active { transform: translateY(6px); box-shadow: 0 0px 0 #7A2A10; }
    .chat-bubble-pulse {
      position: absolute; top: -4px; right: -4px;
      width: 18px; height: 18px; background: #6EE7A0;
      border-radius: 50%; border: 2.5px solid var(--cream);
      animation: pulse 2s infinite;
    }
    .bubble-tooltip {
      position: absolute; right: 72px; top: 50%; transform: translateY(-50%);
      background: var(--brown); color: var(--cream);
      font-family: 'Nunito', sans-serif; font-size: 0.8rem; font-weight: 700;
      padding: 0.4rem 0.9rem; border-radius: 100px; white-space: nowrap;
      opacity: 0; pointer-events: none; transition: opacity 0.2s;
      box-shadow: 0 3px 0 rgba(0,0,0,0.2), 0 6px 16px rgba(0,0,0,0.15);
    }
    .chat-bubble:hover .bubble-tooltip { opacity: 1; }

    /* FOOTER */
    footer { background: var(--text); color: rgba(253,246,236,0.5); padding: 2.5rem 3rem; display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 1rem; font-size: 0.85rem; }
    .footer-logo { font-family: 'Lora', serif; font-size: 1.2rem; font-weight: 700; color: var(--cream); }
    .footer-logo span { color: var(--rust-light); font-style: italic; }

    /* ANIMATIONS */
    @keyframes fadeUp { from { opacity: 0; transform: translateY(24px); } to { opacity: 1; transform: translateY(0); } }
    @keyframes msgIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }
    @keyframes bounce { 0%, 80%, 100% { transform: scale(0.7); opacity: 0.5; } 40% { transform: scale(1); opacity: 1; } }
    @keyframes pulse { 0%, 100% { box-shadow: 0 0 0 0 rgba(110,231,160,0.5); } 50% { box-shadow: 0 0 0 6px rgba(110,231,160,0); } }
    .reveal { opacity: 0; transform: translateY(32px); transition: opacity 0.65s ease, transform 0.65s ease; }
    .reveal.visible { opacity: 1; transform: translateY(0); }

    @media (max-width: 900px) {
      nav { padding: 1rem 1.5rem; } .nav-links { display: none; }
      .hero-inner, .tips-layout, .mission-layout { grid-template-columns: 1fr; gap: 2.5rem; }
      .callout-grid, .community-grid { grid-template-columns: 1fr; }
      section { padding: 4rem 1.5rem; } .stats-strip { gap: 2.5rem; }
      .hero { padding: 7rem 1.5rem 3rem; }
    }
  </style>
</head>
<body>

<!-- NAV -->
<nav>
  <a class="nav-logo" href="#">Scrubs <span>&</span> Beyond</a>
  <ul class="nav-links">
    <li><a href="#guides">Career Guides</a></li>
    <li><a href="#residency">Residency Tips</a></li>
    <li><a href="#community">Community</a></li>
    <li><a href="#ask">Ask AI</a></li>
    <li><a href="#community" class="nav-cta">Join Free</a></li>
  </ul>
</nav>

<!-- FLOATING CHAT BUBBLE -->
<button class="chat-bubble" onclick="document.getElementById('ask').scrollIntoView({behavior:'smooth'})">
  🩺
  <div class="chat-bubble-pulse"></div>
  <div class="bubble-tooltip">Ask our AI ✨</div>
</button>

<!-- HERO -->
<section class="hero">
  <div class="deco deco1"></div><div class="deco deco2"></div><div class="deco deco3"></div>
  <div class="hero-inner">
    <div>
      <div class="hero-tag">✨ Free · Community-Driven · No Membership</div>
      <h1>Your path into <em>medicine,</em> made warm.</h1>
      <p class="hero-sub">From high school hallways to hospital halls — Scrubs & Beyond is the cozy corner of the internet where aspiring medical professionals find guides, advice, and people who truly get it.</p>
      <div class="hero-actions">
        <a href="#guides" class="btn-primary">Explore Career Guides →</a>
        <a href="#ask" class="btn-secondary">Ask our AI 🩺</a>
      </div>
    </div>
    <div class="hero-visual">
      <div class="hcard accent-rust offset2">
        <span class="hcard-emoji">🩺</span>
        <div class="hcard-label">Featured Guide</div>
        <div class="hcard-title">How to Become a CRNA</div>
        <div class="hcard-desc">From nursing school to anesthesia — every step, from someone who's walked it.</div>
        <span class="hcard-pill pill-rust">Anesthesia</span>
      </div>
      <div class="hcard accent-sage offset">
        <span class="hcard-emoji">💬</span>
        <div class="hcard-label">Community Question</div>
        <div class="hcard-title">"What does residency week one actually look like?"</div>
        <div class="hcard-desc">14 warm, honest responses from residents who've been there.</div>
        <span class="hcard-pill pill-sage">Residency</span>
      </div>
      <div class="hcard accent-honey">
        <span class="hcard-emoji">☕</span>
        <div class="hcard-label">Tip of the Week</div>
        <div class="hcard-title">Building your first clinical schedule</div>
        <div class="hcard-desc">The time-blocking method that kept dozens of students sane through rotations.</div>
        <span class="hcard-pill pill-honey">Scheduling</span>
      </div>
    </div>
  </div>
</section>

<!-- STATS -->
<div class="stats-strip">
  <div class="stat"><span class="stat-num">100%</span><span class="stat-label">Free, always</span></div>
  <div class="stat"><span class="stat-num">15+</span><span class="stat-label">Career path guides</span></div>
  <div class="stat"><span class="stat-num">∞</span><span class="stat-label">Community support</span></div>
  <div class="stat"><span class="stat-num">0</span><span class="stat-label">Membership fees</span></div>
</div>

<!-- GUIDES -->
<section id="guides">
  <div class="section-inner">
    <span class="section-tag">Career Guides</span>
    <h2>Every path into <em>medicine,</em> mapped out.</h2>
    <p class="section-sub">Whether you're a high schooler dreaming big or already in your first rotation — we break down exactly what it takes, step by cozy step.</p>
    <div class="guides-grid reveal">
      <a class="guide-card featured" href="#">
        <div class="guide-icon-wrap gi-white">🩺</div>
        <div class="guide-name">Registered Nurse (RN)</div>
        <div class="guide-desc">From prerequisites to NCLEX — your complete roadmap to becoming an RN, including what nursing school is really like from the inside.</div>
        <div class="guide-arrow">Read guide →</div>
      </a>
      <a class="guide-card" href="#">
        <div class="guide-icon-wrap gi-rust">💉</div>
        <div class="guide-name">CRNA / Anesthesia</div>
        <div class="guide-desc">How to go from RN to Certified Registered Nurse Anesthetist — timelines, programs, and everything nobody tells you beforehand.</div>
        <div class="guide-arrow">Read guide →</div>
      </a>
      <a class="guide-card" href="#">
        <div class="guide-icon-wrap gi-sage">🔬</div>
        <div class="guide-name">Medical Doctor (MD)</div>
        <div class="guide-desc">Pre-med, MCAT, med school applications, residency matching — the full picture, written by people who lived every single step.</div>
        <div class="guide-arrow">Read guide →</div>
      </a>
      <a class="guide-card" href="#">
        <div class="guide-icon-wrap gi-honey">🧬</div>
        <div class="guide-name">Physician Assistant (PA)</div>
        <div class="guide-desc">Everything about PA school, the PANCE, and why more students are choosing this rewarding and flexible path into medicine.</div>
        <div class="guide-arrow">Read guide →</div>
      </a>
      <a class="guide-card" href="#">
        <div class="guide-icon-wrap gi-sage">🏥</div>
        <div class="guide-name">Clinical Experience 101</div>
        <div class="guide-desc">How to get your first clinical hours as a high schooler or undergrad — volunteering, scribing, CNA certification, and more.</div>
        <div class="guide-arrow">Read guide →</div>
      </a>
      <a class="guide-card" href="#">
        <div class="guide-icon-wrap gi-parch">📋</div>
        <div class="guide-name">More coming soon…</div>
        <div class="guide-desc">EMT, Pharmacist, Radiologist, Surgeon — this library is growing. Jump in the community to suggest what we cover next.</div>
        <div class="guide-arrow">Suggest a guide →</div>
      </a>
    </div>
  </div>
</section>

<!-- CALLOUTS -->
<section class="callout-section">
  <div class="section-inner">
    <span class="section-tag">What We Cover</span>
    <h2>Real topics, <em>real talk.</em></h2>
    <p class="section-sub">No fluff. No gatekeeping. Just warm, honest guidance on the things that actually matter in your medical journey.</p>
    <div class="callout-grid reveal">
      <div class="callout-card cc1">
        <div class="cc-bg"><span class="cc-emoji-big">🩺</span></div>
        <div class="cc-body">
          <span class="cc-tag">Career Paths</span>
          <div class="cc-title">Find your place in medicine</div>
          <div class="cc-sub">MD, RN, CRNA, PA — we map every route so you choose with confidence, not confusion.</div>
          <div class="cc-link">Explore all paths →</div>
        </div>
      </div>
      <div class="callout-card cc2">
        <div class="cc-bg"><span class="cc-emoji-big">📚</span></div>
        <div class="cc-body">
          <span class="cc-tag">Study & School</span>
          <div class="cc-title">Survive and thrive in med school</div>
          <div class="cc-sub">Scheduling strategies, study methods, and mental health tips from students who made it through.</div>
          <div class="cc-link">Read the guides →</div>
        </div>
      </div>
      <div class="callout-card cc3">
        <div class="cc-bg"><span class="cc-emoji-big">🌟</span></div>
        <div class="cc-body">
          <span class="cc-tag">Community</span>
          <div class="cc-title">You're not alone in this</div>
          <div class="cc-sub">Ask anything, share your story, connect with people one step ahead who remember exactly where you are.</div>
          <div class="cc-link">Join us →</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- TIPS -->
<section id="residency" class="tips-section">
  <div class="section-inner">
    <div class="tips-layout">
      <div>
        <span class="section-tag">Residency & Scheduling</span>
        <h2>Advice from people <em>already through it.</em></h2>
        <p class="section-sub">The stuff they don't put in orientation packets. Real, warm advice from residents and students who learned the hard way so you don't have to.</p>
        <a href="#ask" class="btn-primary">Ask our AI →</a>
      </div>
      <div class="tips-list reveal">
        <div class="tip-item"><div class="tip-num tn-rust">01</div><div><div class="tip-heading">Time-block your first month before it starts</div><div class="tip-text">Map out sleep, study, and self-care before day one. These need to be non-negotiable appointments — not afterthoughts.</div></div></div>
        <div class="tip-item"><div class="tip-num tn-sage">02</div><div><div class="tip-heading">Find your person on day one</div><div class="tip-text">Every cohort has someone who figures things out fast. Introduce yourself early. You'll lean on each other more than you expected.</div></div></div>
        <div class="tip-item"><div class="tip-num tn-honey">03</div><div><div class="tip-heading">Keep a "wins" journal through rotations</div><div class="tip-text">You'll forget how far you've come. One small win per day — it becomes your fuel when things get hard.</div></div></div>
        <div class="tip-item"><div class="tip-num tn-parch">04</div><div><div class="tip-heading">Start your match list earlier than you think</div><div class="tip-text">Students who begin researching programs in MS2 have a real advantage. Start a spreadsheet now, even if it's just five programs.</div></div></div>
      </div>
    </div>
  </div>
</section>

<!-- COMMUNITY -->
<section id="community" class="community-section">
  <div class="section-inner">
    <span class="section-tag">Community</span>
    <h2>You're not figuring this out <em>alone.</em></h2>
    <p class="section-sub">Ask questions. Share your journey. Get guidance from people a step ahead — and pay it forward when you get there.</p>
    <div class="community-grid reveal">
      <div class="community-card"><div class="cc-icon">🎓</div><h3>High Schoolers</h3><p>Just starting to dream about medicine? Ask anything. Get honest answers about what to study, how to shadow, and what medical school actually takes.</p></div>
      <div class="community-card"><div class="cc-icon">🩻</div><h3>Clinical Students</h3><p>In your first rotation and feeling overwhelmed? Connect with students who just went through it and get real, warm advice on surviving clinicals.</p></div>
      <div class="community-card"><div class="cc-icon">🌿</div><h3>Mentors & Residents</h3><p>Been through it already? Share what you wish you'd known. A few minutes of your time could genuinely change someone's entire trajectory.</p></div>
    </div>
  </div>
</section>

<!-- FOUNDER -->
<section class="founder-section">
  <div class="founder-deco">"</div>
  <div class="founder-inner">
    <blockquote>"I wished I had <span>something warm to turn to.</span> So we built it — for me, and for every person who comes after."</blockquote>
    <div class="founder-name">— Founder, Scrubs & Beyond · Aspiring CRNA</div>
  </div>
</section>

<!-- MISSION -->
<section id="mission">
  <div class="section-inner">
    <div class="mission-layout">
      <div>
        <span class="section-tag">Our Mission</span>
        <h2>Built by a teen who <em>needed this.</em></h2>
        <p class="section-sub">Scrubs & Beyond started because navigating medicine is overwhelming and often lonely — and it really shouldn't be. We're building the resource we all wish existed: free, honest, community-powered, and genuinely warm.</p>
        <p class="section-sub" style="margin-top:-1.5rem">Follow us on TikTok for bite-sized tips, career breakdowns, and real talk about life in medicine from someone living the journey right alongside you.</p>
        <a href="#" class="btn-primary">Follow on TikTok 🎵</a>
      </div>
      <div class="phones-wrap reveal">
        <div class="phone-mock"><div class="phone-screen"><div class="phone-fill pf1"><div class="phone-top"><div class="phone-dot">🩺</div><div class="phone-likes">❤️ 4.2k</div></div><div class="phone-center-emoji">🩺</div><div class="phone-bottom-text">How to become a CRNA 🧡 #medtok #nursing</div></div></div></div>
        <div class="phone-mock"><div class="phone-screen"><div class="phone-fill pf2"><div class="phone-top"><div class="phone-dot">📚</div><div class="phone-likes">❤️ 7.1k</div></div><div class="phone-center-emoji">😅</div><div class="phone-bottom-text">Day 1 of residency was honestly a lot… #resident</div></div></div></div>
        <div class="phone-mock"><div class="phone-screen"><div class="phone-fill pf3"><div class="phone-top"><div class="phone-dot">✏️</div><div class="phone-likes">❤️ 3.8k</div></div><div class="phone-center-emoji">☕</div><div class="phone-bottom-text">Study tips that actually helped in nursing school ✨</div></div></div></div>
      </div>
    </div>
  </div>
</section>

<!-- AI CHAT SECTION -->
<section class="ai-section" id="ask">
  <div class="section-inner">
    <div style="text-align:center; margin-bottom: 2.5rem;">
      <span class="section-tag" style="display:block; text-align:center;">AI Assistant</span>
      <h2 style="text-align:center;">Ask anything about <em>your path.</em></h2>
      <p class="section-sub" style="margin: 0.5rem auto 0; text-align:center;">Career questions, path comparisons, what med school is really like — our AI knows it all and answers with warmth, not jargon.</p>
    </div>
    <div class="ai-inner reveal">
      <div class="ai-card">
        <!-- Header -->
        <div class="ai-header">
          <div class="ai-avatar">🩺</div>
          <div class="ai-header-text">
            <h3>Scrubs AI</h3>
            <p><span class="ai-status"></span>Online · Ready to help your medical journey</p>
          </div>
        </div>
        <!-- Messages -->
        <div class="ai-messages" id="msgs">
          <div class="msg bot">
            <div class="msg-avatar bot">🩺</div>
            <div class="msg-bubble">Hey! 👋 I'm Scrubs AI — here to help with anything on your path into medicine. Ask me about career paths, what school is really like, how to get clinical hours, or anything else on your mind. What would you like to know?</div>
          </div>
        </div>
        <!-- Suggestions -->
        <div class="ai-suggestions" id="suggestions">
          <button class="suggestion-btn" onclick="sendSuggestion(this)">What's the difference between RN and CRNA?</button>
          <button class="suggestion-btn" onclick="sendSuggestion(this)">How do I get clinical hours in high school?</button>
          <button class="suggestion-btn" onclick="sendSuggestion(this)">Is PA school or med school right for me?</button>
          <button class="suggestion-btn" onclick="sendSuggestion(this)">What does a typical residency week look like?</button>
        </div>
        <!-- Input -->
        <div class="ai-input-area">
          <input class="ai-input" id="chatInput" type="text" placeholder="Ask anything about medicine or your career path…" onkeydown="if(event.key==='Enter') sendMsg()" />
          <button class="ai-send" onclick="sendMsg()">➤</button>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-logo">Scrubs <span>&</span> Beyond</div>
  <div>Free forever · Community-powered · No memberships</div>
  <div>© 2025 Scrubs & Beyond · Made with 🧡</div>
</footer>

<script>
  // Reveal on scroll
  const obs = new IntersectionObserver(entries => {
    entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); });
  }, { threshold: 0.1 });
  document.querySelectorAll('.reveal').forEach(el => obs.observe(el));

  // Chat logic
  const msgs = document.getElementById('msgs');
  const input = document.getElementById('chatInput');
  const suggestionsEl = document.getElementById('suggestions');

  function addMsg(text, role) {
    const div = document.createElement('div');
    div.className = `msg ${role}`;
    const av = document.createElement('div');
    av.className = `msg-avatar ${role === 'user' ? 'user-av' : 'bot'}`;
    av.textContent = role === 'user' ? '🙋' : '🩺';
    const bubble = document.createElement('div');
    bubble.className = 'msg-bubble';
    bubble.textContent = text;
    if (role === 'user') { div.appendChild(bubble); div.appendChild(av); }
    else { div.appendChild(av); div.appendChild(bubble); }
    msgs.appendChild(div);
    msgs.scrollTop = msgs.scrollHeight;
    return bubble;
  }

  function addTyping() {
    const div = document.createElement('div');
    div.className = 'msg bot'; div.id = 'typing-indicator';
    const av = document.createElement('div');
    av.className = 'msg-avatar bot'; av.textContent = '🩺';
    const bubble = document.createElement('div');
    bubble.className = 'msg-bubble';
    bubble.innerHTML = '<div class="typing"><span></span><span></span><span></span></div>';
    div.appendChild(av); div.appendChild(bubble);
    msgs.appendChild(div); msgs.scrollTop = msgs.scrollHeight;
  }

  function removeTyping() {
    const t = document.getElementById('typing-indicator');
    if (t) t.remove();
  }

  async function callAI(userMsg) {
    addTyping();
    try {
      const res = await fetch('https://api.anthropic.com/v1/messages', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({
          model: 'claude-sonnet-4-20250514',
          max_tokens: 1000,
          system: `You are Scrubs AI, the warm and knowledgeable assistant for "Scrubs & Beyond" — a free, community-driven website for aspiring medical professionals. You help with:
- Medical career paths (RN, CRNA, MD, PA, EMT, etc.) and how to pursue them
- What medical/nursing school is really like
- Getting clinical hours as a high schooler or undergrad
- Residency tips and scheduling advice
- Choosing between different medical careers

Your tone is warm, encouraging, and honest — like a knowledgeable friend who's been through it. Keep answers helpful and conversational. Use an occasional emoji to stay friendly. Never give actual medical advice — only career and education guidance. If asked something outside medical careers/education, kindly redirect to your focus area.`,
          messages: [{ role: 'user', content: userMsg }]
        })
      });
      const data = await res.json();
      removeTyping();
      const reply = data.content?.map(b => b.text || '').join('') || "Hmm, I had trouble with that one. Try asking again!";
      addMsg(reply, 'bot');
    } catch (e) {
      removeTyping();
      addMsg("Oops, something went wrong on my end 😅 Try again in a moment!", 'bot');
    }
  }

  function sendMsg() {
    const text = input.value.trim();
    if (!text) return;
    suggestionsEl.style.display = 'none';
    addMsg(text, 'user');
    input.value = '';
    callAI(text);
  }

  function sendSuggestion(btn) {
    const text = btn.textContent;
    suggestionsEl.style.display = 'none';
    addMsg(text, 'user');
    callAI(text);
  }
</script>
</body>
</html>
