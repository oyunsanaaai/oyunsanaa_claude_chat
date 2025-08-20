(()=>{

  const $ = (s,r=document)=>r.querySelector(s);
  const $$ = (s,r=document)=>r.querySelectorAll(s);

  const el = {
    open1: $('#oyOpen1'), open2: $('#oyOpen2'),
    overlay: $('#oyOverlay'), modal: $('#oyModal'),
    header: $('#oyHeader'), title: $('#chatTitle'),
    drawer: $('#oyDrawer'), menu: $('.oy-menu'),
    itemGuides: $('#itemGuides'), guidesWrap: $('#guidesWrap'),
    guideCats: $('#guideCats'), guideList: $('#guideList'),
    activeWrap: $('#activeWrap'), activeList: $('#activeList'),
    panel: $('#oyPanel'), pBack: $('#oyPanelBack'),
    pTitle: $('#oyPanelTitle'), pBody: $('#oyPanelBody'),
    chat: $('#oyChat'), stream: $('#oyStream'),
    file: $('#oyFile'), input: $('#oyInput'), send: $('#btnSend'),
    btnDrawer: $('#btnDrawer'), btnClose: $('#btnClose'),
    accName: $('#accName'), accCode: $('#accCode'),
  };

  /* ================== ӨГӨГДӨЛ ================== */
  const AGE = [
    {slug:'age-0-7',  name:'Бага балчир үе (0–7)',           color:'#E1D9C9'},
    {slug:'age-8-12', name:'Адтай бяцхан үе (8–12)',         color:'#AE9372'},
    {slug:'age-13-18',name:'Сэргэлэн өсвөр үе (13–18)',      color:'#B27D57'},
    {slug:'age-19-25',name:'Эхлэл, мөрөөдлийн үе (19–25)',  color:'#7F4B30'},
    {slug:'age-26-40',name:'Эрх чөлөөт, эрч хүчтэй үе (26–40)', color:'#A28776'},
    {slug:'age-41-55',name:'Туршлага, бүтээлийн үе (41–55)', color:'#7D8769'},
    {slug:'age-56-70',name:'Ухаан, нөлөөллийн үе (56–70)',  color:'#424C21'},
    {slug:'age-70p',  name:'Өвлөж, үлдээх үе (70+)',         color:'#173125'},
  ];
  const BUNDLES = [
    {slug:'fam',      name:'Гэр бүл',            color:'#D8A48F'},
    {slug:'career',   name:'Ажил мэргэжлийн',    color:'#957C60'},
    {slug:'class',    name:'Анги хамт олон',     color:'#EFEBCE'},
    {slug:'sport',    name:'Спорт, урлагийн',    color:'#ABAC97'},
    {slug:'org',      name:'Байгууллага',        color:'#433A29'},
  ];
  const SPECIAL = [
    {slug:'vision',   name:'Харааны бэрхшээлтэй', color:'#353326'},
    {slug:'special',  name:'Тусгай хэрэгцээт',     color:'#897E45'},
  ];
  const ALL15 = [...AGE, ...BUNDLES, ...SPECIAL];

  const CATS = [
    {key:'age',     label:'Энгийн ангилал', items:AGE},
    {key:'bundle',  label:'Багц',           items:BUNDLES},
    {key:'special', label:'Тусгай хэрэгцээт', items:SPECIAL},
  ];

  /* ================== ТӨЛӨВ ================== */
  const LSKEY = 'oy_state_v2';
  let state = {
    account:{name:'Хэрэглэгч', code:'OY-0000'},
    current:null,                     // идэвхтэй чат key
    active:{},                        // key -> {name,color,premium}
  };
  try{ const s=JSON.parse(localStorage.getItem(LSKEY)||'null'); if(s) state={...state,...s}; }catch(_){}
  function save(){ localStorage.setItem(LSKEY, JSON.stringify(state)); }

  /* ================== НЭЭХ / ХААХ ================== */
  function openModal(){ el.modal.hidden=false; el.overlay.hidden=false; bootOnce(); }
  function closeModal(){ el.modal.hidden=true; el.overlay.hidden=true; closeDrawer(); save(); }
  function toggleDrawer(){
    const open=!el.drawer.classList.contains('open');
    el.drawer.classList.toggle('open', open);
    document.body.style.overflow=open?'hidden':'';
  }
  function closeDrawer(){ el.drawer.classList.remove('open'); document.body.style.overflow=''; }

  /* ================== ТУСЛАХ ================== */
  function textColorFor(hex){
    const c=(hex||'').replace('#',''); if(c.length<6) return '#111';
    const r=parseInt(c.slice(0,2),16), g=parseInt(c.slice(2,4),16), b=parseInt(c.slice(4,6),16);
    const L=(0.299*r+0.587*g+0.114*b)/255;
    return L>0.7? '#111':'#fff';
  }
  function esc(s){ return String(s).replace(/[&<>"']/g,m=>({ '&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;' }[m])); }
  function bubble(html, who='bot'){
    const d=document.createElement('div'); d.className='oy-bubble '+(who==='user'?'oy-user':'oy-bot'); d.innerHTML=html;
    el.stream.appendChild(d); el.chat.scrollTop=el.chat.scrollHeight;
  }
  function meta(t){ const m=document.createElement('div'); m.className='oy-meta'; m.textContent=t; el.stream.appendChild(m); }

  /* ================== ХӨТӨЧ (ангилал/чат) ================== */
  function renderCats(){
    el.guideCats.innerHTML='';
    CATS.forEach(cat=>{
      const d=document.createElement('div');
      d.className='oy-pill'; d.style.setProperty('--c','#f4f4f4'); d.style.setProperty('--tc','#111');
      d.innerHTML=`<span>${cat.label}${cat.premium?' ⭐':''}</span>`;
      d.onclick=()=>renderChats(cat);
      el.guideCats.appendChild(d);
    });
  }
  function renderChats(cat){
    el.guideList.innerHTML='';
    cat.items.forEach(it=>{
      const pill=document.createElement('div');
      pill.className='oy-pill';
      pill.style.setProperty('--c', it.color);
      pill.style.setProperty('--tc', textColorFor(it.color));
      pill.innerHTML=`<span>${cat.premium?'⭐ ':''}${it.name}</span>`;
      pill.onclick=()=>selectChat(it, !!cat.premium);
      el.guideList.appendChild(pill);
    });
  }
  function selectChat(it, premium){
    const key=`${it.slug}|${premium?'p':'n'}`;
    state.current=key;
    state.active[key]={name:it.name,color:it.color,premium:!!premium};
    save(); redrawActive();
    el.title.textContent=`Оюунсанаа — ${it.name}`;
    closeDrawer();
    loadChat(key,true);
  }

  /* ================== ИДЭВХТЭЙ ЧАТУУД ================== */
  function redrawActive(){
    el.activeList.innerHTML='';
    Object.entries(state.active).forEach(([key,m])=>{
      const row=document.createElement('div'); row.className='item';
      const dot=document.createElement('span'); dot.className='dot'; dot.style.background=m.color; dot.title=m.premium?'Премиум':'Энгийн';
      const name=document.createElement('div'); name.className='name'; name.textContent=(m.premium?'⭐ ':'')+m.name;
      const x=document.createElement('button'); x.textContent='×'; x.title='Идэвхтээгээс хасах';
      name.onclick=()=>{ state.current=key; save(); el.title.textContent=`Оюунсанаа — ${m.name}`; loadChat(key,false); closeDrawer(); };
      x.onclick=(e)=>{ e.stopPropagation(); delete state.active[key]; if(state.current===key) state.current=null; save(); redrawActive(); };
      row.append(dot,name,x); el.activeList.appendChild(row);
    });
  }
  function moveActiveToBottom(open){
    if(open){ el.menu.appendChild(el.activeWrap); }
    else { el.menu.insertBefore(el.activeWrap, el.itemGuides.nextSibling); }
  }

  /* ================== ЧАТ МЕССЕЖ (localStorage) ================== */
  const msgKey = k=>`oy_msgs_${k}`;
  function loadChat(key,greet){
    el.stream.innerHTML='';
    const raw=localStorage.getItem(msgKey(key));
    if(raw){
      try{ (JSON.parse(raw)||[]).forEach(m=>bubble(m.html,m.who)); }catch(_){}
    }else if(greet){
      bubble('Сайн уу, хайрт минь. Чат эхэллээ. 🌿','bot'); meta('Эхэллээ');
    }
    setTimeout(()=>el.input.focus(),30);
  }
  function pushMsg(key, who, html){
    const k=msgKey(key); const arr=JSON.parse(localStorage.getItem(k)||'[]');
    arr.push({t:Date.now(), who, html}); localStorage.setItem(k, JSON.stringify(arr));
  }

  /* ================== ПАНЕЛ АГУУЛГА ================== */
  const PANEL = {
    account:{ title:'Миний бүртгэл', html:`
      <div class="card"><b>Суурь мэдээлэл</b><div class="muted">Нэр, Код нь сайтын бүртгэлээс автоматаар орно.</div></div>
      <div class="card">
        <label>Имэйл<br><input id="accEmail" style="width:100%;padding:8px;border:1px solid var(--line);border-radius:8px"></label><br><br>
        <label>Утас<br><input id="accPhone" style="width:100%;padding:8px;border:1px solid var(--line);border-radius:8px"></label><br><br>
        <button id="btnAccSave" class="oy-back">Хадгалах</button>
        
      </div>
    `},
    summary:{ title:'Дүгнэлт', html:`
      <div class="card"><b>Анхны зураг</b><div class="muted">Унталт, ус, алхалт, стресс (анхны 7 хоног)</div></div>
      <div class="card"><b>Явцын зураг</b><div class="muted">Сүүлийн 7/30 хоногийн индикатор</div></div>
      <div class="card"><b>Гол 3 зөвлөгөө</b><div class="muted">Дараа нь динамик болно</div></div>
    `},
    daily:{ title:'Өдөр тутмын даалгавар', html:`
      <div class="card"><b>30 өдрийн чеклист</b><div class="muted">Сэтгэл 70% · Бие 30% · Санхүү</div></div>
      <div class="card"><b>Өнөөдрийн бөглөлт</b><div class="muted">Дараа нь дэлгэрнэ</div></div>
    `},
    journal:{ title:'Өдрийн тэмдэглэл → Ном', html:`
      <div class="card"><b>Чөлөөт бичвэр</b><div class="muted">Markdown дэмждэг</div></div>
      <div class="card"><b>Чиглүүлсэн захидлууд</b><div class="muted">Талархал, уучлал, аавдаа захиа…</div></div>
      <div class="card"><b>Нууц дэвтэр (PIN)</b><div class="muted">Дараа нь идэвхжүүлнэ</div></div>
    `},
    goals:{ title:'Зорилго · Төлөвлөгөө · Хуваарь', html:`
      <div class="card"><b>Том зорилго (3 хүртэл)</b></div>
      <div class="card"><b>Жижиг алхам · Цагийн хуваарь</b></div>
      <div class="card"><b>Санхүүгийн зорилго</b></div>
    `},
    edu:{ title:'Сэтгэлийн боловсрол', html:`
      <div class="card"><b>Бяцхан хичээлүүд</b><div class="muted">Амьсгал 3×3, Талархал, Анхаарал…</div></div>
    `},
    health:{ title:'Хоол · Дасгал', html:`
      <div class="card"><b>Ус / Калори / Дасгал</b><div class="muted">Зураг илгээх боломжтой</div></div>
    `},
    reminders:{ title:'Сануулга', html:`
      <div class="card"><b>Календарь сануулгууд</b><div class="muted">Эм, уулзалт, төрсөн өдөр…</div></div>
    `},
    programs:{ title:'Нэмэлт хөтөлбөр', html:`
      <div class="card"><b>Жишээ</b><div class="muted">Анхаарал 7хон · Муу зуршил 21хон · Ус 14хон</div></div>
    `},
  };
  function showPanel(key){
    const p=PANEL[key]; if(!p) return;
    el.pTitle.textContent=p.title; el.pBody.innerHTML=p.html; el.panel.hidden=false;
    $('#oyPanelBack').onclick=()=> el.panel.hidden=true;
    const btn=$('#btnAccSave'); if(btn) btn.onclick=()=> bubble('Бүртгэлийн нэмэлт талбар хадгалагдлаа.','bot');
  }

  /* ================== BOOT / EVENTS ================== */
  function bootOnce(){
    if(el.modal.dataset.boot) return;
    el.modal.dataset.boot='1';

    // Аккаунт
    el.accName.textContent=state.account.name||'Хэрэглэгч';
    el.accCode.textContent=state.account.code||'OY-0000';

    // Ангиллууд
    renderCats(); redrawActive();

    // Өмнөх чат сэргээх
    if(state.current && state.active[state.current]){
      el.title.textContent=`Оюунсанаа — ${state.active[state.current].name}`;
      loadChat(state.current,false);
    }else{
      bubble('Сайн уу, хайрт минь. Сэтгэлийн хөтөчөөс ангиллаа сонгоод чат руу оръё. 🌸','bot'); meta('Эхэллээ');
    }
  }

  // Нээх/хаах
  el.open1.onclick=openModal; el.open2.onclick=openModal;
  el.overlay.onclick=closeModal; el.btnClose.onclick=closeModal;

  // Меню товч
  el.btnDrawer.onclick=(e)=>{ e.preventDefault(); e.stopPropagation(); toggleDrawer(); };

  // Меню item
  el.menu.addEventListener('click', (e)=>{
    const it=e.target.closest('.oy-item'); if(!it) return;
    const key=it.dataset.menu;
    if(key==='guides'){
      const open = el.guidesWrap.hidden;
      el.guidesWrap.hidden = !open;      // toggle
      moveActiveToBottom(open);          // нээгдэхэд доош шилжинэ
      return;
    }
    el.guidesWrap.hidden=true; moveActiveToBottom(false);
    showPanel(key);
  });

  // Drawer-г гадна дарвал хаах
  function globalClose(e){
    if(!el.drawer.classList.contains('open')) return;
    if(e.target.closest('#oyDrawer')) return;
    if(e.target.closest('#btnDrawer')) return;
    closeDrawer();
  }
  document.addEventListener('click', globalClose);
  document.addEventListener('touchstart', globalClose, {passive:true});

  // Чат руу бичих үед drawer хааг
  el.input.addEventListener('focus', ()=>{ if(el.drawer.classList.contains('open')) closeDrawer(); });

  // Илгээх
  function send(){
    const t=(el.input.value||'').trim(); if(!t) return;
    if(!state.current){ bubble('Эхлээд Сэтгэлийн хөтөчөөс чат сонгоорой. 🌿','bot'); el.input.value=''; return; }
    bubble(esc(t),'user'); pushMsg(state.current,'user',esc(t)); el.input.value='';
    setTimeout(()=>{ const r='Сонсож байна, амраг минь. Амьсгалаа зөөлөн аваад… ярилцъя. 💬';
      bubble(r,'bot'); pushMsg(state.current,'bot',r); save(); },150);
  }
  el.input.addEventListener('keydown', e=>{ if(e.key==='Enter' && !e.shiftKey){ e.preventDefault(); send(); }});
  el.send.onclick=send;

  // Файл хавсралт
  el.file.addEventListener('change', (e)=>{
    if(!state.current){ e.target.value=''; return; }
    const names=[...e.target.files].map(f=>f.name).slice(0,3).join(', ');
    if(names){ const h=`Хавсаргасан: <i>${esc(names)}</i>`; bubble(h,'user'); pushMsg(state.current,'user',h); save(); }
    e.target.value='';
  });

  /* ================== ГАДНААС ТОГТООХ API ================== */
  // Жишээ: window.oySetAccount({name:'Нараа', code:'OY-1234'})
  window.oySetAccount=function({name,code}={}){
    if(name) state.account.name=name;
    if(code) state.account.code=code;
    el.accName.textContent=state.account.name||'Хэрэглэгч';
    el.accCode.textContent=state.account.code||'OY-0000';
    save();
  };

})();













































