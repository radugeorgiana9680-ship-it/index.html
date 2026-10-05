<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no,viewport-fit=cover">
<meta name="theme-color" content="#f7c8d8">
<title>Pure Shine Cleaning Manager</title>

<style>
:root{
--pink:#f4c8d8;
--pink2:#e9a5be;
--pale:#fff4f8;
--gold:#d1a34c;
--text:#111;
--muted:#6f6268;
--card:#fff;
--shadow:0 8px 24px rgba(80,35,55,.10);
--scale:1
}

*{
box-sizing:border-box;
-webkit-tap-highlight-color:transparent
}

html,body{
margin:0;
min-height:100%;
font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",sans-serif;
color:var(--text);
background:#faf3f6
}

button,input,select,textarea{
font:inherit
}

button{
cursor:pointer
}

body{
overflow-x:hidden
}

#app{
display:none;
min-height:100vh;
padding-bottom:92px
}

.top{
position:sticky;
top:0;
z-index:30;
background:rgba(255,250,252,.95);
backdrop-filter:blur(16px);
padding:12px 16px;
border-bottom:1px solid #ead4dc
}

.toprow{
display:flex;
justify-content:space-between;
align-items:center
}

.brand{
display:flex;
align-items:center;
gap:10px
}

.brand img{
width:54px;
height:54px;
border-radius:15px;
object-fit:cover;
border:2px solid var(--gold);
background:#f4dbe5
}

.brand h1{
font:700 22px Georgia,serif;
margin:0
}

.brand p{
font-size:12px;
color:var(--muted);
margin:3px 0 0
}

.topbuttons{
display:flex;
gap:7px
}

.icon{
width:44px;
height:44px;
border-radius:14px;
border:1px solid var(--gold);
background:#fff;
color:#8d3157;
font-size:22px
}

.icon.add{
background:var(--pink2);
color:#111
}

main{
width:min(100%,760px);
margin:auto;
padding:14px
}

.page{
display:none
}

.page.active{
display:block
}

.head{
display:flex;
justify-content:space-between;
align-items:center;
margin:4px 0 14px
}

.head h2{
font:700 27px Georgia,serif;
margin:0
}

