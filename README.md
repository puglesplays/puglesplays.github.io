<!doctype html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>ClassConnect (SG) — Demo</title>
  <style>
    :root{
      --bg:#0b1220;
      --card:#121b2f;
      --card2:#0f1730;
      --text:#e8eefc;
      --muted:#a9b6d3;
      --line:#223155;
      --accent:#7c5cff;
      --accent2:#22c55e;
      --danger:#ef4444;
      --shadow: 0 10px 30px rgba(0,0,0,.35);
      --radius: 18px;
    }
    *{box-sizing:border-box}
    body{
      margin:0;
      font-family: ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, Helvetica, Arial, "Apple Color Emoji","Segoe UI Emoji";
      background: radial-gradient(1200px 800px at 20% -10%, #1a2a55 0%, var(--bg) 55%), var(--bg);
      color:var(--text);
      min-height:100vh;
    }
    .container{
      max-width: 980px;
      margin: 0 auto;
      padding: 22px 16px 60px;
    }
    .topbar{
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap:12px;
      padding: 10px 2px 14px;
      position: sticky;
      top: 0;
      backdrop-filter: blur(10px);
      background: rgba(11,18,32,.65);
      border-bottom: 1px solid rgba(34,49,85,.35);
      z-index: 10;
    }
    .brand{
      display:flex;
      align-items:center;
      gap:12px;
    }
    .logo{
      width: 40px;
      height: 40px;
      border-radius: 14px;
      background: linear-gradient(135deg, var(--accent), #39b7ff);
      box-shadow: var(--shadow);
    }
    .brand h1{
      margin:0;
      font-size: 18px;
      letter-spacing:.2px;
      font-weight: 800;
      line-height: 1.1;
    }
    .brand .sub{
      display:block;
      margin-top:2px;
      color: var(--muted);
      font-weight: 600;
      font-size: 12px;
    }
    .right{
      display:flex;
      align-items:center;
      gap:10px;
    }
    .pill{
      display:flex;
      align-items:center;
      gap:8px;
      padding: 9px 12px;
      background: rgba(18,27,47,.7);
      border: 1px solid rgba(34,49,85,.55);
      border-radius: 999px;
      color: var(--muted);
      font-weight: 650;
      font-size: 13px;
      white-space: nowrap;
    }
    .btn{
      border:0;
      cursor:pointer;
      border-radius: 999px;
      padding: 10px 14px;
      font-weight: 800;
      color: var(--text);
      background: rgba(18,27,47,.9);
      border: 1px solid rgba(34,49,85,.8);
      transition: transform .05s ease, background .15s ease, border-color .15s ease;
    }
    .btn:active{transform: translateY(1px)}
    .btn.primary{
      background: linear-gradient(135deg, var(--accent), #39b7ff);
      border-color: transparent;
    }
    .btn.success{
      background: linear-gradient(135deg, var(--accent2), #16a34a);
      border-color: transparent;
    }
    .btn.danger{
      background: rgba(239,68,68,.12);
      border: 1px solid rgba(239,68,68,.55);
      color: #fecaca;
    }

    .header{
      display:flex;
      align-items:flex-end;
      justify-content:space-between;
      flex-wrap: wrap;
      gap: 12px;
      margin-top: 14px;
    }
    .header h2{
      margin:0;
      font-size: 22px;
      font-weight: 900;
      letter-spacing:.2px;
    }
    .header p{
      margin: 6px 0 0;
      color: var(--muted);
      font-weight: 600;
      font-size: 13px;
    }
    .controls{
      display:flex;
      gap: 10px;
      flex-wrap: wrap;
      align-items:center;
      justify-content:flex-end;
    }
    .input{
      background: rgba(18,27,47,.7);
      border: 1px solid rgba(34,49,85,.8);
      color: var(--text);
      border-radius: 999px;
      padding: 10px 12px;
      min-width: 240px;
      outline: none;
      font-weight: 650;
    }
    .chips{
      display:flex;
      gap: 8px;
      flex-wrap: wrap;
    }
    .chip{
      cursor:pointer;
      user-select:none;
      padding: 9px 12px;
      border-radius: 999px;
      border: 1px solid rgba(34,49,85,.8);
      background: rgba(18,27,47,.6);
      color: var(--muted);
      font-weight: 800;
      font-size: 12px;
      transition: background .15s ease, color .15s ease, border-color .15s ease;
    }
    .chip.active{
      background: rgba(124,92,255,.18);
      border-color: rgba(124,92,255,.55);
      color: var(--text);
    }

    .grid{
      display:grid;
      grid-template-columns: repeat(12, 1fr);
      gap: 14px;
      margin-top: 18px;
    }
    .card{
      grid-column: span 12;
      background: linear-gradient(180deg, rgba(18,27,47,.85), rgba(18,27,47,.55));
      border: 1px solid rgba(34,49,85,.7);
      border-radius: var(--radius);
      padding: 14px;
      box-shadow: var(--shadow);
      display:flex;
      gap: 14px;
      align-items: stretch;
    }
    @media (min-width: 740px){
      .card{grid-column: span 6;}
    }
    .badge{
      display:inline-flex;
      align-items:center;
      gap:6px;
      padding: 6px 10px;
      border-radius: 999px;
      font-size: 12px;
      font-weight: 900;
      border: 1px solid rgba(34,49,85,.7);
      color: var(--muted);
      background: rgba(15,23,48,.55);
    }
    .badge.green{
      border-color: rgba(34,197,94,.5);
      background: rgba(34,197,94,.12);
      color: #bbf7d0;
    }
    .badge.type{
      border-color: rgba(124,92,255,.55);
      background: rgba(124,92,255,.12);
      color: #ddd6fe;
    }
    .leftcol{
      width: 54px;
      flex: 0 0 54px;
      display:flex;
      align-items:flex-start;
      justify-content:center;
    }
    .icon{
      width: 46px;
      height: 46px;
      border-radius: 16px;
      background: rgba(124,92,255,.16);
      border: 1px solid rgba(124,92,255,.35);
      display:flex;
      align-items:center;
      justify-content:center;
      font-size: 20px;
    }
    .content{
      flex: 1 1 auto;
      min-width: 0;
    }
    .titleRow{
      display:flex;
      align-items:flex-start;
      justify-content:space-between;
      gap: 10px;
    }
    .content h3{
      margin:0;
      font-size: 16px;
      font-weight: 950;
      letter-spacing:.2px;
    }
    .meta{
      margin-top: 6px;
      display:flex;
      flex-wrap: wrap;
      gap: 8px;
    }
    .desc{
      margin: 10px 0 0;
      color: var(--muted);
      font-weight: 650;
      font-size: 13px;
      line-height: 1.35;
    }
    .actions{
      display:flex;
      gap: 8px;
      margin-top: 12px;
      flex-wrap: wrap;
    }

    /* Modal */
    .overlay{
      position: fixed;
      inset: 0;
      background: rgba(0,0,0,.55);
      display:none;
      align-items:center;
      justify-content:center;
      padding: 18px;
      z-index: 50;
    }
    .overlay.show{display:flex;}
    .modal{
      width: min(720px, 100%);
      border-radius: 22px;
      background: linear-gradient(180deg, rgba(18,27,47,.98), rgba(15,23,48,.96));
      border: 1px solid rgba(34,49,85,.9);
      box-shadow: 0 20px 60px rgba(0,0,0,.5);
      overflow:hidden;
    }
    .modalHeader{
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap: 10px;
      padding: 14px 16px;
      border-bottom: 1px solid rgba(34,49,85,.7);
    }
    .modalHeader h3{
      margin:0;
      font-size: 16px;
      font-weight: 950;
    }
    .modalBody{
      padding: 16px;
    }
    .twoCol{
      display:grid;
      grid-template-columns: 1fr;
      gap: 12px;
    }
    @media (min-width: 740px){
      .twoCol{grid-template-columns: 1.2fr .8fr;}
    }
    .panel{
      border: 1px solid rgba(34,49,85,.75);
      background: rgba(11,18,32,.35);
      border-radius: 18px;
      padding: 14px;
    }
    .kv{
      display:grid;
      grid-template-columns: 120px 1fr;
      gap: 10px 12px;
      margin-top: 6px;
      font-weight: 700;
      color: var(--muted);
      font-size: 13px;
    }
    .kv div:nth-child(2n){
      color: var(--text);
      font-weight: 850;
    }
    .modalFooter{
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap: 10px;
      padding: 14px 16px;
      border-top: 1px solid rgba(34,49,85,.7);
      flex-wrap: wrap;
    }
    .note{
      color: var(--muted);
      font-weight: 650;
      font-size: 12px;
    }

    /* Toast */
    .toast{
      position: fixed;
      left: 50%;
      transform: translateX(-50%);
      bottom: 16px;
      width: min(720px, calc(100% - 28px));
      border-radius: 18px;
      background: rgba(18,27,47,.95);
      border: 1px solid rgba(34,49,85,.9);
      box-shadow: var(--shadow);
      padding: 12px 14px;
      display:none;
      gap: 10px;
      align-items:flex-start;
      z-index: 80;
    }
    .toast.show{display:flex;}
    .toast strong{font-weight: 950;}
    .toast p{margin:2px 0 0; color: var(--muted); font-weight: 650; font-size: 13px;}
    .toast .x{
      margin-left:auto;
      background: transparent;
      border: 0;
      color: var(--muted);
      cursor:pointer;
      font-size: 16px;
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="topbar">
      <div class="brand">
        <div class="logo" aria-hidden="true"></div>
        <div>
          <h1>ClassConnect (SG) <span class="sub">Demo — browse classes, register, see time & location</span></h1>
        </div>
      </div>

      <div class="right">
        <div class="pill" id="greeting">Welcome, Guest</div>
        <button class="btn" id="loginBtn">Login</button>
        <button class="btn danger" id="logoutBtn" style="display:none;">Logout</button>
      </div>
    </div>

    <div class="header">
      <div>
        <h2>Class List</h2>
        <p>Search + filter, then hit <b>Register</b> to view <b>time</b>, <b>location</b>, and <b>class type</b>.</p>
      </div>

      <div class="controls">
        <input class="input" id="searchInput" placeholder="Search classes (e.g., chemistry, economics, art)..." />
        <div class="chips" id="chips"></div>
      </div>
    </div>

    <div class="grid" id="classGrid"></div>
  </div>

  <!-- Class Details / Register Modal -->
  <div class="overlay" id="classModal">
    <div class="modal" role="dialog" aria-modal="true" aria-labelledby="classModalTitle">
      <div class="modalHeader">
        <h3 id="classModalTitle">Class Details</h3>
        <button class="btn" id="closeClassModal">Close</button>
      </div>
      <div class="modalBody">
        <div class="twoCol">
          <div class="panel">
            <div style="display:flex; align-items:center; justify-content:space-between; gap:10px;">
              <div>
                <div style="display:flex; flex-wrap:wrap; gap:8px;">
                  <span class="badge" id="classCategoryBadge">Category</span>
                  <span class="badge type" id="classTypeBadge">Type</span>
                </div>
                <h2 id="classTitle" style="margin:10px 0 0; font-size:22px; font-weight:950;">Title</h2>
                <p id="classDesc" class="desc" style="margin-top:8px;">Description</p>
              </div>
              <div class="icon" id="classIcon" aria-hidden="true">📚</div>
            </div>
          </div>

          <div class="panel">
            <div class="badge" style="margin-bottom:10px;">Session Info</div>
            <div class="kv">
              <div>When</div><div id="classWhen">—</div>
              <div>Duration</div><div id="classDuration">—</div>
              <div>Where</div><div id="classWhere">—</div>
              <div>Address</div><div id="classAddress">—</div>
              <div>Nearest MRT</div><div id="classMRT">—</div>
              <div>Class type</div><div id="classType">—</div>
            </div>
            <div style="margin-top:12px; display:flex; gap:8px; flex-wrap:wrap;">
              <button class="btn" id="mapBtn">Map (demo)</button>
              <button class="btn" id="calendarBtn">Add to Calendar (demo)</button>
            </div>
          </div>
        </div>
      </div>
      <div class="modalFooter">
        <div class="note" id="registerNote">Log in to confirm registration (demo only).</div>
        <div style="display:flex; gap:10px; flex-wrap:wrap;">
          <button class="btn" id="detailsOnlyBtn">Back</button>
          <button class="btn success" id="confirmRegisterBtn">Confirm Registration</button>
        </div>
      </div>
    </div>
  </div>

  <!-- Login Modal -->
  <div class="overlay" id="loginModal">
    <div class="modal" role="dialog" aria-modal="true" aria-labelledby="loginTitle">
      <div class="modalHeader">
        <h3 id="loginTitle">Login (Demo)</h3>
        <button class="btn" id="closeLoginModal">Close</button>
      </div>
      <div class="modalBody">
        <div class="panel">
          <p class="desc" style="margin-top:0;">
            This is a demo login. Nothing is saved. It only changes the displayed name (e.g., <b>Student #12</b>).
          </p>
          <div style="display:grid; gap:10px; margin-top:12px;">
            <label style="font-weight:850; color:var(--muted); font-size:13px;">Student number</label>
            <input class="input" id="studentNumber" inputmode="numeric" placeholder="e.g., 12" style="min-width:unset;" />
            <button class="btn primary" id="doLoginBtn">Log in</button>
          </div>
        </div>
      </div>
      <div class="modalFooter">
        <div class="note">No password, no storage, no accounts — display only.</div>
      </div>
    </div>
  </div>

  <!-- Toast -->
  <div class="toast" id="toast">
    <div id="toastIcon" style="font-size:18px; line-height:1;">✅</div>
    <div>
      <strong id="toastTitle">Saved</strong>
      <p id="toastMsg">Message</p>
    </div>
    <button class="x" id="toastClose" aria-label="Close">✕</button>
  </div>

  <script>
    // -------------------------
    // Demo data: practical high-school schedule style (with electives)
    // classType: "Lecture-based" | "Project-based" | "Mixed"
    // -------------------------
    const classes = [
      {
        id: "eng-11",
        title: "English Language Arts 11",
        category: "Core",
        classType: "Lecture-based",
        durationMins: 60,
        description: "Reading strategies, essay writing, and discussion-based analysis of texts.",
        when: "Mon 08:00–09:00",
        where: "School Campus (Block B, Level 3)",
        address: "Demo address: 1 School Way, Singapore 000001",
        mrt: "Nearest MRT (demo)",
        icon: "📚",
      },
      {
        id: "math-adv",
        title: "Additional Mathematics",
        category: "Core",
        classType: "Mixed",
        durationMins: 60,
        description: "Functions, calculus fundamentals, and problem-solving practice with weekly quizzes.",
        when: "Tue 09:30–10:30",
        where: "School Campus (Block A, Level 2)",
        address: "Demo address: 1 School Way, Singapore 000001",
        mrt: "Nearest MRT (demo)",
        icon: "➗",
      },
      {
        id: "chem",
        title: "Chemistry",
        category: "Science",
        classType: "Mixed",
        durationMins: 75,
        description: "Core concepts + practical labs (acid-base, kinetics, and basic titrations).",
        when: "Wed 10:45–12:00",
        where: "Science Lab 2 (School Campus)",
        address: "Demo address: 1 School Way, Singapore 000001",
        mrt: "Nearest MRT (demo)",
        icon: "🧪",
      },
      {
        id: "bio",
        title: "Biology",
        category: "Science",
        classType: "Mixed",
        durationMins: 75,
        description: "Cell processes, genetics, and ecology with structured lab write-ups.",
        when: "Thu 08:00–09:15",
        where: "Science Lab 1 (School Campus)",
        address: "Demo address: 1 School Way, Singapore 000001",
        mrt: "Nearest MRT (demo)",
        icon: "🧬",
      },
      {
        id: "econ",
        title: "Economics",
        category: "Humanities",
        classType: "Lecture-based",
        durationMins: 60,
        description: "Micro + macro foundations, case studies, and evaluation of real-world policies.",
        when: "Fri 09:30–10:30",
        where: "School Campus (Seminar Room 4)",
        address: "Demo address: 1 School Way, Singapore 000001",
        mrt: "Nearest MRT (demo)",
        icon: "📈",
      },
      {
        id: "cs",
        title: "Computer Science (Intro)",
        category: "Elective",
        classType: "Project-based",
        durationMins: 90,
        description: "Build small apps and games while learning logic, variables, and debugging.",
        when: "Tue 15:00–16:30",
        where: "Computer Lab (School Campus)",
        address: "Demo address: 1 School Way, Singapore 000001",
        mrt: "Nearest MRT (demo)",
        icon: "💻",
      },
      {
        id: "design",
        title: "Design & Technology",
        category: "Elective",
        classType: "Project-based",
        durationMins: 90,
        description: "Prototype design challenges (CAD, basic fabrication, and testing).",
        when: "Thu 15:00–16:30",
        where: "Design Studio (School Campus)",
        address: "Demo address: 1 School Way, Singapore 000001",
        mrt: "Nearest MRT (demo)",
        icon: "🛠️",
      },
      {
        id: "art",
        title: "Visual Art",
        category: "Elective",
        classType: "Project-based",
        durationMins: 75,
        description: "Studio projects (drawing, painting, and mixed media) with critique sessions.",
        when: "Mon 14:00–15:15",
        where: "Art Room (School Campus)",
        address: "Demo address: 1 School Way, Singapore 000001",
        mrt: "Nearest MRT (demo)",
        icon: "🎨",
      },
      {
        id: "band",
        title: "Concert Band",
        category: "CCA / Elective",
        classType: "Mixed",
        durationMins: 90,
        description: "Sectionals + full ensemble rehearsals focused on performance readiness.",
        when: "Wed 15:00–16:30",
        where: "Music Room (School Campus)",
        address: "Demo address: 1 School Way, Singapore 000001",
        mrt: "Nearest MRT (demo)",
        icon: "🎼",
      },
      {
        id: "pe",
        title: "Physical Education",
        category: "Core",
        classType: "Project-based",
        durationMins: 60,
        description: "Skill practice + fitness tracking (performance tasks and reflection logs).",
        when: "Fri 14:00–15:00",
        where: "School Sports Hall",
        address: "Demo address: 1 School Way, Singapore 000001",
        mrt: "Nearest MRT (demo)",
        icon: "🏃",
      },
      {
        id: "media",
        title: "Media Studies",
        category: "Elective",
        classType: "Mixed",
        durationMins: 75,
        description: "Analyze media texts and create short-form content with peer feedback.",
        when: "Tue 13:00–14:15",
        where: "Seminar Room 2 (School Campus)",
        address: "Demo address: 1 School Way, Singapore 000001",
        mrt: "Nearest MRT (demo)",
        icon: "🎬",
      }
    ];

    // In-memory session (NO saving)
    const session = { isLoggedIn: false, displayName: "Guest" };

    // In-memory registrations (demo feel)
    const registeredIds = new Set();

    const state = {
      selectedCategory: "All",
      selectedType: "All", // NEW: filters by classType
      search: "",
      activeClass: null
    };

    // Elements
    const classGrid = document.getElementById("classGrid");
    const greeting = document.getElementById("greeting");

    const loginBtn = document.getElementById("loginBtn");
    const logoutBtn = document.getElementById("logoutBtn");

    const searchInput = document.getElementById("searchInput");
    const chipsEl = document.getElementById("chips");

    const classModal = document.getElementById("classModal");
    const closeClassModal = document.getElementById("closeClassModal");
    const detailsOnlyBtn = document.getElementById("detailsOnlyBtn");
    const confirmRegisterBtn = document.getElementById("confirmRegisterBtn");
    const registerNote = document.getElementById("registerNote");

    const classCategoryBadge = document.getElementById("classCategoryBadge");
    const classTypeBadge = document.getElementById("classTypeBadge");
    const classTitle = document.getElementById("classTitle");
    const classDesc = document.getElementById("classDesc");
    const classIcon = document.getElementById("classIcon");
    const classWhen = document.getElementById("classWhen");
    const classDuration = document.getElementById("classDuration");
    const classWhere = document.getElementById("classWhere");
    const classAddress = document.getElementById("classAddress");
    const classMRT = document.getElementById("classMRT");
    const classType = document.getElementById("classType");
    const mapBtn = document.getElementById("mapBtn");
    const calendarBtn = document.getElementById("calendarBtn");

    const loginModal = document.getElementById("loginModal");
    const closeLoginModal = document.getElementById("closeLoginModal");
    const studentNumber = document.getElementById("studentNumber");
    const doLoginBtn = document.getElementById("doLoginBtn");

    const toast = document.getElementById("toast");
    const toastTitle = document.getElementById("toastTitle");
    const toastMsg = document.getElementById("toastMsg");
    const toastClose = document.getElementById("toastClose");
    const toastIcon = document.getElementById("toastIcon");

    // Helpers
    function showToast(title, msg, icon="✅"){
      toastTitle.textContent = title;
      toastMsg.textContent = msg;
      toastIcon.textContent = icon;
      toast.classList.add("show");
      clearTimeout(showToast._t);
      showToast._t = setTimeout(() => toast.classList.remove("show"), 3500);
    }

    function openOverlay(el){ el.classList.add("show"); }
    function closeOverlay(el){ el.classList.remove("show"); }

    function updateTopRight(){
      greeting.textContent = `Welcome, ${session.displayName}`;
      if(session.isLoggedIn){
        loginBtn.style.display = "none";
        logoutBtn.style.display = "inline-block";
      }else{
        loginBtn.style.display = "inline-block";
        logoutBtn.style.display = "none";
      }
    }

    // NEW: combined chips for Category + Type
    function getCategories(){
      const set = new Set(classes.map(c => c.category));
      return ["All", ...Array.from(set).sort()];
    }
    function getTypes(){
      return ["All", "Project-based", "Lecture-based", "Mixed"];
    }

    function renderChips(){
      chipsEl.innerHTML = "";

      // Row 1: Category chips
      const catWrap = document.createElement("div");
      catWrap.className = "chips";
      catWrap.style.width = "100%";

      getCategories().forEach(cat => {
        const chip = document.createElement("div");
        chip.className = "chip" + (state.selectedCategory === cat ? " active" : "");
        chip.textContent = cat;
        chip.title = "Filter by category";
        chip.addEventListener("click", () => {
          state.selectedCategory = cat;
          renderChips();
          renderGrid();
        });
        catWrap.appendChild(chip);
      });

      // Row 2: Type chips
      const typeWrap = document.createElement("div");
      typeWrap.className = "chips";
      typeWrap.style.width = "100%";
      typeWrap.style.marginTop = "8px";

      getTypes().forEach(t => {
        const chip = document.createElement("div");
        chip.className = "chip" + (state.selectedType === t ? " active" : "");
        chip.textContent = t;
        chip.title = "Filter by class type";
        chip.addEventListener("click", () => {
          state.selectedType = t;
          renderChips();
          renderGrid();
        });
        typeWrap.appendChild(chip);
      });

      chipsEl.appendChild(catWrap);
      chipsEl.appendChild(typeWrap);
    }

    function matchesFilters(c){
      const catOk = state.selectedCategory === "All" || c.category === state.selectedCategory;
      const typeOk = state.selectedType === "All" || c.classType === state.selectedType;

      const q = state.search.trim().toLowerCase();
      const text = (c.title + " " + c.category + " " + c.classType + " " + c.description + " " + c.where).toLowerCase();
      const searchOk = q === "" || text.includes(q);

      return catOk && typeOk && searchOk;
    }

    function renderGrid(){
      classGrid.innerHTML = "";
      const filtered = classes.filter(matchesFilters);

      if(filtered.length === 0){
        const empty = document.createElement("div");
        empty.className = "card";
        empty.style.gridColumn = "span 12";
        empty.innerHTML = `
          <div class="content">
            <h3>No classes found</h3>
            <p class="desc">Try a different search term, category, or class type filter.</p>
          </div>
        `;
        classGrid.appendChild(empty);
        return;
      }

      filtered.forEach(c => {
        const isReg = registeredIds.has(c.id);
        const card = document.createElement("div");
        card.className = "card";

        card.innerHTML = `
          <div class="leftcol">
            <div class="icon" aria-hidden="true">${c.icon}</div>
          </div>
          <div class="content">
            <div class="titleRow">
              <div style="min-width:0;">
                <h3 title="${c.title}">${c.title}</h3>
                <div class="meta">
                  <span class="badge">${c.category}</span>
                  <span class="badge type">🧩 ${c.classType}</span>
                  <span class="badge">⏱ ${c.durationMins} min</span>
                  <span class="badge">🗓 ${c.when}</span>
                  ${isReg ? `<span class="badge green">✅ Registered</span>` : ``}
                </div>
              </div>
            </div>
            <p class="desc">${c.description}</p>
            <div class="actions">
              <button class="btn primary" data-action="register">Register</button>
              <button class="btn" data-action="details">Details</button>
            </div>
          </div>
        `;

        card.querySelector('[data-action="register"]').addEventListener("click", () => openClassModal(c));
        card.querySelector('[data-action="details"]').addEventListener("click", () => openClassModal(c));

        classGrid.appendChild(card);
      });
    }

    function openClassModal(c){
      state.activeClass = c;

      classCategoryBadge.textContent = c.category;
      classTypeBadge.textContent = c.classType;

      classTitle.textContent = c.title;
      classDesc.textContent = c.description;
      classIcon.textContent = c.icon;

      classWhen.textContent = c.when;
      classDuration.textContent = `${c.durationMins} minutes`;
      classWhere.textContent = c.where;
      classAddress.textContent = c.address;
      classMRT.textContent = c.mrt;

      // NEW: show in session info
      classType.textContent = c.classType;

      const isReg = registeredIds.has(c.id);

      if(isReg){
        registerNote.textContent = "You are already registered for this class (demo session).";
        confirmRegisterBtn.textContent = "Registered";
        confirmRegisterBtn.disabled = true;
        confirmRegisterBtn.style.opacity = 0.7;
      }else{
        confirmRegisterBtn.textContent = "Confirm Registration";
        confirmRegisterBtn.disabled = false;
        confirmRegisterBtn.style.opacity = 1;

        registerNote.textContent = session.isLoggedIn
          ? `Logged in as ${session.displayName}. Confirm to register (demo).`
          : "Log in to confirm registration (demo only).";
      }

      openOverlay(classModal);
    }

    // Events
    searchInput.addEventListener("input", (e) => {
      state.search = e.target.value || "";
      renderGrid();
    });

    loginBtn.addEventListener("click", () => {
      studentNumber.value = "";
      openOverlay(loginModal);
      setTimeout(() => studentNumber.focus(), 0);
    });

    logoutBtn.addEventListener("click", () => {
      session.isLoggedIn = false;
      session.displayName = "Guest";
      updateTopRight();
      showToast("Logged out", "Back to Guest (nothing saved).", "👋");
      if(classModal.classList.contains("show") && state.activeClass){
        openClassModal(state.activeClass);
      }
    });

    doLoginBtn.addEventListener("click", () => {
      const raw = (studentNumber.value || "").trim();
      const num = raw.replace(/[^\d]/g, "");
      if(!num){
        showToast("Login needed", "Please enter a student number (e.g., 12).", "⚠️");
        return;
      }
      session.isLoggedIn = true;
      session.displayName = `Student #${num}`;
      updateTopRight();
      closeOverlay(loginModal);
      showToast("Logged in", `Welcome, ${session.displayName} (demo only).`, "✅");

      if(classModal.classList.contains("show") && state.activeClass){
        openClassModal(state.activeClass);
      }
    });

    closeLoginModal.addEventListener("click", () => closeOverlay(loginModal));

    closeClassModal.addEventListener("click", () => closeOverlay(classModal));
    detailsOnlyBtn.addEventListener("click", () => closeOverlay(classModal));

    [classModal, loginModal].forEach(overlay => {
      overlay.addEventListener("click", (e) => {
        if(e.target === overlay) closeOverlay(overlay);
      });
    });

    document.addEventListener("keydown", (e) => {
      if(e.key === "Escape"){
        closeOverlay(classModal);
        closeOverlay(loginModal);
        toast.classList.remove("show");
      }
    });

    confirmRegisterBtn.addEventListener("click", () => {
      const c = state.activeClass;
      if(!c) return;

      if(!session.isLoggedIn){
        showToast("Login required", "Please log in to register (demo).", "🔒");
        return;
      }
      if(registeredIds.has(c.id)){
        showToast("Already registered", "You already registered in this demo session.", "✅");
        return;
      }

      registeredIds.add(c.id);
      showToast("Registered!", `See you ${c.when} @ ${c.where}.`, "🎉");

      openClassModal(c);
      renderGrid();
    });

    mapBtn.addEventListener("click", () => {
      const c = state.activeClass;
      if(!c) return;
      const q = encodeURIComponent(`${c.where} ${c.address}`);
      window.open(`https://www.google.com/maps/search/?api=1&query=${q}`, "_blank");
      showToast("Map opened", "Opened location in a new tab (demo).", "🗺️");
    });

    calendarBtn.addEventListener("click", () => {
      showToast("Calendar (demo)", "This button is a placeholder for calendar integration.", "📅");
    });

    toastClose.addEventListener("click", () => toast.classList.remove("show"));

    // Init
    updateTopRight();
    renderChips();
    renderGrid();
  </script>
</body>
</html>
