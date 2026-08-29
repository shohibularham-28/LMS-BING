<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>LMS Bahasa Inggris Mr. Hanif</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Lora:wght@500;600;700&family=Inter:wght@400;500;600;700&family=IBM+Plex+Mono:wght@500;600&display=swap" rel="stylesheet">
<style>
  :root{
    --ink:#1F2A44;
    --ink-soft:#3B4252;
    --paper:#FBF9F4;
    --paper-line:#E7E2D6;
    --mustard:#D9A441;
    --mustard-dark:#B9832C;
    --sage:#5B8266;
    --sage-bg:#EAF1EA;
    --clay:#B4533C;
    --clay-bg:#F6E9E5;
    --card:#FFFFFF;
    --shadow: 0 6px 20px rgba(31,42,68,0.08);
    --radius: 14px;
  }
  *{box-sizing:border-box;}
  html,body{height:100%;}
  body{
    margin:0;
    background:var(--paper);
    color:var(--ink-soft);
    font-family:'Inter',sans-serif;
    -webkit-font-smoothing:antialiased;
  }
  h1,h2,h3{font-family:'Lora',serif; color:var(--ink); margin:0 0 8px;}
  .mono{font-family:'IBM Plex Mono',monospace; letter-spacing:.04em;}
  button{font-family:'Inter',sans-serif; cursor:pointer;}
  #app{min-height:100vh; display:flex; flex-direction:column;}

  /* ===== Top bar ===== */
  .topbar{
    background:var(--ink);
    color:#F3EFE4;
    padding:16px 24px;
    display:flex;
    align-items:center;
    justify-content:space-between;
  }
  .topbar .brand{display:flex; align-items:center; gap:10px;}
  .brand .mark{
    width:34px;height:34px;border-radius:9px;
    background:var(--mustard);
    display:flex;align-items:center;justify-content:center;
    font-family:'Lora',serif; font-weight:700; color:var(--ink); font-size:16px;
  }
  .brand-text{line-height:1.15;}
  .brand-text .name{font-family:'Lora',serif; font-size:16px; font-weight:600;}
  .brand-text .role{font-size:11px; opacity:.7; font-family:'IBM Plex Mono',monospace;}
  .topbar .who{display:flex; align-items:center; gap:14px; font-size:13px;}
  .logout-btn{
    background:transparent; border:1px solid rgba(243,239,228,.35); color:#F3EFE4;
    padding:7px 14px; border-radius:8px; font-size:13px;
  }
  .logout-btn:hover{background:rgba(243,239,228,.12);}

  main{flex:1; display:flex; justify-content:center; padding:32px 20px 60px;}
  .container{width:100%; max-width:920px;}

  /* ===== Login ===== */
  .login-wrap{
    flex:1; display:flex; align-items:center; justify-content:center; padding:24px;
  }
  .login-card{
    background:var(--card);
    border-radius:20px;
    box-shadow:var(--shadow);
    width:100%; max-width:420px;
    padding:36px 32px 32px;
    border-top:6px solid var(--mustard);
    position:relative;
  }
  .login-card .mark-big{
    width:48px;height:48px;border-radius:12px;background:var(--ink);
    display:flex;align-items:center;justify-content:center; margin-bottom:16px;
    font-family:'Lora',serif;font-weight:700;color:var(--mustard);font-size:20px;
  }
  .login-card h1{font-size:22px;}
  .login-card p.sub{font-size:13px; color:#7C8398; margin-bottom:24px;}
  .field{margin-bottom:16px;}
  .field label{display:block; font-size:12px; font-weight:600; color:var(--ink); margin-bottom:6px; text-transform:uppercase; letter-spacing:.03em;}
  .field input{
    width:100%; padding:11px 13px; border:1.5px solid var(--paper-line); border-radius:9px;
    font-size:14px; background:#FDFCF9; color:var(--ink);
  }
  .field input:focus{outline:none; border-color:var(--mustard);}
  .field select{
    width:100%; padding:11px 13px; border:1.5px solid var(--paper-line); border-radius:9px;
    font-size:14px; background:#FDFCF9; color:var(--ink); font-family:'Inter',sans-serif;
    appearance:none; -webkit-appearance:none;
    background-image:url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='14' height='9'><path d='M1 1l6 6 6-6' stroke='%237C8398' stroke-width='1.6' fill='none' fill-rule='evenodd'/></svg>");
    background-repeat:no-repeat; background-position:right 14px center;
  }
  .field select:focus{outline:none; border-color:var(--mustard);}
  .role-toggle{
    display:flex; gap:6px; background:#F1EEE3; padding:4px; border-radius:11px; margin-bottom:22px;
  }
  .role-btn{
    flex:1; border:none; background:transparent; padding:9px 10px; border-radius:8px;
    font-size:12.5px; font-weight:600; color:#8A8F9F;
  }
  .role-btn.active{background:var(--ink); color:#F3EFE4;}
  .btn-primary{
    width:100%; background:var(--ink); color:#F3EFE4; border:none; padding:12px;
    border-radius:9px; font-size:14px; font-weight:600; margin-top:6px;
  }
  .btn-primary:hover{background:#141B2E;}
  .login-error{
    background:var(--clay-bg); color:var(--clay); font-size:12.5px; padding:9px 12px;
    border-radius:8px; margin-bottom:14px; display:none;
  }

  /* ===== Cards / generic ===== */
  .card{
    background:var(--card); border-radius:var(--radius); box-shadow:var(--shadow);
    padding:26px 28px; margin-bottom:20px;
  }
  .eyebrow{
    font-family:'IBM Plex Mono',monospace; font-size:11px; letter-spacing:.08em;
    text-transform:uppercase; color:var(--mustard-dark); font-weight:600; margin-bottom:6px;
  }
  .badge{
    display:inline-flex; align-items:center; gap:6px; font-size:11.5px; font-weight:600;
    padding:4px 10px; border-radius:20px; font-family:'IBM Plex Mono',monospace;
  }
  .badge.gray{background:#EEEBE1; color:#7C8398;}
  .badge.mustard{background:#FBEED4; color:var(--mustard-dark);}
  .badge.sage{background:var(--sage-bg); color:var(--sage);}
  .badge.clay{background:var(--clay-bg); color:var(--clay);}

  .btn-mustard{
    background:var(--mustard); color:var(--ink); border:none; padding:11px 20px; border-radius:9px;
    font-size:13.5px; font-weight:700;
  }
  .btn-mustard:hover{background:var(--mustard-dark);}
  .btn-mustard:disabled{opacity:.55; cursor:not-allowed;}

  /* ===== Status panel (used by settings success message) ===== */
  .status-panel{
    display:flex; align-items:center; gap:14px; padding:18px 20px; border-radius:12px; margin-bottom:20px;
  }
  .status-panel.done{background:var(--sage-bg); border:1px solid #C7DCC9;}
  .status-icon{
    width:38px;height:38px;border-radius:50%; display:flex;align-items:center;justify-content:center;
    font-size:18px; flex-shrink:0;
  }
  .status-panel.done .status-icon{background:var(--sage); color:#fff;}
  .status-panel .stxt strong{display:block; font-size:14px; color:var(--ink); font-family:'Lora',serif;}
  .status-panel .stxt span{font-size:12.5px; color:#7C8398;}

  /* ===== Teacher dashboard ===== */
  .btn-small{
    background:var(--ink); color:#F3EFE4; border:none; padding:8px 14px; border-radius:8px; font-size:12.5px; font-weight:600;
  }
  .btn-small:disabled{background:#DEDBD0; color:#9AA0B4; cursor:not-allowed;}
  .back-link{
    background:none; border:none; color:#9AA0B4; font-size:13px; margin-bottom:14px; padding:0;
    display:flex; align-items:center; gap:6px; font-family:'Inter',sans-serif;
  }
  .back-link:hover{color:var(--ink);}

  .loading-note{font-size:13px; color:#9AA0B4; padding:20px 0;}

  /* ===== Home tiles (shared by assignment tiles) ===== */
  .tile-left{display:flex; align-items:center; gap:14px;}
  .tile-icon{
    width:42px; height:42px; border-radius:11px; background:var(--ink); color:var(--mustard);
    display:flex; align-items:center; justify-content:center; font-family:'Lora',serif; font-weight:700; font-size:17px;
  }
  .tile-title{font-family:'Lora',serif; font-weight:600; color:var(--ink); font-size:15px;}
  .tile-sub{font-size:12px; color:#9AA0B4; font-family:'IBM Plex Mono',monospace; margin-top:2px;}

  /* ===== Assignments ===== */
  .assignment-tile{
    display:flex; align-items:center; justify-content:space-between; gap:14px;
    padding:16px 18px; border:1.5px solid var(--paper-line); border-radius:13px;
  }
  .assignment-tile .tile-icon{background:var(--clay); color:#fff;}
  .assignment-actions{display:flex; align-items:center; gap:8px; flex-shrink:0;}
  .btn-danger-ghost{
    background:transparent; border:1.5px solid var(--clay); color:var(--clay);
    padding:8px 13px; border-radius:8px; font-size:12.5px; font-weight:600;
  }
  .btn-danger-ghost:hover{background:var(--clay-bg);}
  .empty-note{font-size:13px; color:#9AA0B4; padding:6px 2px;}

  .hidden{display:none !important;}
  ::-webkit-scrollbar{width:8px;}
  ::-webkit-scrollbar-thumb{background:#DDD3BB; border-radius:8px;}

  @media(max-width:600px){
    .card{padding:20px 18px;}
  }
</style>
</head>
<body>
<div id="app"></div>

<script>
/* ============ Static config ============ */
const USERS = {
  arhamhanif:{password:'guru123', role:'teacher', name:'Mr. Arham Hanif', title:'English Teacher'},
  Tia:{password:'siswa', role:'student', name:'Tia', title:'XI D1', class:'XI D1'}
};

const CLASS_OPTIONS = ['XI D1', 'XI D2', 'XI E1'];

function teacherUser(){
  const key = Object.keys(USERS).find(u => USERS[u].role === 'teacher');
  return USERS[key];
}

let session = null; // {username, role}

/* ============ Storage helpers (persist across reloads) ============ */
async function loadAssignments(){
  try{
    const res = await window.storage.get('assignments', true);
    if(res && res.value) return JSON.parse(res.value);
  }catch(e){ /* none saved yet */ }
  return [];
}

async function saveAssignments(list){
  try{
    await window.storage.set('assignments', JSON.stringify(list), true);
    return true;
  }catch(e){
    console.error('Could not save assignments:', e);
    return false;
  }
}

async function getEffectivePassword(username){
  try{
    const res = await window.storage.get('password:' + username, true);
    if(res && res.value) return res.value;
  }catch(e){ /* no override saved, use default */ }
  return USERS[username].password;
}

async function setPasswordOverride(username, newPassword){
  try{
    await window.storage.set('password:' + username, newPassword, true);
    return true;
  }catch(e){
    console.error('Could not save new password:', e);
    return false;
  }
}

/* ============ Helpers ============ */
function render(html){ document.getElementById('app').innerHTML = html; }
function fmtTime(ts){
  if(!ts) return '-';
  const d = new Date(ts);
  return d.toLocaleString('en-US',{day:'2-digit',month:'short',hour:'2-digit',minute:'2-digit'});
}
/* ============ LOGIN ============ */
let loginRole = 'student';

function renderLogin(){
  render(`
    <div class="login-wrap">
      <div class="login-card">
        <div class="mark-big">H</div>
        <h1>Sign In</h1>
        <p class="sub">Access your assignments, or review your students' work.</p>
        <div class="role-toggle">
          <button type="button" class="role-btn" data-role="student">Student Login</button>
          <button type="button" class="role-btn" data-role="teacher">Teacher Login</button>
        </div>
        <div class="login-error" id="loginError">Incorrect username, password, or class. Please try again.</div>
        <div id="loginFields"></div>
        <button class="btn-primary" id="loginBtn">Sign In</button>
      </div>
    </div>
  `);
  document.querySelectorAll('.role-btn').forEach(b=>{
    b.addEventListener('click', ()=>{ loginRole = b.getAttribute('data-role'); renderLoginFields(); });
  });
  document.getElementById('loginBtn').onclick = doLogin;
  renderLoginFields();
}

function renderLoginFields(){
  document.querySelectorAll('.role-btn').forEach(b=>{
    b.classList.toggle('active', b.getAttribute('data-role') === loginRole);
  });
  const container = document.getElementById('loginFields');
  let html = `
    <div class="field">
      <label for="uname">Username</label>
      <input id="uname" type="text" autocomplete="off">
    </div>
    <div class="field">
      <label for="pword">Password</label>
      <input id="pword" type="password">
    </div>
  `;
  if(loginRole === 'student'){
    const opts = CLASS_OPTIONS.map(c=>`<option value="${c}">${c}</option>`).join('');
    html += `
      <div class="field">
        <label for="uclass">Class</label>
        <select id="uclass">
          <option value="">Select your class</option>
          ${opts}
        </select>
      </div>
    `;
  }
  container.innerHTML = html;
  document.getElementById('loginError').style.display = 'none';
  container.querySelectorAll('input, select').forEach(f=>{
    f.addEventListener('keydown', e=>{ if(e.key==='Enter') doLogin(); });
  });
}

async function doLogin(){
  const u = document.getElementById('uname').value.trim();
  const p = document.getElementById('pword').value;
  const user = USERS[u];
  const errBox = document.getElementById('loginError');
  const loginBtn = document.getElementById('loginBtn');

  if(!user || user.role !== loginRole){
    errBox.style.display = 'block';
    return;
  }
  loginBtn.disabled = true;
  const effectivePassword = await getEffectivePassword(u);
  loginBtn.disabled = false;

  if(p !== effectivePassword){
    errBox.style.display = 'block';
    return;
  }
  if(loginRole === 'student'){
    const cls = document.getElementById('uclass').value;
    if(!cls || cls !== user.class){
      errBox.style.display = 'block';
      return;
    }
  }
  session = {username:u, role:user.role};
  if(user.role==='student') renderStudentApp();
  else renderTeacherApp();
}

function logout(){ session=null; renderLogin(); }

function topbar(roleLabel){
  const user = USERS[session.username];
  return `
    <div class="topbar">
      <div class="brand">
        <div class="mark">H</div>
        <div class="brand-text">
          <div class="name">LMS Bahasa Inggris Mr. Hanif</div>
          <div class="role">${roleLabel}</div>
        </div>
      </div>
      <div class="who">
        <span>${user.name} &middot; <span style="opacity:.7">${user.title}</span></span>
        ${session.role === 'student' ? `<button class="logout-btn" onclick="renderStudentSettings()">Settings</button>` : ''}
        <button class="logout-btn" onclick="logout()">Sign Out</button>
      </div>
    </div>
  `;
}

/* ============ STUDENT APP ============ */
async function renderStudentApp(){
  render(`
    <div id="app-inner">
      ${topbar('Student Learning Space')}
      <main><div class="container" id="studentMain"><p class="loading-note">Loading your progress...</p></div></main>
    </div>
  `);
  renderStudentHome();
}

async function renderStudentHome(){
  const main = document.getElementById('studentMain');
  main.innerHTML = `<p class="loading-note">Loading your assignments...</p>`;
  const assignments = await loadAssignments();

  const assignmentTiles = assignments.length === 0
    ? `<p class="empty-note">No assignments yet. Check back later.</p>`
    : assignments.slice().reverse().map(a => `
        <div class="assignment-tile">
          <div class="tile-left">
            <div class="tile-icon">T</div>
            <div>
              <div class="tile-title">${a.title}</div>
              <div class="tile-sub">Given ${fmtTime(a.createdAt)}</div>
            </div>
          </div>
          <button class="btn-mustard" data-open-assignment="${a.id}">Open</button>
        </div>
      `).join('');

  main.innerHTML = `
    <div class="eyebrow">Home</div>
    <h1 style="margin-bottom:4px;">Welcome, ${USERS[session.username].name}</h1>
    <p style="font-size:13px; color:#8A8F9F; margin-bottom:20px;">Here are the assignments your teacher has given.</p>
    <div class="eyebrow">Assignments</div>
    <div class="card" style="display:flex; flex-direction:column; gap:14px;">${assignmentTiles}</div>
  `;

  main.querySelectorAll('[data-open-assignment]').forEach(btn=>{
    btn.addEventListener('click', async ()=>{
      const id = btn.getAttribute('data-open-assignment');
      const list = await loadAssignments();
      const a = list.find(x=>x.id===id);
      if(a) renderStudentAssignmentView(a);
    });
  });
}

function renderStudentAssignmentView(assignment){
  const main = document.getElementById('studentMain');
  main.innerHTML = `
    <button class="back-link" onclick="renderStudentHome()">&larr; Back to Home</button>
    <div class="eyebrow">Assignment</div>
    <h1 style="margin-bottom:4px;">${assignment.title}</h1>
    <p style="font-size:13px; color:#8A8F9F; margin-bottom:20px;">Given ${fmtTime(assignment.createdAt)} by ${teacherUser().name}.</p>
    <div class="card" style="display:flex; flex-direction:column; gap:14px; align-items:flex-start;">
      <p style="font-size:13.5px; color:var(--ink-soft); margin:0; word-break:break-all;">${assignment.url}</p>
      <a class="btn-mustard" href="${assignment.url}" target="_blank" rel="noopener noreferrer" style="text-decoration:none; display:inline-block;">Open Assignment &#8599;</a>
    </div>
  `;
}

/* ---- Student settings: change password (available for every class) ---- */
function renderStudentSettings(){
  const main = document.getElementById('studentMain');
  main.innerHTML = `
    <button class="back-link" onclick="renderStudentHome()">&larr; Back to Home</button>
    <div class="eyebrow">Settings</div>
    <h1 style="margin-bottom:4px;">Change Password</h1>
    <p style="font-size:13px; color:#8A8F9F; margin-bottom:20px;">Update the password you use to sign in. This applies no matter which class you're in.</p>
    <div class="card" style="max-width:420px;">
      <div class="login-error" id="settingsError">Something went wrong. Please check the fields below.</div>
      <div class="status-panel done hidden" id="settingsSuccess" style="margin-bottom:18px;">
        <div class="status-icon">&#10003;</div>
        <div class="stxt"><strong>Password updated</strong><span>Use your new password next time you sign in.</span></div>
      </div>
      <div class="field">
        <label for="curPass">Current Password</label>
        <input id="curPass" type="password">
      </div>
      <div class="field">
        <label for="newPass">New Password</label>
        <input id="newPass" type="password">
      </div>
      <div class="field">
        <label for="confirmPass">Confirm New Password</label>
        <input id="confirmPass" type="password">
      </div>
      <button class="btn-primary" id="savePassBtn" style="margin-top:2px;">Save New Password</button>
    </div>
  `;

  document.getElementById('savePassBtn').onclick = async ()=>{
    const errBox = document.getElementById('settingsError');
    const successBox = document.getElementById('settingsSuccess');
    errBox.style.display = 'none';
    successBox.classList.add('hidden');

    const cur = document.getElementById('curPass').value;
    const next = document.getElementById('newPass').value;
    const confirm = document.getElementById('confirmPass').value;

    const effective = await getEffectivePassword(session.username);
    if(cur !== effective){
      errBox.textContent = 'Your current password is incorrect.';
      errBox.style.display = 'block';
      return;
    }
    if(!next || next.length < 4){
      errBox.textContent = 'New password must be at least 4 characters.';
      errBox.style.display = 'block';
      return;
    }
    if(next !== confirm){
      errBox.textContent = 'New password and confirmation do not match.';
      errBox.style.display = 'block';
      return;
    }

    const ok = await setPasswordOverride(session.username, next);
    if(!ok){
      errBox.textContent = 'Could not save your new password. Please try again.';
      errBox.style.display = 'block';
      return;
    }
    document.getElementById('curPass').value = '';
    document.getElementById('newPass').value = '';
    document.getElementById('confirmPass').value = '';
    successBox.classList.remove('hidden');
  };
}

/* ============ TEACHER APP ============ */
async function renderTeacherApp(){
  render(`
    <div id="app-inner">
      ${topbar('Teacher Workspace')}
      <main><div class="container" id="teacherMain"><p class="loading-note">Loading...</p></div></main>
    </div>
  `);
  renderTeacherHome();
}

async function renderTeacherHome(){
  const main = document.getElementById('teacherMain');
  main.innerHTML = `<p class="loading-note">Loading...</p>`;

  const assignments = await loadAssignments();
  const assignmentTiles = assignments.length === 0
    ? `<p class="empty-note">No assignments given yet.</p>`
    : assignments.slice().reverse().map(a => `
        <div class="assignment-tile">
          <div class="tile-left">
            <div class="tile-icon">T</div>
            <div>
              <div class="tile-title">${a.title}</div>
              <div class="tile-sub">Given ${fmtTime(a.createdAt)}</div>
            </div>
          </div>
          <div class="assignment-actions">
            <button class="btn-small" data-preview-assignment="${a.id}">Preview</button>
            <button class="btn-danger-ghost" data-delete-assignment="${a.id}">Delete</button>
          </div>
        </div>
      `).join('');

  main.innerHTML = `
    <div class="eyebrow">Home</div>
    <h1 style="margin-bottom:4px;">Welcome, ${USERS[session.username].name}</h1>
    <p style="font-size:13px; color:#8A8F9F; margin-bottom:20px;">Give assignments to your students and manage what's currently posted.</p>
    <div class="eyebrow">Assignments</div>
    <div class="card" style="display:flex; flex-direction:column; gap:14px;">
      <button class="btn-mustard" id="newAssignmentBtn" style="align-self:flex-start;">+ Give New Assignment</button>
      ${assignmentTiles}
    </div>
  `;

  document.getElementById('newAssignmentBtn').onclick = ()=> renderTeacherNewAssignment();

  main.querySelectorAll('[data-preview-assignment]').forEach(btn=>{
    btn.addEventListener('click', async ()=>{
      const id = btn.getAttribute('data-preview-assignment');
      const list = await loadAssignments();
      const a = list.find(x=>x.id===id);
      if(a) renderTeacherAssignmentPreview(a);
    });
  });

  main.querySelectorAll('[data-delete-assignment]').forEach(btn=>{
    btn.addEventListener('click', async ()=>{
      const id = btn.getAttribute('data-delete-assignment');
      if(!confirm('Delete this assignment? Students will no longer see it.')) return;
      const list = await loadAssignments();
      const next = list.filter(x=>x.id!==id);
      await saveAssignments(next);
      renderTeacherHome();
    });
  });
}

function renderTeacherNewAssignment(){
  const main = document.getElementById('teacherMain');
  main.innerHTML = `
    <button class="back-link" onclick="renderTeacherHome()">&larr; Back to Home</button>
    <div class="eyebrow">New Assignment</div>
    <h1 style="margin-bottom:4px;">Give an Assignment</h1>
    <p style="font-size:13px; color:#8A8F9F; margin-bottom:20px;">Give it a title and a link. It will appear immediately on every student's home page.</p>
    <div class="card" style="max-width:520px;">
      <div class="login-error" id="assignmentError">Please fill in the title and a valid link.</div>
      <div class="field">
        <label for="assignmentTitle">Assignment Title</label>
        <input id="assignmentTitle" type="text" placeholder="e.g. Weekly Grammar Exercise">
      </div>
      <div class="field">
        <label for="assignmentUrl">Assignment Link</label>
        <input id="assignmentUrl" type="url" placeholder="https://...">
      </div>
      <button class="btn-mustard" id="publishAssignmentBtn" style="width:100%; margin-top:6px;">Publish to Students</button>
    </div>
  `;

  document.getElementById('publishAssignmentBtn').onclick = async ()=>{
    const errBox = document.getElementById('assignmentError');
    errBox.style.display = 'none';
    const title = document.getElementById('assignmentTitle').value.trim();
    let url = document.getElementById('assignmentUrl').value.trim();

    if(!title || !url){
      errBox.textContent = 'Please fill in the title and a valid link.';
      errBox.style.display = 'block';
      return;
    }
    if(!/^https?:\/\//i.test(url)){
      url = 'https://' + url;
    }
    try{ new URL(url); }catch(e){
      errBox.textContent = 'That link doesn\'t look valid. Please check it and try again.';
      errBox.style.display = 'block';
      return;
    }

    const btn = document.getElementById('publishAssignmentBtn');
    btn.disabled = true;
    btn.textContent = 'Publishing...';

    const list = await loadAssignments();
    list.push({
      id: 'a' + Date.now(),
      title,
      url,
      createdAt: Date.now()
    });
    const ok = await saveAssignments(list);

    if(!ok){
      btn.disabled = false;
      btn.textContent = 'Publish to Students';
      errBox.textContent = 'Could not publish the assignment. Please try again.';
      errBox.style.display = 'block';
      return;
    }
    renderTeacherHome();
  };
}

function renderTeacherAssignmentPreview(assignment){
  const main = document.getElementById('teacherMain');
  main.innerHTML = `
    <button class="back-link" onclick="renderTeacherHome()">&larr; Back to Home</button>
    <div class="eyebrow">Assignment Preview</div>
    <h1 style="margin-bottom:4px;">${assignment.title}</h1>
    <p style="font-size:13px; color:#8A8F9F; margin-bottom:20px;">This is exactly what students see when they open this assignment.</p>
    <div class="card" style="display:flex; flex-direction:column; gap:14px; align-items:flex-start;">
      <p style="font-size:13.5px; color:var(--ink-soft); margin:0; word-break:break-all;">${assignment.url}</p>
      <a class="btn-mustard" href="${assignment.url}" target="_blank" rel="noopener noreferrer" style="text-decoration:none; display:inline-block;">Open Assignment &#8599;</a>
    </div>
  `;
}

/* ============ INIT ============ */
renderLogin();
</script>
</body>
</html>
