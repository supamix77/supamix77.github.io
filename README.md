<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>AirForge — Radio Production Studio</title>
<link rel="preconnect" href="https://fonts.googleapis.com"/>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600&family=JetBrains+Mono:wght@400;600&family=Barlow+Condensed:wght@600;700;800&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg:        #080C12;
    --bg2:       #0D1420;
    --bg3:       #111827;
    --panel:     #141E2E;
    --border:    #1E2D42;
    --border2:   #253548;
    --teal:      #22D3B8;
    --teal-dim:  #16897A;
    --teal-glow: rgba(34,211,184,0.12);
    --red:       #EF4444;
    --amber:     #F59E0B;
    --blue:      #3B82F6;
    --text:      #E2EAF4;
    --text2:     #7A90AA;
    --text3:     #3D5068;
    --mono:      'JetBrains Mono', monospace;
    --display:   'Barlow Condensed', sans-serif;
    --body:      'Inter', sans-serif;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--body);
    font-size: 15px;
    line-height: 1.6;
    -webkit-font-smoothing: antialiased;
  }

  /* ── NAV ── */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 0 2.5rem;
    height: 56px;
    background: rgba(8,12,18,0.88);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid var(--border);
  }
  .nav-logo {
    font-family: var(--display);
    font-size: 1.4rem;
    font-weight: 800;
    letter-spacing: 0.04em;
    color: var(--text);
    text-decoration: none;
  }
  .nav-logo span { color: var(--teal); }
  .nav-links { display: flex; gap: 2rem; }
  .nav-links a {
    color: var(--text2);
    text-decoration: none;
    font-size: 0.82rem;
    font-weight: 500;
    letter-spacing: 0.06em;
    text-transform: uppercase;
    transition: color 0.2s;
  }
  .nav-links a:hover { color: var(--teal); }
  .nav-cta {
    background: var(--teal);
    color: #000;
    padding: 0.45rem 1.2rem;
    border-radius: 4px;
    font-size: 0.82rem;
    font-weight: 600;
    text-decoration: none;
    letter-spacing: 0.04em;
    transition: opacity 0.2s;
  }
  .nav-cta:hover { opacity: 0.85; }

  /* ── HERO ── */
  .hero {
    min-height: 100vh;
    display: flex; flex-direction: column;
    align-items: center; justify-content: center;
    text-align: center;
    padding: 7rem 2rem 4rem;
    position: relative;
    overflow: hidden;
  }
  .hero::before {
    content: '';
    position: absolute; inset: 0;
    background:
      radial-gradient(ellipse 70% 50% at 50% 60%, rgba(34,211,184,0.07) 0%, transparent 70%),
      radial-gradient(ellipse 40% 30% at 20% 20%, rgba(59,130,246,0.05) 0%, transparent 60%);
    pointer-events: none;
  }

  .hero-eyebrow {
    font-family: var(--mono);
    font-size: 0.72rem;
    color: var(--teal);
    letter-spacing: 0.18em;
    text-transform: uppercase;
    margin-bottom: 1.5rem;
    display: flex; align-items: center; gap: 0.75rem;
  }
  .hero-eyebrow::before, .hero-eyebrow::after {
    content: '';
    display: block;
    width: 32px; height: 1px;
    background: var(--teal-dim);
  }

  h1 {
    font-family: var(--display);
    font-size: clamp(3.5rem, 9vw, 7.5rem);
    font-weight: 800;
    line-height: 0.92;
    letter-spacing: -0.01em;
    text-transform: uppercase;
    margin-bottom: 1.5rem;
  }
  h1 em {
    font-style: normal;
    color: var(--teal);
    display: block;
  }

  .hero-sub {
    font-size: clamp(1rem, 2vw, 1.15rem);
    color: var(--text2);
    max-width: 520px;
    margin: 0 auto 2.5rem;
    font-weight: 400;
    line-height: 1.65;
  }

  .hero-actions {
    display: flex; gap: 1rem; justify-content: center; flex-wrap: wrap;
    margin-bottom: 4rem;
  }
  .btn-primary {
    background: var(--teal);
    color: #000;
    padding: 0.8rem 2rem;
    border-radius: 4px;
    font-size: 0.9rem;
    font-weight: 600;
    text-decoration: none;
    letter-spacing: 0.04em;
    transition: opacity 0.2s, transform 0.15s;
    display: inline-block;
  }
  .btn-primary:hover { opacity: 0.88; transform: translateY(-1px); }
  .btn-ghost {
    color: var(--text);
    padding: 0.8rem 2rem;
    border-radius: 4px;
    font-size: 0.9rem;
    font-weight: 500;
    text-decoration: none;
    letter-spacing: 0.04em;
    border: 1px solid var(--border2);
    transition: border-color 0.2s, color 0.2s;
    display: inline-block;
  }
  .btn-ghost:hover { border-color: var(--teal); color: var(--teal); }

  /* ── FAKE WAVEFORM PLAYER ── */
  .player-demo {
    width: 100%;
    max-width: 860px;
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 10px;
    overflow: hidden;
    box-shadow: 0 32px 80px rgba(0,0,0,0.6), 0 0 0 1px rgba(34,211,184,0.08);
  }

  .player-header {
    padding: 0.6rem 1rem;
    background: var(--panel);
    border-bottom: 1px solid var(--border);
    display: flex; align-items: center; gap: 0.5rem;
  }
  .dot { width: 10px; height: 10px; border-radius: 50%; }
  .dot-r { background: #EF4444; }
  .dot-y { background: #F59E0B; }
  .dot-g { background: #22C55E; }
  .player-title {
    margin-left: auto; margin-right: auto;
    font-family: var(--mono);
    font-size: 0.7rem;
    color: var(--text3);
    letter-spacing: 0.1em;
  }

  .timeline-area { padding: 0.75rem 1rem; }
  .ruler {
    display: flex; justify-content: space-between;
    font-family: var(--mono);
    font-size: 0.62rem;
    color: var(--text3);
    margin-bottom: 0.4rem;
    padding: 0 2px;
  }

  .track { display: flex; align-items: center; gap: 0.75rem; margin-bottom: 0.5rem; }
  .track-label {
    font-family: var(--mono);
    font-size: 0.62rem;
    color: var(--text3);
    width: 52px;
    flex-shrink: 0;
    letter-spacing: 0.06em;
  }
  .track-lane {
    flex: 1; height: 48px;
    background: #0A1018;
    border-radius: 4px;
    position: relative;
    overflow: hidden;
    border: 1px solid var(--border);
  }

  .clip {
    position: absolute; top: 3px; bottom: 3px;
    border-radius: 3px;
    overflow: hidden;
  }
  .clip-t1 { background: rgba(34,211,184,0.12); border: 1px solid rgba(34,211,184,0.35); left: 0%; width: 44%; }
  .clip-t1b { background: rgba(34,211,184,0.10); border: 1px solid rgba(34,211,184,0.28); left: 50%; width: 42%; }
  .clip-t2 { background: rgba(251,146,60,0.10); border: 1px solid rgba(251,146,60,0.30); left: 8%; width: 60%; }
  .clip-t3 { background: rgba(167,139,250,0.10); border: 1px solid rgba(167,139,250,0.28); left: 20%; width: 35%; }
  .clip-t3b { background: rgba(167,139,250,0.08); border: 1px solid rgba(167,139,250,0.22); left: 62%; width: 28%; }

  .clip-label {
    font-family: var(--mono);
    font-size: 0.58rem;
    padding: 2px 5px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
  .clip-t1 .clip-label, .clip-t1b .clip-label { color: var(--teal); }
  .clip-t2 .clip-label { color: #FB923C; }
  .clip-t3 .clip-label, .clip-t3b .clip-label { color: #A78BFA; }

  /* waveform SVG lines */
  .waveform { width: 100%; height: 100%; position: absolute; top: 0; left: 0; }

  /* playhead */
  .playhead {
    position: absolute; top: 0; bottom: 0; left: 28%;
    width: 2px; background: var(--red);
    box-shadow: 0 0 8px var(--red);
    pointer-events: none;
    animation: playhead-move 8s linear infinite;
  }
  @keyframes playhead-move {
    0%   { left: 2%; }
    100% { left: 96%; }
  }

  /* transport bar */
  .transport {
    padding: 0.75rem 1rem;
    background: var(--panel);
    border-top: 1px solid var(--border);
    display: flex; align-items: center; gap: 0.6rem;
  }
  .t-btn {
    width: 34px; height: 34px; border-radius: 50%;
    background: var(--bg3);
    border: 1px solid var(--border2);
    color: var(--text);
    font-size: 0.85rem;
    display: flex; align-items: center; justify-content: center;
    cursor: pointer;
    transition: border-color 0.15s, color 0.15s;
    user-select: none;
  }
  .t-btn:hover { border-color: var(--teal); color: var(--teal); }
  .t-btn.rec {
    color: var(--red);
    border-color: rgba(239,68,68,0.4);
    animation: rec-pulse 1s ease-in-out infinite;
  }
  @keyframes rec-pulse {
    0%, 100% { box-shadow: 0 0 0 0 rgba(239,68,68,0.3); }
    50%       { box-shadow: 0 0 0 5px rgba(239,68,68,0); }
  }
  .t-spacer { flex: 1; }
  .t-time {
    font-family: var(--mono);
    font-size: 0.75rem;
    color: var(--text2);
    letter-spacing: 0.08em;
  }
  .t-time span { color: var(--teal); }

  /* ── SECTION ── */
  section {
    padding: 5rem 2rem;
    max-width: 1100px;
    margin: 0 auto;
  }

  .section-label {
    font-family: var(--mono);
    font-size: 0.68rem;
    color: var(--teal);
    letter-spacing: 0.2em;
    text-transform: uppercase;
    margin-bottom: 1rem;
  }

  h2 {
    font-family: var(--display);
    font-size: clamp(2rem, 5vw, 3.2rem);
    font-weight: 800;
    text-transform: uppercase;
    line-height: 1.0;
    margin-bottom: 1rem;
    letter-spacing: 0.01em;
  }

  .section-sub {
    color: var(--text2);
    max-width: 480px;
    margin-bottom: 3rem;
    font-size: 0.95rem;
    line-height: 1.7;
  }

  /* ── FEATURES GRID ── */
  .features {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    gap: 1px;
    background: var(--border);
    border: 1px solid var(--border);
    border-radius: 10px;
    overflow: hidden;
  }
  .feature {
    background: var(--bg2);
    padding: 2rem;
    transition: background 0.2s;
  }
  .feature:hover { background: var(--panel); }
  .feature-icon {
    font-size: 1.4rem;
    margin-bottom: 1rem;
    display: block;
  }
  .feature h3 {
    font-family: var(--display);
    font-size: 1.1rem;
    font-weight: 700;
    letter-spacing: 0.04em;
    text-transform: uppercase;
    margin-bottom: 0.5rem;
  }
  .feature p {
    color: var(--text2);
    font-size: 0.88rem;
    line-height: 1.65;
  }

  /* ── SPECS ── */
  .specs-area {
    background: var(--bg);
    border-top: 1px solid var(--border);
    border-bottom: 1px solid var(--border);
  }
  .specs-inner {
    max-width: 1100px; margin: 0 auto;
    padding: 5rem 2rem;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
  }
  .spec-block h3 {
    font-family: var(--mono);
    font-size: 0.72rem;
    color: var(--teal);
    letter-spacing: 0.14em;
    text-transform: uppercase;
    margin-bottom: 1.25rem;
    padding-bottom: 0.75rem;
    border-bottom: 1px solid var(--border);
  }
  .spec-row {
    display: flex; justify-content: space-between; align-items: baseline;
    padding: 0.55rem 0;
    border-bottom: 1px solid rgba(30,45,66,0.5);
    font-size: 0.88rem;
  }
  .spec-key { color: var(--text2); }
  .spec-val {
    font-family: var(--mono);
    font-size: 0.82rem;
    color: var(--text);
  }

  /* ── WORKFLOW ── */
  .workflow {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 0;
    position: relative;
  }
  .workflow::before {
    content: '';
    position: absolute;
    top: 28px; left: 0; right: 0; height: 1px;
    background: linear-gradient(90deg, transparent, var(--teal-dim), transparent);
  }
  .wf-step { padding: 0 1.5rem 0 0; }
  .wf-num {
    font-family: var(--display);
    font-size: 2.5rem;
    font-weight: 800;
    color: var(--teal);
    line-height: 1;
    margin-bottom: 1rem;
    display: block;
  }
  .wf-step h3 {
    font-family: var(--display);
    font-size: 1rem;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.06em;
    margin-bottom: 0.5rem;
  }
  .wf-step p {
    color: var(--text2);
    font-size: 0.83rem;
    line-height: 1.65;
  }

  /* ── CTA ── */
  .cta-section {
    text-align: center;
    padding: 6rem 2rem;
    background: linear-gradient(180deg, var(--bg) 0%, var(--bg2) 50%, var(--bg) 100%);
    border-top: 1px solid var(--border);
    position: relative;
    overflow: hidden;
  }
  .cta-section::before {
    content: '';
    position: absolute; inset: 0;
    background: radial-gradient(ellipse 60% 60% at 50% 50%, rgba(34,211,184,0.06) 0%, transparent 70%);
    pointer-events: none;
  }
  .cta-section h2 { margin-bottom: 1rem; }
  .cta-section p { color: var(--text2); margin-bottom: 2.5rem; font-size: 1rem; max-width: 440px; margin-left: auto; margin-right: auto; }

  /* ── FOOTER ── */
  footer {
    border-top: 1px solid var(--border);
    padding: 2rem 2.5rem;
    display: flex; align-items: center; justify-content: space-between;
    font-size: 0.78rem;
    color: var(--text3);
  }
  footer a { color: var(--text3); text-decoration: none; }
  footer a:hover { color: var(--teal); }

  /* ── RESPONSIVE ── */
  @media (max-width: 640px) {
    nav { padding: 0 1.25rem; }
    .nav-links { display: none; }
    .specs-inner { grid-template-columns: 1fr; gap: 2.5rem; }
    .workflow { grid-template-columns: 1fr 1fr; gap: 2rem; }
    .workflow::before { display: none; }
    footer { flex-direction: column; gap: 0.75rem; text-align: center; }
  }

  @media (prefers-reduced-motion: reduce) {
    .playhead { animation: none; left: 28%; }
    .t-btn.rec { animation: none; }
  }
</style>
</head>
<body>

<nav>
  <a class="nav-logo" href="#"><span>Air</span>Forge</a>
  <div class="nav-links">
    <a href="#features">Features</a>
    <a href="#specs">Specs</a>
    <a href="#workflow">Workflow</a>
  </div>
  <a class="nav-cta" href="#download">Download Free</a>
</nav>

<!-- HERO -->
<div class="hero">
  <div class="hero-eyebrow">Radio Production Studio</div>
  <h1>Cut.<br><em>Polish.</em><br>Broadcast.</h1>
  <p class="hero-sub">
    Professional WAV editing built for radio. Four-track timeline, realtime mixing,
    WideOrbit-ready export. From raw recording to on-air cart in minutes.
  </p>
  <div class="hero-actions">
    <a class="btn-primary" href="#download">Download for Windows</a>
    <a class="btn-ghost" href="#features">See Features</a>
  </div>

  <!-- PLAYER DEMO -->
  <div class="player-demo">
    <div class="player-header">
      <div class="dot dot-r"></div>
      <div class="dot dot-y"></div>
      <div class="dot dot-g"></div>
      <div class="player-title">AIRFORGE STUDIO — SUMMER_PROMO_FINAL.wav</div>
    </div>
    <div class="timeline-area">
      <div class="ruler">
        <span>0:00.000</span><span>0:15.000</span><span>0:30.000</span>
        <span>0:45.000</span><span>1:00.000</span><span>1:15.000</span>
      </div>

      <!-- Track 1 -->
      <div class="track">
        <div class="track-label">TRACK 1</div>
        <div class="track-lane">
          <div class="clip clip-t1">
            <span class="clip-label">WSPA_VoiceTrack_01.wav</span>
            <svg class="waveform" viewBox="0 0 400 42" preserveAspectRatio="none">
              <polyline points="0,21 8,8 12,30 18,5 24,35 28,12 34,26 40,4 46,32 52,15 58,28 64,7 70,33 76,18 82,10 88,28 94,20 100,6 106,34 112,14 118,26 124,9 130,31 136,19 142,11 148,27 154,21 160,5 166,33 172,16 178,24 184,8 190,30 196,18 202,12 208,29 214,22 220,7 226,31 232,15 238,25 244,10 250,32 256,20 262,13 268,28 274,21 280,8 286,34 292,17 298,26 304,11 310,30 316,19 322,14 328,27 334,22 340,9 346,31 352,16 358,24 364,10 370,32 376,20 382,21 400,21" stroke="rgba(34,211,184,0.55)" stroke-width="1.2" fill="none"/>
            </svg>
          </div>
          <div class="clip clip-t1b">
            <span class="clip-label">WSPA_VoiceTrack_02.wav</span>
            <svg class="waveform" viewBox="0 0 400 42" preserveAspectRatio="none">
              <polyline points="0,21 6,12 14,32 20,8 28,28 34,14 42,33 48,6 56,29 62,18 68,11 76,31 82,22 90,7 96,35 104,13 110,27 118,9 126,30 132,19 140,12 148,28 154,23 162,6 168,34 176,16 184,25 192,10 200,31 208,20 214,14 222,29 228,21 236,8 242,33 250,17 258,26 266,11 274,30 282,19 290,13 298,27 304,22 312,9 320,31 328,16 334,24 342,10 350,32 358,20 366,15 374,28 382,21 400,21" stroke="rgba(34,211,184,0.5)" stroke-width="1.2" fill="none"/>
            </svg>
          </div>
          <div class="playhead"></div>
        </div>
      </div>

      <!-- Track 2 -->
      <div class="track">
        <div class="track-label">TRACK 2</div>
        <div class="track-lane">
          <div class="clip clip-t2">
            <span class="clip-label">BED_SummerVibes.wav</span>
            <svg class="waveform" viewBox="0 0 400 42" preserveAspectRatio="none">
              <polyline points="0,21 4,18 8,24 12,17 16,25 20,16 24,26 28,15 32,25 36,16 40,24 44,17 48,23 52,18 56,24 60,17 64,25 68,16 72,26 76,15 80,25 84,16 88,24 92,17 96,23 100,18 104,24 108,17 112,25 116,16 120,26 124,15 128,25 132,16 136,24 140,17 144,23 148,18 152,24 156,17 160,25 164,16 168,26 172,15 176,25 180,16 184,24 188,17 192,23 196,18 200,24 204,17 208,25 212,16 216,26 220,15 224,25 228,16 232,24 236,17 240,23 244,18 248,24 252,17 256,25 260,16 264,26 268,15 272,25 276,16 280,24 284,17 288,23 292,18 296,24 300,17 304,21 400,21" stroke="rgba(251,146,60,0.5)" stroke-width="1.2" fill="none"/>
            </svg>
          </div>
        </div>
      </div>

      <!-- Track 3 -->
      <div class="track">
        <div class="track-label">TRACK 3</div>
        <div class="track-lane">
          <div class="clip clip-t3">
            <span class="clip-label">STINGER_Intro.wav</span>
            <svg class="waveform" viewBox="0 0 400 42" preserveAspectRatio="none">
              <polyline points="0,21 2,4 6,38 10,6 14,36 18,8 22,34 26,10 30,32 34,12 38,30 42,14 46,28 50,16 54,26 58,18 62,24 66,19 70,23 74,20 78,22 82,21 400,21" stroke="rgba(167,139,250,0.5)" stroke-width="1.2" fill="none"/>
            </svg>
          </div>
          <div class="clip clip-t3b">
            <span class="clip-label">STINGER_Outro.wav</span>
            <svg class="waveform" viewBox="0 0 400 42" preserveAspectRatio="none">
              <polyline points="0,21 4,22 8,20 14,4 18,38 22,7 26,35 30,10 34,32 38,13 42,29 46,17 50,25 54,19 58,23 62,21 400,21" stroke="rgba(167,139,250,0.45)" stroke-width="1.2" fill="none"/>
            </svg>
          </div>
        </div>
      </div>
    </div>

    <!-- Transport -->
    <div class="transport">
      <div class="t-btn">⏮</div>
      <div class="t-btn">▶</div>
      <div class="t-btn">■</div>
      <div class="t-btn rec">●</div>
      <div class="t-btn">+</div>
      <div class="t-btn">−</div>
      <div class="t-btn">↔</div>
      <div class="t-spacer"></div>
      <div class="t-time">Cursor <span>0:32.448</span> · End <span>1:18.000</span> · Snap 10ms</div>
    </div>
  </div>
</div>

<!-- FEATURES -->
<section id="features">
  <div class="section-label">What It Does</div>
  <h2>Built for<br>Broadcast</h2>
  <p class="section-sub">
    Everything a radio production director needs. Nothing a DAW puts in the way.
  </p>
  <div class="features">
    <div class="feature">
      <span class="feature-icon">🎚️</span>
      <h3>Four-Track Timeline</h3>
      <p>Layer voice tracks, music beds, stingers, and effects. Real-time mixing with per-track volume, mute, solo, and FX chain.</p>
    </div>
    <div class="feature">
      <span class="feature-icon">✂️</span>
      <h3>Non-Destructive Editing</h3>
      <p>Split, trim, slip, and fade clips without touching your source files. Unlimited undo. Edit at the frame level.</p>
    </div>
    <div class="feature">
      <span class="feature-icon">📡</span>
      <h3>WideOrbit Ready</h3>
      <p>Export directly to WideOrbit spec. SCOT metadata embedded. Cart name, title, artist, intro, EOM — all written to the WAV.</p>
    </div>
    <div class="feature">
      <span class="feature-icon">⚡</span>
      <h3>Phoenix Audio Engine</h3>
      <p>PortAudio + NumPy mixer with preallocated buffers. Near-zero latency playback. No glitches, no dropouts on modern hardware.</p>
    </div>
    <div class="feature">
      <span class="feature-icon">🎙️</span>
      <h3>Live Recording</h3>
      <p>Record direct to a track with monitoring. Drop voice takes straight into the timeline without leaving the session.</p>
    </div>
    <div class="feature">
      <span class="feature-icon">📂</span>
      <h3>Batch Processing</h3>
      <p>Convert folders of MP3s to broadcast-spec WAV in one click. Normalize, conform, and rename to station standards automatically.</p>
    </div>
  </div>
</section>

<!-- SPECS -->
<div class="specs-area">
  <div class="specs-inner" id="specs">
    <div class="spec-block">
      <h3>Audio Engine</h3>
      <div class="spec-row"><span class="spec-key">Sample Rate</span><span class="spec-val">44.1 kHz</span></div>
      <div class="spec-row"><span class="spec-key">Bit Depth</span><span class="spec-val">16-bit PCM</span></div>
      <div class="spec-row"><span class="spec-key">Channels</span><span class="spec-val">Stereo</span></div>
      <div class="spec-row"><span class="spec-key">Backend</span><span class="spec-val">PortAudio / WASAPI</span></div>
      <div class="spec-row"><span class="spec-key">Callback Buffer</span><span class="spec-val">~100ms</span></div>
      <div class="spec-row"><span class="spec-key">Mixer</span><span class="spec-val">NumPy float32</span></div>
    </div>
    <div class="spec-block">
      <h3>Project &amp; Export</h3>
      <div class="spec-row"><span class="spec-key">Tracks</span><span class="spec-val">4 (CART/VO, BED, FX, AUX)</span></div>
      <div class="spec-row"><span class="spec-key">Formats In</span><span class="spec-val">WAV, MP3</span></div>
      <div class="spec-row"><span class="spec-key">Format Out</span><span class="spec-val">WAV (broadcast spec)</span></div>
      <div class="spec-row"><span class="spec-key">Metadata</span><span class="spec-val">SCOT, BWF, Cart Chunk</span></div>
      <div class="spec-row"><span class="spec-key">Platform</span><span class="spec-val">Windows 10/11</span></div>
      <div class="spec-row"><span class="spec-key">Runtime</span><span class="spec-val">Python 3.11+</span></div>
    </div>
  </div>
</div>

<!-- WORKFLOW -->
<section id="workflow">
  <div class="section-label">How It Works</div>
  <h2>From File<br>to Cart</h2>
  <p class="section-sub">Four steps from raw audio to a production-ready broadcast cart.</p>
  <div class="workflow">
    <div class="wf-step">
      <span class="wf-num">01</span>
      <h3>Drop Your Files</h3>
      <p>Drag WAV or MP3 files onto any track. AirForge conforms them to broadcast spec automatically.</p>
    </div>
    <div class="wf-step">
      <span class="wf-num">02</span>
      <h3>Edit the Timeline</h3>
      <p>Split, trim, and arrange clips. Set fade in/out. Layer bed music under your voice track.</p>
    </div>
    <div class="wf-step">
      <span class="wf-num">03</span>
      <h3>Set Markers</h3>
      <p>Place your Intro and EOM cues. Audition the full mix in realtime before committing.</p>
    </div>
    <div class="wf-step">
      <span class="wf-num">04</span>
      <h3>Export to Cart</h3>
      <p>One click exports a WideOrbit-ready WAV with all metadata embedded. Done.</p>
    </div>
  </div>
</section>

<!-- CTA -->
<div class="cta-section" id="download">
  <h2>Start Producing<br><em style="color:var(--teal);font-style:normal;">For Free</em></h2>
  <p>No subscription. No license server. Download once, use forever.</p>
  <div class="hero-actions">
    <a class="btn-primary" href="#">Download for Windows</a>
    <a class="btn-ghost" href="#">View on GitHub</a>
  </div>
</div>

<footer>
  <div>© 2025 AirForge Studio. All rights reserved.</div>
  <div style="display:flex;gap:1.5rem;">
    <a href="#">GitHub</a>
    <a href="#">Support</a>
    <a href="#">License</a>
  </div>
</footer>

</body>
</html>
