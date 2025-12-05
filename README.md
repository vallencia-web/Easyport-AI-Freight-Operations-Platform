<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Easyport • AI Freight Operations on Google Cloud</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <meta name="description" content="Easyport is an AI-powered B2B SaaS platform that modernizes freight forwarding operations using Google Cloud technologies such as Vertex AI, BigQuery, and Cloud Run." />

  <!-- Minimal, modern font -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet" />

  <style>
    :root {
      --bg: #050816;
      --bg-alt: #050816;
      --card-bg: rgba(15, 23, 42, 0.85);
      --accent: #00e0ff;
      --accent-soft: rgba(0, 224, 255, 0.18);
      --accent-second: #7c3aed;
      --text-main: #f9fafb;
      --text-muted: #9ca3af;
      --border-subtle: rgba(148, 163, 184, 0.3);
      --shadow-soft: 0 18px 40px rgba(15, 23, 42, 0.75);
      --radius-xl: 22px;
      --radius-lg: 16px;
      --radius-pill: 999px;
      --max-width: 1120px;
      --nav-height: 68px;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: "Inter", system-ui, -apple-system, BlinkMacSystemFont, sans-serif;
      background:
        radial-gradient(circle at 0% 0%, rgba(124, 58, 237, 0.18), transparent 55%),
        radial-gradient(circle at 100% 0%, rgba(56, 189, 248, 0.25), transparent 55%),
        radial-gradient(circle at 50% 120%, rgba(14, 165, 233, 0.25), #020617 70%);
      color: var(--text-main);
      line-height: 1.6;
      -webkit-font-smoothing: antialiased;
    }

    a {
      color: inherit;
      text-decoration: none;
    }

    /* Layout */

    .page {
      min-height: 100vh;
      display: flex;
      flex-direction: column;
    }

    header {
      position: sticky;
      top: 0;
      z-index: 40;
      backdrop-filter: blur(18px);
      background: linear-gradient(to bottom,
        rgba(2, 6, 23, 0.92),
        rgba(2, 6, 23, 0.82),
        transparent);
      border-bottom: 1px solid rgba(148, 163, 184, 0.22);
    }

    .nav {
      max-width: var(--max-width);
      margin: 0 auto;
      height: var(--nav-height);
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 0 1.5rem;
    }

    .nav-left {
      display: flex;
      align-items: center;
      gap: 0.75rem;
    }

    .logo-mark {
      width: 32px;
      height: 32px;
      border-radius: 12px;
      border: 1px solid rgba(148, 163, 184, 0.6);
      background: radial-gradient(circle at 20% 0%, #22d3ee, transparent 45%),
                  radial-gradient(circle at 80% 100%, #7c3aed, transparent 50%),
                  #020617;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 0 0 1px rgba(15, 23, 42, 0.9), 0 16px 30px rgba(15, 23, 42, 0.8);
    }

    .logo-mark span {
      font-size: 16px;
      font-weight: 700;
      color: #e5faff;
    }

    .logo-text {
      display: flex;
      flex-direction: column;
      gap: 2px;
    }

    .logo-text-main {
      font-weight: 600;
      letter-spacing: 0.12em;
      font-size: 0.82rem;
      text-transform: uppercase;
    }

    .logo-text-sub {
      font-size: 0.74rem;
      color: var(--text-muted);
    }

    .nav-links {
      display: flex;
      align-items: center;
      gap: 1.5rem;
      font-size: 0.86rem;
      color: #e5e7eb;
    }

    .nav-links a {
      position: relative;
      padding-bottom: 2px;
    }

    .nav-links a::after {
      content: "";
      position: absolute;
      left: 0;
      bottom: 0;
      width: 0;
      height: 2px;
      background: linear-gradient(90deg, var(--accent), var(--accent-second));
      transition: width 0.22s ease;
    }

    .nav-links a:hover::after {
      width: 100%;
    }

    .tag-beta {
      border-radius: var(--radius-pill);
      padding: 0.22rem 0.7rem;
      font-size: 0.7rem;
      border: 1px solid rgba(56, 189, 248, 0.45);
      background: radial-gradient(circle at 0 0, rgba(56, 189, 248, 0.4), transparent 55%);
      color: #ccfbf1;
      display: inline-flex;
      align-items: center;
      gap: 0.25rem;
    }

    .tag-dot {
      width: 7px;
      height: 7px;
      border-radius: 999px;
      background: #22c55e;
      box-shadow: 0 0 0 5px rgba(34, 197, 94, 0.18);
    }

    main {
      flex: 1;
    }

    .section {
      max-width: var(--max-width);
      margin: 0 auto;
      padding: 3.5rem 1.5rem;
    }

    .section.compact {
      padding-top: 1.75rem;
      padding-bottom: 2.5rem;
    }

    /* Hero */

    .hero {
      display: grid;
      grid-template-columns: minmax(0, 3fr) minmax(0, 2.5fr);
      gap: 2.8rem;
      align-items: center;
      padding-top: 3rem;
      padding-bottom: 4rem;
    }

    .hero-kicker {
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      padding: 0.22rem 0.5rem 0.22rem 0.22rem;
      border-radius: var(--radius-pill);
      border: 1px solid rgba(148, 163, 184, 0.4);
      background: radial-gradient(circle at 0 0, rgba(56, 189, 248, 0.45), transparent 55%);
      font-size: 0.75rem;
      color: #e5f6ff;
      margin-bottom: 1.2rem;
    }

    .kicker-pill {
      padding: 0.17rem 0.6rem;
      border-radius: 999px;
      background: rgba(15, 23, 42, 0.88);
      border: 1px solid rgba(148, 163, 184, 0.6);
      font-weight: 500;
    }

    .hero-title {
      font-size: clamp(2.4rem, 4vw, 3rem);
      line-height: 1.1;
      font-weight: 700;
      letter-spacing: -0.04em;
      margin-bottom: 1.1rem;
    }

    .hero-title span.accent {
      background: linear-gradient(120deg, #22d3ee, #0ea5e9, #a855f7);
      -webkit-background-clip: text;
      color: transparent;
    }

    .hero-subtitle {
      font-size: 0.98rem;
      max-width: 34rem;
      color: var(--text-muted);
      margin-bottom: 1.6rem;
    }

    .hero-metadata {
      display: flex;
      flex-wrap: wrap;
      gap: 0.75rem 1.5rem;
      font-size: 0.78rem;
      color: #9ca3af;
      margin-bottom: 1.8rem;
    }

    .hero-metadata span {
      display: inline-flex;
      align-items: center;
      gap: 0.4rem;
    }

    .badge-pill {
      border-radius: 999px;
      border: 1px solid rgba(148, 163, 184, 0.6);
      padding: 0.15rem 0.65rem;
      font-size: 0.72rem;
      background: rgba(15, 23, 42, 0.9);
    }

    .hero-actions {
      display: flex;
      flex-wrap: wrap;
      gap: 0.8rem;
      margin-bottom: 1.8rem;
    }

    .btn-primary,
    .btn-ghost {
      border-radius: 999px;
      padding: 0.7rem 1.3rem;
      font-size: 0.85rem;
      display: inline-flex;
      align-items: center;
      gap: 0.45rem;
      border: 1px solid transparent;
      cursor: pointer;
      transition: transform 0.14s ease, box-shadow 0.14s ease, background 0.14s ease,
        border-color 0.14s ease;
      background: none;
    }

    .btn-primary {
      background: radial-gradient(circle at 0 0, #22d3ee, transparent 55%),
        linear-gradient(120deg, #22d3ee, #0ea5e9, #7c3aed);
      border-color: rgba(56, 189, 248, 0.9);
      color: #0f172a;
      font-weight: 600;
      box-shadow: 0 14px 40px rgba(8, 47, 73, 0.9);
    }

    .btn-primary:hover {
      transform: translateY(-1px);
      box-shadow: 0 18px 48px rgba(8, 47, 73, 0.96);
    }

    .btn-ghost {
      border-color: rgba(148, 163, 184, 0.6);
      color: #e5e7eb;
      background: rgba(15, 23, 42, 0.8);
    }

    .btn-ghost:hover {
      background: rgba(15, 23, 42, 0.98);
      transform: translateY(-1px);
    }

    .btn-icon {
      font-size: 1rem;
    }

    .hero-footnote {
      font-size: 0.74rem;
      color: var(--text-muted);
    }

    /* Hero right: architecture card */

    .hero-right {
      position: relative;
    }

    .glass-card {
      position: relative;
      border-radius: var(--radius-xl);
      background: radial-gradient(circle at 0 0, rgba(59, 130, 246, 0.40), transparent 58%),
                  radial-gradient(circle at 100% 100%, rgba(45, 212, 191, 0.4), transparent 60%),
                  rgba(15, 23, 42, 0.9);
      border: 1px solid rgba(148, 163, 184, 0.4);
      box-shadow: var(--shadow-soft);
      padding: 1.7rem 1.5rem 1.4rem;
      overflow: hidden;
    }

    .glass-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-bottom: 1.1rem;
    }

    .glass-title-block {
      display: flex;
      flex-direction: column;
      gap: 0.2rem;
    }

    .glass-title {
      font-size: 0.9rem;
      font-weight: 600;
    }

    .glass-sub {
      font-size: 0.74rem;
      color: #cbd5f5;
    }

    .status-chip {
      border-radius: 999px;
      padding: 0.22rem 0.75rem;
      font-size: 0.7rem;
      border: 1px solid rgba(163, 230, 53, 0.8);
      background: rgba(22, 163, 74, 0.2);
      display: inline-flex;
      align-items: center;
      gap: 0.3rem;
      color: #dcfce7;
    }

    .status-light {
      width: 7px;
      height: 7px;
      border-radius: 999px;
      background: #a3e635;
      box-shadow: 0 0 0 6px rgba(190, 242, 100, 0.45);
    }

    .arch-grid {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 0.75rem;
      margin-bottom: 1.2rem;
    }

    .arch-card {
      border-radius: var(--radius-lg);
      background: rgba(15, 23, 42, 0.86);
      border: 1px solid rgba(148, 163, 184, 0.48);
      padding: 0.75rem 0.85rem;
      font-size: 0.78rem;
    }

    .arch-label {
      font-size: 0.72rem;
      text-transform: uppercase;
      letter-spacing: 0.12em;
      color: #9ca3af;
      margin-bottom: 0.28rem;
    }

    .arch-main {
      font-weight: 500;
      margin-bottom: 0.15rem;
    }

    .arch-desc {
      font-size: 0.72rem;
      color: #9ca3af;
    }

    .arch-pill-row {
      display: flex;
      flex-wrap: wrap;
      gap: 0.4rem;
      margin-top: 0.35rem;
    }

    .arch-pill {
      padding: 0.1rem 0.55rem;
      border-radius: 999px;
      border: 1px solid rgba(148, 163, 184, 0.6);
      font-size: 0.68rem;
      color: #e5e7eb;
    }

    .arch-footer {
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 0.5rem;
      font-size: 0.72rem;
      color: #cbd5f5;
      border-top: 1px dashed rgba(148, 163, 184, 0.5);
      padding-top: 0.75rem;
      margin-top: 0.2rem;
    }

    .mini-metric {
      display: flex;
      flex-direction: column;
      gap: 0.1rem;
    }

    .mini-metric span:first-child {
      font-size: 0.68rem;
      text-transform: uppercase;
      letter-spacing: 0.12em;
      color: #9ca3af;
    }

    .mini-metric span:last-child {
      font-size: 0.86rem;
      font-weight: 500;
    }

    .blur-orb {
      position: absolute;
      inset: auto;
      width: 180px;
      height: 180px;
      background: radial-gradient(circle, rgba(56, 189, 248, 0.45), transparent 60%);
      filter: blur(18px);
      opacity: 0.8;
      right: -40px;
      bottom: -40px;
      pointer-events: none;
    }

    /* Sections */

    .section-heading {
      font-size: 1.45rem;
      font-weight: 600;
      margin-bottom: 0.4rem;
      letter-spacing: -0.03em;
    }

    .section-tagline {
      font-size: 0.88rem;
      color: var(--text-muted);
      max-width: 34rem;
      margin-bottom: 1.8rem;
    }

    .two-col {
      display: grid;
      grid-template-columns: minmax(0, 1.4fr) minmax(0, 1.7fr);
      gap: 2.4rem;
      align-items: flex-start;
    }

    .paragraph {
      font-size: 0.92rem;
      color: var(--text-muted);
    }

    .highlight-box {
      border-radius: var(--radius-lg);
      background: rgba(15, 23, 42, 0.92);
      border: 1px solid rgba(148, 163, 184, 0.5);
      padding: 1rem 1.1rem;
      font-size: 0.86rem;
      color: #e5e7eb;
      box-shadow: 0 16px 35px rgba(15, 23, 42, 0.85);
    }

    .pill-row {
      display: flex;
      flex-wrap: wrap;
      gap: 0.45rem;
      margin-top: 0.65rem;
    }

    .pill {
      border-radius: 999px;
      border: 1px solid rgba(148, 163, 184, 0.6);
      padding: 0.15rem 0.6rem;
      font-size: 0.75rem;
      color: #e5e7eb;
      background: rgba(15, 23, 42, 0.85);
    }

    /* Feature grid */

    .feature-grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 1.5rem;
    }

    .feature-card {
      border-radius: var(--radius-lg);
      background: rgba(15, 23, 42, 0.9);
      border: 1px solid rgba(148, 163, 184, 0.5);
      padding: 1rem 1rem 1.1rem;
      font-size: 0.86rem;
      box-shadow: 0 16px 32px rgba(15, 23, 42, 0.85);
    }

    .feature-label {
      font-size: 0.74rem;
      text-transform: uppercase;
      letter-spacing: 0.14em;
      color: #9ca3af;
      margin-bottom: 0.35rem;
    }

    .feature-title {
      font-size: 0.92rem;
      font-weight: 500;
      margin-bottom: 0.35rem;
    }

    .feature-card p {
      color: var(--text-muted);
    }

    /* Stats row */

    .stats-row {
      display: flex;
      flex-wrap: wrap;
      gap: 1.3rem;
      margin-top: 1.2rem;
    }

    .stat {
      min-width: 150px;
      padding: 0.75rem 0.9rem;
      border-radius: var(--radius-lg);
      border: 1px solid rgba(148, 163, 184, 0.45);
      background: rgba(15, 23, 42, 0.9);
      font-size: 0.82rem;
    }

    .stat span.value {
      display: block;
      font-size: 1.25rem;
      font-weight: 600;
      margin-bottom: 0.2rem;
    }

    .stat span.label {
      color: var(--text-muted);
      font-size: 0.78rem;
    }

    /* Contact */

    .contact-card {
      border-radius: var(--radius-xl);
      border: 1px solid rgba(148, 163, 184, 0.6);
      background: radial-gradient(circle at 0 0, rgba(56, 189, 248, 0.4), transparent 55%),
                  radial-gradient(circle at 100% 100%, rgba(124, 58, 237, 0.4), transparent 60%),
                  rgba(15, 23, 42, 0.94);
      padding: 1.6rem 1.6rem;
      display: grid;
      grid-template-columns: minmax(0, 2.4fr) minmax(0, 2fr);
      gap: 1.8rem;
      box-shadow: var(--shadow-soft);
      font-size: 0.9rem;
    }

    .contact-card h3 {
      font-size: 1.1rem;
      font-weight: 600;
      margin-bottom: 0.4rem;
    }

    .contact-card p {
      color: #e5e7eb;
      font-size: 0.88rem;
    }

    .contact-meta {
      display: flex;
      flex-direction: column;
      gap: 0.2rem;
      margin-top: 0.7rem;
      font-size: 0.85rem;
    }

    .contact-meta span {
      color: #e5e7eb;
    }

    .contact-meta a {
      color: #e0f2fe;
      text-decoration: underline;
      text-decoration-style: dotted;
      text-underline-offset: 3px;
    }

    .contact-cta {
      display: flex;
      flex-direction: column;
      gap: 0.8rem;
      align-items: flex-start;
      justify-content: center;
    }

    footer {
      border-top: 1px solid rgba(31, 41, 55, 0.9);
      padding: 1.4rem 1.5rem 2rem;
      font-size: 0.8rem;
      color: var(--text-muted);
    }

    footer .footer-inner {
      max-width: var(--max-width);
      margin: 0 auto;
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      justify-content: space-between;
      gap: 0.8rem;
    }

    footer a {
      color: #c4f1ff;
    }

    /* Responsive */

    @media (max-width: 900px) {
      .hero {
        grid-template-columns: minmax(0, 1fr);
      }

      .hero-right {
        order: -1;
      }

      .two-col {
        grid-template-columns: minmax(0, 1fr);
      }

      .feature-grid {
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }

      .contact-card {
        grid-template-columns: minmax(0, 1fr);
      }
    }

    @media (max-width: 640px) {
      .nav-links {
        display: none;
      }

      .section {
        padding-inline: 1.2rem;
      }

      .feature-grid {
        grid-template-columns: minmax(0, 1fr);
      }

      .stats-row {
        gap: 0.9rem;
      }

      .hero {
        padding-top: 2.4rem;
      }
    }
  </style>
</head>
<body>
<div class="page">

  <!-- NAVBAR -->
  <header>
    <nav class="nav">
      <div class="nav-left">
        <div class="logo-mark"><span>E</span></div>
        <div class="logo-text">
          <span class="logo-text-main">EASYPORT</span>
          <span class="logo-text-sub">AI Freight • Google Cloud Native</span>
        </div>
      </div>
      <div class="nav-links">
        <a href="#about">Overview</a>
        <a href="#features">Capabilities</a>
        <a href="#architecture">Google Cloud</a>
        <a href="#value">Impact</a>
        <a href="#contact">Contact</a>
        <span class="tag-beta">
          <span class="tag-dot"></span>
          Live solution • B2B SaaS
        </span>
      </div>
    </nav>
  </header>

  <main>

    <!-- HERO -->
    <section class="section hero" id="top">
      <div>
        <div class="hero-kicker">
          <span class="kicker-pill">Built with Google Cloud</span>
          <span>Vertex AI • BigQuery • Cloud Run</span>
        </div>

        <h1 class="hero-title">
          AI freight operations
          <span class="accent">designed for forwarders,</span>
          powered by Google Cloud.
        </h1>

        <p class="hero-subtitle">
          Easyport is an AI-powered B2B SaaS platform that digitizes and orchestrates
          freight forwarding workflows end-to-end. We combine automation, real-time
          intelligence, and secure Google Cloud infrastructure to help logistics
          teams move faster with higher accuracy.
        </p>

        <div class="hero-metadata">
          <span>
            <span class="badge-pill">AI-native B2B SaaS</span>
          </span>
          <span>Indonesia • Serving global freight forwarders</span>
        </div>

        <div class="hero-actions">
          <a class="btn-primary" href="mailto:vallencia@easyport.cc?subject=Easyport%20Demo%20Request">
            <span>Request a demo</span>
            <span class="btn-icon">↗</span>
          </a>
          <a class="btn-ghost" href="https://easyport.cc" target="_blank" rel="noopener noreferrer">
            <span>Visit main site</span>
          </a>
        </div>

        <p class="hero-footnote">
          Easyport eliminates manual inefficiencies, provides real-time insights, and
          enables freight forwarders to make faster, data-driven decisions across
          shipments, documents, and operations.
        </p>
      </div>

      <!-- HERO RIGHT: MINI ARCHITECTURE -->
      <div class="hero-right">
        <div class="glass-card">
          <div class="glass-header">
            <div class="glass-title-block">
              <div class="glass-title">Easyport x Google Cloud</div>
              <div class="glass-sub">High-confidence AI freight orchestration</div>
            </div>
            <div class="status-chip">
              <span class="status-light"></span>
              Live in production
            </div>
          </div>

          <div class="arch-grid">
            <div class="arch-card">
              <div class="arch-label">AI layer</div>
              <div class="arch-main">Vertex AI</div>
              <div class="arch-desc">
                Document extraction, shipment classification, predictive ETAs
                and workload automation.
              </div>
              <div class="arch-pill-row">
                <span class="arch-pill">OCR & NLP</span>
                <span class="arch-pill">ML Models</span>
              </div>
            </div>

            <div class="arch-card">
              <div class="arch-label">Data foundation</div>
              <div class="arch-main">BigQuery + Cloud Storage</div>
              <div class="arch-desc">
                Centralized freight, customer and operations data with
                secure, scalable analytics.
              </div>
            </div>

            <div class="arch-card">
              <div class="arch-label">Application runtime</div>
              <div class="arch-main">Cloud Run microservices</div>
              <div class="arch-desc">
                Stateless APIs and orchestration services powering the Easyport web app.
              </div>
            </div>

            <div class="arch-card">
              <div class="arch-label">Security</div>
              <div class="arch-main">IAM • Encryption</div>
              <div class="arch-desc">
                Enterprise-grade access control and encrypted data in transit and at rest.
              </div>
            </div>
          </div>

          <div class="arch-footer">
            <div class="mini-metric">
              <span>Typical gains</span>
              <span>30–50% less manual handling</span>
            </div>
            <div class="mini-metric">
              <span>Focus vertical</span>
              <span>Global freight forwarders</span>
            </div>
          </div>

          <div class="blur-orb"></div>
        </div>
      </div>
    </section>

    <!-- ABOUT / OVERVIEW -->
    <section class="section compact" id="about">
      <div class="two-col">
        <div>
          <h2 class="section-heading">Purpose-built for the freight forwarding industry</h2>
          <p class="section-tagline">
            Easyport’s mission is to empower freight forwarding companies with
            cutting-edge AI and SaaS solutions, enabling them to operate with greater
            efficiency, precision, and scalability.
          </p>
          <p class="paragraph">
            Traditional freight workflows are fragmented across email, spreadsheets,
            and legacy systems. This creates manual inefficiencies, inconsistent data,
            and limited visibility into day-to-day operations. Easyport replaces these
            silos with an AI-driven operations layer running on Google Cloud. From
            quoting and booking to documentation, monitoring, and post-shipment
            analytics, Easyport intelligently orchestrates tasks so teams can focus on
            exceptions and customers rather than low-value manual work.
          </p>
        </div>

        <div>
          <div class="highlight-box">
            <strong>What Easyport delivers</strong>
            <ul style="margin-top:0.6rem; padding-left:1.1rem;">
              <li>End-to-end freight operations in a single, secure platform</li>
              <li>AI-assisted workflows for documents, shipments, and tasks</li>
              <li>Real-time operational dashboards powered by BigQuery</li>
              <li>Predictive insights for ETAs, delays, and workload peaks</li>
            </ul>
            <div class="pill-row">
              <span class="pill">B2B SaaS</span>
              <span class="pill">Logistics &amp; Supply Chain</span>
              <span class="pill">Google Cloud Native</span>
              <span class="pill">AI-powered automation</span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- FEATURES / CAPABILITIES -->
    <section class="section compact" id="features">
      <h2 class="section-heading">Operational capabilities, AI-first by design</h2>
      <p class="section-tagline">
        Easyport combines AI, data, and cloud-native engineering to automate the
        most tedious parts of the freight lifecycle while preserving full human control.
      </p>

      <div class="feature-grid">
        <div class="feature-card">
          <div class="feature-label">Workflows</div>
          <div class="feature-title">Automated freight operations</div>
          <p>
            Digitize bookings, documentation, tracking, and hand-offs with configurable
            workflows that reflect how modern freight teams actually operate.
          </p>
        </div>

        <div class="feature-card">
          <div class="feature-label">AI DOCUMENTS</div>
          <div class="feature-title">Smart document understanding</div>
          <p>
            Use Vertex AI and OCR to extract, validate, and normalize information from
            invoices, packing lists, and bills of lading, reducing repetitive data entry.
          </p>
        </div>

        <div class="feature-card">
          <div class="feature-label">INSIGHTS</div>
          <div class="feature-title">Real-time operations visibility</div>
          <p>
            BigQuery-based dashboards reveal shipment status, exceptions, and workload
            bottlenecks, enabling proactive decisions instead of reactive firefighting.
          </p>
        </div>

        <div class="feature-card">
          <div class="feature-label">PREDICTION</div>
          <div class="feature-title">Predictive ETAs & risk scoring</div>
          <p>
            ML models highlight shipments at risk of delay, enabling teams to act early,
            update customers, and avoid surprises.
          </p>
        </div>

        <div class="feature-card">
          <div class="feature-label">ORCHESTRATION</div>
          <div class="feature-title">Cloud Run microservices</div>
          <p>
            Stateless microservices on Cloud Run coordinate events between systems,
            partners, and users with low latency and automatic scaling.
          </p>
        </div>

        <div class="feature-card">
          <div class="feature-label">SECURITY</div>
          <div class="feature-title">Enterprise-grade security</div>
          <p>
            IAM, VPC networking, and encryption in transit and at rest keep sensitive
            freight and customer data protected while remaining accessible to the right people.
          </p>
        </div>
      </div>
    </section>

    <!-- GOOGLE CLOUD ARCHITECTURE SECTION -->
    <section class="section compact" id="architecture">
      <h2 class="section-heading">How Easyport runs on Google Cloud</h2>
      <p class="section-tagline">
        Our architecture is designed to be secure, observable, and globally scalable,
        while remaining simple for freight teams to deploy and operate.
      </p>

      <div class="two-col">
        <div>
          <div class="paragraph">
            <p>
              Easyport’s application layer runs as containerized services on
              <strong>Cloud Run</strong>, providing a fully managed, auto-scaling runtime for
              APIs, background workers, and front-end delivery. Operational data is
              streamed and stored in <strong>BigQuery</strong> for analytics, while documents
              and unstructured content are securely stored in <strong>Cloud Storage</strong>.
            </p>
            <br />
            <p>
              On top of this data foundation, we use <strong>Vertex AI</strong> to build and serve
              models that classify shipments, extract document data, and surface
              predictive insights for ETAs and operational risk. Access to data and
              services is governed through <strong>Cloud IAM</strong>, ensuring least-privilege
              access and full auditability across tenants and environments.
            </p>
          </div>
          <div class="stats-row">
            <div class="stat">
              <span class="value">100%</span>
              <span class="label">Google Cloud-hosted core workloads</span>
            </div>
            <div class="stat">
              <span class="value">ms</span>
              <span class="label">Typical response times for key APIs via Cloud Run</span>
            </div>
            <div class="stat">
              <span class="value">Multi-tenant</span>
              <span class="label">Designed for global freight forwarders</span>
            </div>
          </div>
        </div>

        <div>
          <div class="highlight-box">
            <strong>Primary Google Cloud products</strong>
            <ul style="margin-top:0.6rem; padding-left:1.1rem;">
              <li><strong>Vertex AI</strong> – ML models for document intelligence and predictions</li>
              <li><strong>BigQuery</strong> – Central freight data warehouse and analytics hub</li>
              <li><strong>Cloud Run</strong> – Serverless containers for APIs and orchestration</li>
              <li><strong>Cloud Storage</strong> – Durable storage for files and documents</li>
              <li><strong>Cloud Logging &amp; Monitoring</strong> – End-to-end observability</li>
              <li><strong>Cloud IAM</strong> – Fine-grained access control and tenancy separation</li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <!-- VALUE / IMPACT -->
    <section class="section compact" id="value">
      <h2 class="section-heading">Operational impact for freight forwarders</h2>
      <p class="section-tagline">
        Easyport helps logistics teams move from manual processing and disconnected
        tools to a unified, AI-driven operations platform.
      </p>

      <div class="two-col">
        <div>
          <div class="paragraph">
            <p>
              By digitizing workflows and embedding AI into everyday tasks, Easyport
              typically reduces manual handling by <strong>30–50%</strong>, shortens response
              times to customers, and increases the reliability of shipment data.
              Instead of re-keying documents or searching across email threads, teams
              receive structured information, alerts, and recommendations inside a
              single interface.
            </p>
            <br />
            <p>
              With Google Cloud as our foundation, we can scale to new trade lanes,
              branches, and partners while keeping performance and security consistent.
              Freight forwarders benefit from continuous improvements to models and
              features as Easyport evolves with industry needs.
            </p>
          </div>
        </div>

        <div>
          <div class="highlight-box">
            <strong>Designed for:</strong>
            <ul style="margin-top:0.6rem; padding-left:1.1rem;">
              <li>Regional and global freight forwarding companies</li>
              <li>Logistics teams modernizing legacy processes</li>
              <li>Organizations that require auditable, secure operations</li>
              <li>Partners building on Google Cloud in the logistics domain</li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <!-- CONTACT -->
    <section class="section compact" id="contact">
      <div class="contact-card">
        <div>
          <h3>Talk to us about AI freight operations on Google Cloud</h3>
          <p>
            Whether you are modernizing an existing freight forwarding business or
            building new digital logistics offerings, Easyport provides an AI-driven
            operations layer ready to run on Google Cloud.
          </p>
          <div class="contact-meta">
            <span><strong>Company:</strong> Easyport (Indonesia)</span>
            <span><strong>Email:</strong> <a href="mailto:vallencia@easyport.cc">vallencia@easyport.cc</a></span>
            <span><strong>Website:</strong> <a href="https://easyport.cc" target="_blank" rel="noopener noreferrer">https://easyport.cc</a></span>
          </div>
        </div>

        <div class="contact-cta">
          <a class="btn-primary" href="mailto:vallencia@easyport.cc?subject=Easyport%20x%20Google%20Cloud%20Inquiry">
            <span>Contact Easyport</span>
            <span class="btn-icon">✉</span>
          </a>
          <a class="btn-ghost" href="#top">
            <span>Back to top</span>
          </a>
          <small style="color:#e5e7eb;">Preferred deployment: Google Cloud • Vertex AI • BigQuery • Cloud Run</small>
        </div>
      </div>
    </section>

  </main>

  <footer>
    <div class="footer-inner">
      <span>© <span id="year"></span> Easyport. All rights reserved.</span>
      <span>Built for freight forwarders • Powered by Google Cloud.</span>
    </div>
  </footer>
</div>

<script>
  // simple dynamic year
  document.getElementById("year").textContent = new Date().getFullYear();

  // smooth scroll for internal links
  document.querySelectorAll('a[href^="#"]').forEach(function (anchor) {
    anchor.addEventListener("click", function (e) {
      const href = this.getAttribute("href");
      if (href.length > 1) {
        e.preventDefault();
        const target = document.querySelector(href);
        if (target) {
          window.scrollTo({
            top: target.offsetTop - 76,
            behavior: "smooth"
          });
        }
      }
    });
  });
</script>
</body>
</html>