.primary,.save{
border:1px solid var(--gold);
background:linear-gradient(#ef9db8,#db6a8d);
color:#111;
border-radius:14px;
padding:11px 15px;
font-weight:800
}

.card{
background:#fff;
border:1px solid #e1c7cf;
border-radius:20px;
padding:15px;
margin-bottom:11px;
box-shadow:var(--shadow)
}

.row{
display:flex;
justify-content:space-between;
gap:10px;
align-items:center
}

.small{
font-size:13px;
color:var(--muted);
line-height:1.4
}

.money{
font-weight:900
}

.datecard{
display:flex;
gap:12px;
align-items:center;
background:#fff0f5;
border:1px solid var(--gold);
border-radius:18px;
padding:14px;
margin-bottom:12px
}

.dateicon{
font-size:27px
}

.stats{
display:grid;
grid-template-columns:1fr 1fr;
gap:10px
}

.stat{
padding:16px;
border-radius:19px;
border:1px solid #d9b56d;
min-height:105px
}

.stat:nth-child(1){
background:#f6d1df
}

.stat:nth-child(2){
background:#efe0f7
}

.stat:nth-child(3){
background:#e1f0e7
}

.stat:nth-child(4){
background:#fff0c8
}

.stat strong{
display:block;
font-size:25px
}

.stat span{
font-size:13px;
color:var(--muted)
}

.hero{
min-height:190px;
border:1px solid var(--gold);
border-radius:22px;
margin:13px 0;
background:
linear-gradient(100deg,rgba(255,255,255,.94),rgba(255,224,237,.76)),
url("assets/home-banner.jpg") center/cover;
display:flex;
align-items:center;
padding:24px
}

.hero h3{
font:700 42px/0.95 "Brush Script MT","Segoe Script",cursive;
color:#a92f5e;
margin:0
}

.hero p{
max-width:270px
}

.quick{
display:grid;
grid-template-columns:1fr 1fr;
gap:10px
}

.quick button{
min-height:62px;
border-radius:17px;
border:1px solid var(--gold);
background:#fff0f5;
font-weight:800
}

.bottom{
position:fixed;
left:0;
right:0;
bottom:0;
z-index:40;
display:grid;
grid-template-columns:repeat(5,1fr);
padding:8px 7px calc(8px + env(safe-area-inset-bottom));
background:rgba(255,250,252,.97);
border-top:1px solid #dfc2ca;
backdrop-filter:blur(16px)
}

.nav{
border:0;
background:transparent;
color:#75636b;
font-size:11px;
display:flex;
flex-direction:column;
align-items:center;
gap:3px
}

.nav b{
font-size:22px
}

.nav.active{
color:#a42f5d;
font-weight:900
}

.calendar{
display:grid;
grid-template-columns:repeat(7,minmax(0,1fr));
gap:5px
}

.cal{
background:#fff;
border:1px solid #dfc37f;
border-radius:10px;
min-height:85px;
padding:5px
}

.cal small{
color:#876d78
}

.jobpill{
width:100%;
font-size:10px;
font-weight:800;
background:#f7d5e2;
border:0;
border-radius:7px;
padding:4px;
text-align:left;
margin-top:4px
}

.timer{
position:fixed;
left:12px;
right:12px;
bottom:82px;
z-index:50;
background:#4c2337;
color:#fff;
border:2px solid var(--gold);
border-radius:18px;
padding:12px;
display:none;
justify-content:space-between;
align-items:center
}

.timer.show{
display:flex
}

.timer button{
background:#f29bb7;
border:0;
border-radius:10px;
padding:9px 12px
}

.sheetbg{
position:fixed;
inset:0;
z-index:100;
background:rgba(50,20,35,.42);
display:none;
align-items:flex-end
}

.sheetbg.show{
display:flex
}

.sheet{
width:100%;
max-height:91vh;
overflow:auto;
background:#fff8fb;
border-radius:25px 25px 0 0;
padding:18px 16px calc(25px + env(safe-area-inset-bottom));
border-top:3px solid var(--gold)
}

.sheethead{
display:flex;
justify-content:space-between;
align-items:center
}

.sheet h3{
font:700 22px Georgia,serif
}

.close{
width:40px;
height:40px;
border-radius:50%;
background:#f4dce5;
border:0
}

.sheet label{
display:block;
font-size:13px;
font-weight:800;
margin:11px 0 5px
}

.sheet input,
.sheet select,
.sheet textarea{
width:100%;
padding:11px;
border:1px solid #d8bec7;
border-radius:12px;
background:#fff
}

.grid2{
display:grid;
grid-template-columns:1fr 1fr;
gap:9px
}

.actions{
display:flex;
justify-content:flex-end;
gap:8px;
margin-top:15px
}

.secondary{
background:#fff;
border:1px solid #d8bec7;
border-radius:11px;
padding:10px 13px
}

.danger{
background:#fff0f3;
color:#a6264e;
border:1px solid #e3a7b8;
border-radius:11px;
padding:9px 12px
}

/* SETTINGS */

.settings-card{
background:#fff;
border:1px solid #eadde2;
border-radius:23px;
padding:20px;
margin-bottom:14px;
box-shadow:var(--shadow)
}

.settings-card h3{
font:700 24px Georgia,serif;
margin:0 0 8px
}

.settings-card p{
margin:0 0 14px
}

.zoomline{
display:flex;
align-items:center;
justify-content:space-between;
gap:12px
}

.zoombtn{
width:58px;
height:58px;
border-radius:17px;
background:#f2d1df;
border:0;
font-size:26px;
font-weight:900
}

.zoomvalue{
font:700 23px Georgia,serif
}

.range{
width:100%;
accent-color:#d06a8e
}

.settingselect{
width:100%;
padding:12px;
border:1px solid #eadce1;
border-radius:15px;
background:#fff
}

.filebox{
width:100%
}

.soundgrid{
display:grid;
grid-template-columns:1fr 1fr;
gap:9px
}

.soundgrid button,
.widebtn{
min-height:50px;
border:0;
border-radius:16px;
background:#f3d3df;
font-weight:800
}

.widebtn{
width:100%;
margin-top:9px
}

.savefinal{
display:block;
width:100%;
min-height:58px;
margin:16px 0 5px;
border:1px solid var(--gold);
border-radius:18px;
background:linear-gradient(#ef9db8,#db6a8d);
font-weight:900;
font-size:18px
}

.status{
text-align:center;
min-height:23px;
color:#9b3158;
font-weight:800
}

.monthnav{
display:grid;
grid-template-columns:44px 1fr 44px;
gap:8px;
align-items:center;
text-align:center;
margin-bottom:10px
}

.monthtotals{
display:grid;
grid-template-columns:1fr 1fr;
gap:10px
}

.monthtotals div{
background:#fff;
border:1px solid var(--gold);
border-radius:17px;
padding:14px
}

.monthtotals span{
font-size:12px
}

.monthtotals strong{
display:block;
font-size:22px;
margin-top:4px
}

@media(max-width:390px){
.hero h3{
font-size:37px
}

.brand h1{
font-size:19px
}
}
</style>
</head>

<body>

<div id="app">

<header class="top">
<div class="toprow">

<div class="brand">
<img id="logo" src="assets/logo.jpg">
<div>
<h1>Cleaning Manager</h1>
<p>Pure Shine Cleaning ✨</p>
</div>
</div>

<div class="topbuttons">
<button class="icon add" onclick="openJob()">＋</button>
<button class="icon" onclick="showPage('settings')">⚙️</button>
</div>

</div>
</header>

<main>

<section id="home" class="page active">

<div class="datecard">
<div class="dateicon">📅</div>
<div>
<b id="today"></b>
<div class="small">Let's make today productive 🌸</div>
</div>
</div>

<div class="stats">

<div class="stat">
<strong id="statJobs">0</strong>
<span>Jobs</span>
</div>

<div class="stat">
<strong id="statHours">0h 0m</strong>
<span>Hours</span>
</div>

<div class="stat">
<strong id="statEarn">£0.00</strong>
<span>Earned</span>
</div>

<div class="stat">
<strong id="statFree">0h 0m</strong>
<span>Available</span>
</div>

</div>

<div class="hero">
<div>
<h3>A clean space<br>is a happy place ♡</h3>
<p>Everything for your cleaning business — organised, simple and beautiful.</p>
</div>
</div>

<div class="quick">
<button onclick="startNextTimer()">⏱ Start Timer</button>
<button onclick="openJob()">✨ Add Job</button>
</div>

</section>


<section id="schedule" class="page">

<div class="head">
<h2>Schedule</h2>
<button class="primary" onclick="openJob()">＋ Add</button>
</div>

<div class="card">

<div class="monthnav">
<button class="secondary" onclick="changeWeek(-7)">‹</button>
<b id="weekLabel"></b>
<button class="secondary" onclick="changeWeek(7)">›</button>
</div>

<div id="calendar" class="calendar"></div>

</div>

</section>


<section id="clients" class="page">

<div class="head">
<h2>Clients</h2>
<button class="primary" onclick="openClient()">＋ Add</button>
</div>

<div id="clientsList"></div>

</section>


<section id="jobs" class="page">

<div class="head">
<h2>Jobs</h2>
<button class="primary" onclick="openJob()">＋ Add</button>
</div>

<div id="jobsList"></div>

</section>


<section id="earnings" class="page">

<div class="head">
<h2>Monthly earnings</h2>
</div>

<div id="earnings"></div>

</section>


<section id="settings" class="page">

<div class="head">
<h2>Settings</h2>
</div>


<div class="settings-card">

<h3>Interface size</h3>

<p>
Change the size of the entire application.
</p>

<div class="zoomline">

<button class="zoombtn" onclick="adjustZoom(-5)">
−
</button>

<div id="zoomValue" class="zoomvalue">
100%
</div>

<button class="zoombtn" onclick="adjustZoom(5)">
+
</button>

</div>

<input
id="zoomRange"
class="range"
type="range"
min="80"
max="200"
step="5"
value="100"
>

</div>


<div class="settings-card">

<h3>Schedule appearance</h3>

<select id="scheduleAppearance" class="settingselect">

<option value="calendar">
Calendar
</option>

<option value="list">
List
</option>

</select>

</div>


<div class="settings-card">

<h3>App icon</h3>

<p>
Change the picture used for the app.
</p>

<input
id="iconFile"
class="filebox"
type="file"
accept="image/*"
>

</div>


<div class="settings-card">

<h3>Profile / logo picture</h3>

<input
id="profileFile"
class="filebox"
type="file"
accept="image/*"
>

</div>


<div class="settings-card">

<h3>Home banner</h3>

<p>
Change the image behind “A clean space is a happy place”.
</p>

<input
id="bannerFile"
class="filebox"
type="file"
accept="image/*"
>

</div>


<div class="settings-card">

<h3>Background</h3>

<input
id="backgroundFile"
class="filebox"
type="file"
accept="image/*"
>

<label>
Transparency
</label>

<input
id="opacity"
class="range"
type="range"
min="0"
max="100"
value="20"
>

</div>


<div class="settings-card">

<h3>Writing style</h3>

<select id="font" class="settingselect">

<option value="modern">
Modern
</option>

<option value="serif">
Elegant Serif
</option>

<option value="script">
Soft Script
</option>

<option value="rounded">
Rounded
</option>

</select>

</div>


<div class="settings-card">

<h3>Reminder sounds</h3>

<div class="soundgrid">

<button onclick="chooseSound('bell')">
🔔 Bell
</button>

<button onclick="chooseSound('soft')">
✨ Soft
</button>

<button onclick="chooseSound('chime')">
🎵 Chime
</button>

<button onclick="chooseSound('double')">
💗 Double
</button>

</div>

<button class="widebtn" onclick="testSound()">
📢 Test sound
</button>

<button class="widebtn" onclick="enableReminders()">
🔔 Enable reminders
</button>

</div>


<!-- BACKUP -->

<div class="settings-card">

<h3>Backup</h3>

<p>
Export your clients, schedule, completed jobs and earnings so your history can be restored.
</p>

<button
class="widebtn"
onclick="exportBackup()"
>
⬇️ Export backup
</button>

<button
class="widebtn"
onclick="document.getElementById('importFile').click()"
>
⬆️ Import backup
</button>

<input
id="importFile"
type="file"
accept="application/json,.json"
hidden
>

</div>


<!-- THIS IS THE FINAL BUTTON -->

<button
id="saveSettings"
class="savefinal"
>
💾 Save changes
</button>

<div
id="saveStatus"
class="status"
>
</div>

</section>

</main>


<div id="timer" class="timer">

<div>

<div
class="small"
style="color:#f3cbd8"
>
CURRENT TIMER
</div>

<b id="timerName"></b>

<div id="timerValue">
00:00:00
</div>

</div>

<button onclick="stopTimer()">
Stop
</button>

</div>


<nav class="bottom">

<button
class="nav active"
data-p="home"
onclick="showPage('home',this)"
>
<b>⌂</b>
Home
</button>

<button
class="nav"
data-p="schedule"
onclick="showPage('schedule',this)"
>
<b>🗓</b>
Schedule
</button>

<button
class="nav"
data-p="clients"
onclick="showPage('clients',this)"
>
<b>👥</b>
Clients
</button>

<button
class="nav"
data-p="jobs"
onclick="showPage('jobs',this)"
>
<b>🧹</b>
Jobs
</button>

<button
class="nav"
data-p="earnings"
onclick="showPage('earnings',this)"
>
<b>£</b>
Earnings
</button>

</nav>

</div>


<!-- CLIENT -->

<div id="clientSheet" class="sheetbg">

<div class="sheet">

<div class="sheethead">

<h3>Client</h3>

<button
class="close"
onclick="closeSheet('clientSheet')"
>
✕
</button>

</div>

<input
id="clientId"
type="hidden"
>

<label>Name</label>
<input id="clientName">

<label>Type</label>

<select id="clientType">

<option>Private</option>
<option>Agency</option>
<option>Occasional</option>
<option>Every 2 weeks</option>
<option>Every 3 weeks</option>
<option>Monthly</option>

</select>

<label>Rate (£/hour)</label>
<input
id="clientRate"
type="number"
step="0.01"
>

<label>Standard hours</label>

<input
id="clientHours"
type="number"
step="0.25"
>

<label>Phone</label>

<input
id="clientPhone"
type="tel"
>

<div class="actions">

<button
class="secondary"
onclick="closeSheet('clientSheet')"
>
Cancel
</button>

<button
class="save"
onclick="saveClient()"
>
Save
</button>

</div>

</div>

</div>


<!-- JOB -->

<div id="jobSheet" class="sheetbg">

<div class="sheet">

<div class="sheethead">

<h3 id="jobTitle">
Cleaning Job
</h3>

<button
class="close"
onclick="closeSheet('jobSheet')"
>
✕
</button>

</div>

<input
id="jobId"
type="hidden"
>

<label>Client</label>

<select id="jobClient"></select>


<div class="grid2">

<div>

<label>Date</label>

<input
id="jobDate"
type="date"
>

</div>

<div>

<label>Day</label>

<select id="jobDay">

<option>Monday</option>
<option>Tuesday</option>
<option>Wednesday</option>
<option>Thursday</option>
<option>Friday</option>
<option>Saturday</option>
<option>Sunday</option>

</select>

</div>

</div>


<div class="grid2">

<div>

<label>Start</label>

<input
id="jobStart"
type="time"
>

</div>

<div>

<label>End</label>

<input
id="jobEnd"
type="time"
>

</div>

</div>


<div class="grid2">

<div>

<label>Hours</label>

<input
id="jobHours"
type="number"
step="0.0166667"
>

</div>

<div>

<label>Rate (£/hour)</label>

<input
id="jobRate"
type="number"
step="0.01"
>

</div>

</div>


<label>Notes</label>

<textarea
id="jobNotes"
rows="3"
></textarea>


<div class="actions">

<button
id="deleteJob"
class="danger"
onclick="deleteCurrentJob()"
>
Delete
</button>

<button
class="secondary"
onclick="closeSheet('jobSheet')"
>
Cancel
</button>

<button
class="save"
onclick="saveJob()"
>
Save job
</button>

</div>

</div>

</div>


<script>

const KEY='PURE_SHINE_CLEANING_MANAGER_FINAL';

const CLIENTS=[

{
id:'lottie',
name:'Lottie',
phone:'07788 447015',
type:'Agency',
rate:16,
hours:2,
day:'Monday',
start:'09:00',
end:'11:00'
},

{
id:'victoria',
name:'Victoria',
phone:'07923 054040',
type:'Agency',
rate:16,
hours:2,
day:'Monday',
start:'13:00',
end:'15:00',
privateRate:18,
agencyRate:16
},

{
id:'matt',
name:'Matt',
phone:'07886 711055',
type:'Agency',
rate:16,
hours:4,
day:'Tuesday',
start:'09:00',
end:'13:00'
},

{
id:'christine',
name:'Christine',
phone:'',
type:'Every 2 weeks',
rate:18,
hours:3,
day:'Tuesday',
start:'09:30',
end:'12:30'
},

{
id:'sonia',
name:'Sonia',
phone:'+44 7813 677012',
type:'Agency',
rate:16,
hours:5,
day:'Wednesday',
start:'09:00',
end:'14:00'
},

{
id:'laura',
name:'Laura',
phone:'+44 7958 391731',
type:'Private',
rate:18,
hours:4,
day:'Thursday',
start:'09:00',
end:'13:00'
},

{
id:'hannah',
name:'Hannah',
phone:'07920 724916',
type:'Agency',
rate:16,
hours:3,
day:'Thursday',
start:'13:00',
end:'16:00'
},

{
id:'meghan',
name:'Meghan',
phone:'+44 7740 291352',
type:'Private',
rate:18,
hours:1,
day:'Thursday',
start:'',
end:''
},

{
id:'shindu',
name:'Shindu',
phone:'07438 168843',
type:'Every 2 weeks',
rate:16,
hours:3,
day:'Friday',
start:'',
end:''
},

{
id:'joanna',
name:'Joanna',
phone:'07872 011386',
type:'Every 2 weeks',
rate:18,
hours:3.5,
day:'Friday',
start:'',
end:''
}

];


const PAST=[

{
id:'p1',
clientId:'laura',
date:'2026-10-01',
day:'Thursday',
hours:2.85,
rate:18,
total:51.30,
done:true
},

{
id:'p2',
clientId:'hannah',
date:'2026-10-01',
day:'Thursday',
hours:3,
rate:16,
total:48,
done:true
},

{
id:'p3',
clientId:'joanna',
date:'2026-10-02',
day:'Friday',
hours:3.7,
rate:18,
total:66.60,
done:true
},

{
id:'p4',
clientId:'meghan',
date:'2026-10-04',
day:'Sunday',
hours:1.6666667,
rate:18,
total:30,
done:true
},

{
id:'p5',
clientId:'lottie',
date:'2026-10-05',
day:'Monday',
hours:2,
rate:16,
total:32,
done:true
},

{
id:'p6',
clientId:'victoria',
date:'',
day:'Monday',
hours:3,
rate:16,
total:48,
done:true
}

];


let data=
JSON.parse(localStorage.getItem(KEY)||'null')
||
{
clients:CLIENTS,
jobs:PAST,
settings:{
zoom:100,
font:'modern',
sound:'soft',
opacity:20,
schedule:'calendar',
reminders:false
}
};


let clients=data.clients||CLIENTS;

let jobs=data.jobs||PAST;

let settings={
zoom:100,
font:'modern',
sound:'soft',
opacity:20,
schedule:'calendar',
reminders:false,
...data.settings
};


let week=new Date();

let timer=null;

let timerInt=null;


const $=id=>document.getElementById(id);


const money=n=>
'£'+Number(n||0).toFixed(2);


function mins(h){

let m=Math.round(Number(h||0)*60);

return Math.floor(m/60)+'h '+(m%60)+'m';

}


function client(id){

return clients.find(c=>c.id===id);

}


function cname(id){

return client(id)?.name||'Unknown';

}


function dayName(d){

return d.toLocaleDateString(
'en-GB',
{weekday:'long'}
);

}


function keyDate(d){

return d.toISOString().slice(0,10);

}


function monday(d){

let x=new Date(d);

x.setHours(0,0,0,0);

let n=x.getDay();

x.setDate(
x.getDate()+(n===0?-6:1-n)
);

return x;

}


function weeks(a,b){

return Math.floor(
(monday(b)-monday(a))/604800000
);

}


const anchor=
new Date('2026-09-28T00:00:00');


function recurring(c,d){

if(dayName(d)!==c.day)
return false;

let t=(c.type||'').toLowerCase();

if(t.includes('2 weeks')){

let w=((weeks(anchor,d)%2)+2)%2;

if(c.id==='joanna')
return w===0;

if(c.id==='shindu')
return w===1;

return w===0;

}

if(t.includes('3 weeks')){

return ((weeks(anchor,d)%3)+3)%3===0;

}

return true;

}


function jobsOn(d){

let a=jobs.filter(
j=>j.date===keyDate(d)
);

clients.forEach(c=>{

if(recurring(c,d)){

let exists=
a.some(j=>j.clientId===c.id);

if(!exists){

a.push({

id:c.id+'_'+keyDate(d),

clientId:c.id,

date:keyDate(d),

day:c.day,

start:c.start,

end:c.end,

hours:c.hours,

rate:c.rate,

recurring:true,

done:false

});

}

}

});

return a;

}


function save(){

localStorage.setItem(
KEY,
JSON.stringify({
clients,
jobs,
settings
})
);

}


function showPage(id,btn){

document
.querySelectorAll('.page')
.forEach(x=>x.classList.remove('active'));

$(id).classList.add('active');

document
.querySelectorAll('.nav')
.forEach(x=>x.classList.remove('active'));

if(btn){

btn.classList.add('active');

}else{

document
.querySelector('.nav[data-p="'+id+'"]')
?.classList.add('active');

}

render();

}


function closeSheet(id){

$(id).classList.remove('show');

}


function render(){

$('today').textContent=
new Date().toLocaleDateString(
'en-GB',
{
weekday:'long',
day:'numeric',
month:'long'
}
);

let h=
jobs.reduce(
(a,j)=>a+Number(j.hours||0),
0
);

let e=
jobs.reduce(
(a,j)=>
a+
(
j.total!=null
?Number(j.total)
:Number(j.hours||0)*Number(j.rate||0)
),
0
);

$('statJobs').textContent=
jobs.length;

$('statHours').textContent=
mins(h);

$('statEarn').textContent=
money(e);

$('statFree').textContent=
mins(Math.max(0,40-h));

renderCalendar();

renderClients();

renderJobs();

renderEarnings();

applySettings();

}


function renderCalendar(){

let s=monday(week);

let html='';

$('weekLabel').textContent=
s.toLocaleDateString(
'en-GB',
{day:'numeric',month:'short'}
)
+
' – '+
new Date(
s.getTime()+518400000
).toLocaleDateString(
'en-GB',
{day:'numeric',month:'short'}
);


for(let i=0;i<7;i++){

let d=new Date(s);

d.setDate(s.getDate()+i);

html+=
'<div class="cal">'+
'<small>'+
dayName(d)+' '+d.getDate()+
'</small>';

jobsOn(d).forEach(j=>{

html+=
'<button class="jobpill" onclick="openJob(\''+
j.id+
'\')">'+
cname(j.clientId)+
'<br>'+
((j.start||'')+
(j.end?'–'+j.end:''))+
'</button>';

});

if(!jobsOn(d).length)
html+='<div class="small">—</div>';

html+='</div>';

}

$('calendar').innerHTML=html;

}


function changeWeek(n){

week.setDate(
week.getDate()+n
);

renderCalendar();

}


function renderClients(){

$('clientsList').innerHTML=
clients.map(c=>

'<div class="card">'+

'<div class="row">'+

'<div>'+

'<b>'+c.name+'</b>'+

'<div class="small">'+
(c.type||'')+
' · '+
money(c.rate)+
'/h · '+
mins(c.hours)+
' standard'+
'</div>'+

'<div class="small">'+
(c.day||'')+
(c.start?' · '+c.start:'')+
(c.end?'–'+c.end:'')+
(c.phone?' · '+c.phone:'')+
'</div>'+

'</div>'+

'<div>'+
'<button class="secondary" onclick="editClient(\''+
c.id+
'\')">Edit</button>'+
'</div>'+

'</div>'+

'</div>'

).join('');

}


function renderJobs(){

$('jobsList').innerHTML=

jobs
.slice()
.sort(
(a,b)=>
(b.date||'').localeCompare(a.date||'')
)
.map(j=>

'<div class="card">'+

'<div class="row">'+

'<div>'+

'<b>'+cname(j.clientId)+'</b>'+

'<div class="small">'+
(j.date||j.day)+
' · '+
(j.start||'—')+
(j.end?'–'+j.end:'')+
'</div>'+

'<div class="small">'+
'Worked: '+
mins(j.hours)+
' · '+
(j.done?'Completed':'Scheduled')+
'</div>'+

'</div>'+

'<div style="text-align:right">'+

'<b>'+
money(
j.total!=null
?j.total
:j.hours*j.rate
)+
'</b><br>'+

'<button class="secondary" onclick="startTimer(\''+
j.id+
'\')">'+
(timer?.id===j.id?'Stop':'Timer')+
'</button>'+

'<button class="secondary" onclick="openJob(\''+
j.id+
'\')">
Edit
</button>'+

'</div>'+

'</div>'+

'</div>'

).join('')
||
'<div class="card">No jobs yet.</div>';

}


let earningsMonth=new Date();

earningsMonth.setDate(1);


function renderEarnings(){

let k=
earningsMonth
.toISOString()
.slice(0,7);

let list=
jobs.filter(
j=>j.date?.slice(0,7)===k
);

let h=
list.reduce(
(a,j)=>a+Number(j.hours||0),
0
);

let e=
list.reduce(
(a,j)=>
a+
(
j.total!=null
?Number(j.total)
:j.hours*j.rate
),
0
);

$('earnings').innerHTML=

'<div class="card">'+

'<div class="monthnav">'+

'<button class="secondary" onclick="moveMonth(-1)">‹</button>'+

'<b>'+
earningsMonth.toLocaleDateString(
'en-GB',
{
month:'long',
year:'numeric'
}
)+
'</b>'+

'<button class="secondary" onclick="moveMonth(1)">›</button>'+

'</div>'+

'<div class="monthtotals">'+

'<div>'+
'<span>Total hours</span>'+
'<strong>'+mins(h)+'</strong>'+
'</div>'+

'<div>'+
'<span>Total earned</span>'+
'<strong>'+money(e)+'</strong>'+
'</div>'+

'</div>'+

'</div>'+

list.map(j=>

'<div class="card">'+

'<div class="row">'+

'<div>'+
'<b>'+cname(j.clientId)+'</b>'+
'<div class="small">'+
j.date+
' · '+
mins(j.hours)+
'</div>'+
'</div>'+

'<b>'+
money(
j.total!=null
?j.total
:j.hours*j.rate
)+
'</b>'+

'</div>'+

'</div>'

).join('');

}


function moveMonth(n){

earningsMonth.setMonth(
earningsMonth.getMonth()+n
);

renderEarnings();

}


function openClient(){

$('clientId').value='';

$('clientName').value='';

$('clientType').value='Private';

$('clientRate').value=18;

$('clientHours').value=2;

$('clientPhone').value='';

$('clientSheet').classList.add('show');

}


function editClient(id){

let c=client(id);

if(!c)return;

$('clientId').value=c.id;

$('clientName').value=c.name;

$('clientType').value=
c.type||'Private';

$('clientRate').value=
c.rate||0;

$('clientHours').value=
c.hours||0;

$('clientPhone').value=
c.phone||'';

$('clientSheet').classList.add('show');

}


function saveClient(){

let id=
$('clientId').value;

let n=
$('clientName').value.trim();

if(!n)return;

let o={

id:id||'c'+Date.now(),

name:n,

type:$('clientType').value,

rate:Number(
$('clientRate').value||0
),

hours:Number(
$('clientHours').value||0
),

phone:$('clientPhone').value.trim()

};

let i=
clients.findIndex(
c=>c.id===o.id
);

if(i<0){

clients.push(o);

}else{

clients[i]={
...clients[i],
...o
};

}

save();

closeSheet('clientSheet');

render();

}


function openJob(id){

let j=
jobs.find(x=>x.id===id);

$('jobId').value=
j?.id||'';

$('jobClient').innerHTML=
clients.map(c=>
'<option value="'+
c.id+
'">'+
c.name+
'</option>'
).join('');

if(j){

$('jobClient').value=
j.clientId;

$('jobDate').value=
j.date||'';

$('jobDay').value=
j.day||'';

$('jobStart').value=
j.start||'';

$('jobEnd').value=
j.end||'';

$('jobHours').value=
j.hours||0;

$('jobRate').value=
j.rate||0;

$('jobNotes').value=
j.notes||'';

$('deleteJob').style.display=
j.recurring?'none':'block';

}else{

let c=clients[0];

$('jobClient').value=
c?.id||'';

$('jobDate').value=
keyDate(new Date());

$('jobDay').value=
dayName(new Date());

$('jobStart').value=
c?.start||'';

$('jobEnd').value=
c?.end||'';

$('jobHours').value=
c?.hours||0;

$('jobRate').value=
c?.rate||0;

$('jobNotes').value='';

$('deleteJob').style.display='none';

}

$('jobSheet').classList.add('show');

}


function saveJob(){

let id=
$('jobId').value;

let c=
client($('jobClient').value);

if(!c)return;

let j={

id:id||'j'+Date.now(),

clientId:c.id,

date:$('jobDate').value,

day:$('jobDay').value,

start:$('jobStart').value,

end:$('jobEnd').value,

hours:Number(
$('jobHours').value||0
),

rate:Number(
$('jobRate').value||c.rate||0
),

notes:$('jobNotes').value.trim(),

done:true

};

let i=
jobs.findIndex(
x=>x.id===id
);

if(i<0){

jobs.push(j);

}else{

jobs[i]={
...jobs[i],
...j
};

}

save();

closeSheet('jobSheet');

render();

}


function deleteCurrentJob(){

let id=$('jobId').value;

if(
!id||
!confirm('Delete this job?')
)return;

jobs=
jobs.filter(
j=>j.id!==id
);

save();

closeSheet('jobSheet');

render();

}


function startTimer(id){

if(timer?.id===id){

stopTimer();

return;

}

let j=
jobs.find(x=>x.id===id)
||
jobsOn(new Date())
.find(x=>x.id===id);

if(!j)return;

timer={
id,
started:Date.now(),
base:Number(j.hours||0),
clientId:j.clientId
};

$('timerName').textContent=
cname(j.clientId);

$('timer').classList.add('show');

clearInterval(timerInt);

timerInt=
setInterval(
updateTimer,
1000
);

updateTimer();

}


function startNextTimer(){

let j=
jobsOn(new Date())[0];

if(j){

startTimer(j.id);

}else{

openJob();

}

}


function updateTimer(){

if(!timer)return;

let sec=
Math.floor(
(Date.now()-timer.started)/1000
);

$('timerValue').textContent=

String(
Math.floor(sec/3600)
).padStart(2,'0')+

':' +

String(
Math.floor(sec/60)%60
).padStart(2,'0')+

':' +

String(
sec%60
).padStart(2,'0');

}


function stopTimer(){

if(!timer)return;

let j=
jobs.find(
x=>x.id===timer.id
);

if(j){

j.hours=
Math.max(
j.hours||0,
(Date.now()-timer.started)/3600000
);

j.done=true;

save();

}

timer=null;

clearInterval(timerInt);

$('timer').classList.remove('show');

render();

}


function adjustZoom(n){

settings.zoom=
Math.max(
80,
Math.min(
200,
Number(settings.zoom||100)+n
)
);

save();

applySettings();

}


$('zoomRange').oninput=e=>{

settings.zoom=
Number(e.target.value);

save();

applySettings();

};


function applySettings(){

$('zoomRange').value=
settings.zoom;

$('zoomValue').textContent=
settings.zoom+'%';

let z=
settings.zoom/100;

document.documentElement
.style
.setProperty(
'--scale',
z
);

$('app').style.zoom=
z===1?'':z;

$('app').style.width=
z===1?'':'calc(100% / '+z+')';

$('scheduleAppearance').value=
settings.schedule||'calendar';

$('font').value=
settings.font||'modern';

$('opacity').value=
settings.opacity??20;


if(settings.font==='serif'){

document.body.style.fontFamily=
'Georgia,serif';

}else if(settings.font==='script'){

document.body.style.fontFamily=
'"Brush Script MT","Segoe Script",cursive';

}else if(settings.font==='rounded'){

document.body.style.fontFamily=
'Trebuchet MS,sans-serif';

}else{

document.body.style.fontFamily=
'-apple-system,BlinkMacSystemFont,"Segoe UI",sans-serif';

}

}


function chooseSound(x){

settings.sound=x;

save();

playSound(x);

}


function playSound(x){

try{

let C=
AudioContext||
webkitAudioContext;

let c=new C();

let ns={
bell:[880],
soft:[660],
chime:[523,659,784],
double:[660,880]
}[x]||[660];

ns.forEach(
(n,i)=>{

let o=
c.createOscillator();

let g=
c.createGain();

o.frequency.value=n;

g.gain.value=.12;

o.connect(g);

g.connect(c.destination);

o.start(
c.currentTime+i*.14
);

o.stop(
c.currentTime+i*.14+.12
);

}
);

}catch(e){}

}


function testSound(){

playSound(
settings.sound||'soft'
);

}


function enableReminders(){

settings.reminders=true;

save();

if(
'Notification' in window
){

Notification.requestPermission();

}

alert(
'Reminders are enabled.'
);

}


function readFile(file,key){

if(!file)return;

let r=
new FileReader();

r.onload=()=>{

try{

localStorage.setItem(
key,
r.result
);

applyImages();

}catch(e){

alert(
'Image too large for device storage.'
);

}

};

r.readAsDataURL(file);

}


function applyImages(){

let b=
localStorage.getItem(
'PS_BANNER'
);

if(b){

$('app')
.querySelector('.hero')
.style.backgroundImage=
'linear-gradient(100deg,rgba(255,255,255,.80),rgba(255,224,237,.62)),url("'+
b+
'")';

}


let l=
localStorage.getItem(
'PS_LOGO'
);

if(l){

$('logo').src=l;

}


let bg=
localStorage.getItem(
'PS_BACKGROUND'
);

if(bg){

document.body.style.backgroundImage=
'linear-gradient(rgba(250,243,246,'+
(Number(settings.opacity||20)/100)+
'),rgba(250,243,246,'+
(Number(settings.opacity||20)/100)+
')),url("'+
bg+
'")';

}

}


$('iconFile').onchange=e=>
readFile(
e.target.files[0],
'PS_ICON'
);


$('profileFile').onchange=e=>
readFile(
e.target.files[0],
'PS_LOGO'
);


$('bannerFile').onchange=e=>
readFile(
e.target.files[0],
'PS_BANNER'
);


$('backgroundFile').onchange=e=>
readFile(
e.target.files[0],
'PS_BACKGROUND'
);


$('opacity').oninput=e=>{

settings.opacity=
Number(e.target.value);

applyImages();

};


$('font').onchange=e=>{

settings.font=
e.target.value;

applySettings();

};


$('scheduleAppearance').onchange=e=>{

settings.schedule=
e.target.value;

save();

};


function exportBackup(){

let blob=
new Blob(
[
JSON.stringify(
{
clients,
jobs,
settings
},
null,
2
)
],
{
type:'application/json'
}
);

let u=
URL.createObjectURL(blob);

let a=
document.createElement('a');

a.href=u;

a.download=
'pure-shine-backup-'+
keyDate(new Date())+
'.json';

document.body.appendChild(a);

a.click();

a.remove();

URL.revokeObjectURL(u);

}


$('importFile').onchange=e=>{

let f=e.target.files[0];

if(!f)return;

let r=
new FileReader();

r.onload=()=>{

try{

let d=
JSON.parse(
r.result
);

if(
Array.isArray(d.clients)
){

clients=d.clients;

}

if(
Array.isArray(d.jobs)
){

jobs=d.jobs;

}

if(d.settings){

settings={
...settings,
...d.settings
};

}

save();

render();

alert(
'Backup imported successfully.'
);

}catch(x){

alert(
'Invalid backup file.'
);

}

};

r.readAsText(f);

};


/* =========================================================
   THIS BUTTON IS THE VERY LAST ITEM IN SETTINGS
   AND REALLY SAVES THE SETTINGS
   ========================================================= */

$('saveSettings').onclick=()=>{

settings.zoom=
Number(
$('zoomRange').value
);

settings.schedule=
$('scheduleAppearance').value;

settings.font=
$('font').value;

settings.opacity=
Number(
$('opacity').value
);


/* Save everything */
save();


/* Apply everything immediately */
applySettings();

applyImages();


/* Confirmation */
$('saveStatus').textContent=
'✓ Settings saved successfully';

$('saveSettings').textContent=
'✓ Settings saved';

setTimeout(()=>{

$('saveStatus').textContent='';

$('saveSettings').textContent=
'💾 Save changes';

},2200);

};


/* START */

render();

$('app').style.display='block';

applySettings();

applyImages();

</script>

</body>
</html>