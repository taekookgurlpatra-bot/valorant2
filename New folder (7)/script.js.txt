let pages=document.querySelectorAll(".page")
let progress=document.getElementById("progress")
let visited=new Set()

function go(id){
pages.forEach(p=>p.classList.remove("active"))
document.getElementById(id).classList.add("active")

visited.add(id)
progress.style.width=(visited.size/8*100)+"%"
}

function back(){go("menu")}

/* hearts rain */
function rain(){
let h=document.createElement("span")
h.innerHTML="💗"
h.style.left=Math.random()*100+"vw"
h.style.fontSize=Math.random()*20+15+"px"
document.body.appendChild(h)
setTimeout(()=>h.remove(),6000)
}
setInterval(rain,400)

/* music */
function play(i){
document.querySelectorAll("audio").forEach(a=>a.pause())
document.querySelectorAll("audio")[i].play()
}

/* tap heart game */
function heartGame(){
let area=document.getElementById("gameArea")
area.innerHTML=""
for(let i=0;i<6;i++){
let h=document.createElement("span")
h.innerHTML="💗"
h.style.fontSize="40px"
h.style.margin="10px"
h.onclick=()=>{
h.remove()
alert("Love grows in tiny moments 💗")
}
area.appendChild(h)
}
}

/* puzzle game */
function startPuzzle(){
let area=document.getElementById("gameArea")
area.innerHTML=`<img src="assets/puzzle-image.jpg" width="200">`
alert("Complete the puzzle mentally 😌💗")
}

/* QUIZ */
let q=[
["When did we first talk?","A","B","C","D","A"],
["Who confessed first?","A","B","C","D","A"],
["Fav thing about us?","A","B","C","D","D"],
["Our vibe?","A","B","C","D","D"],
["Future dream?","A","B","C","D","D"],
["What connects us?","Both","Only you","Only me","None","Both"],
["Fav memory?","A","B","C","D","D"],
["Fav habit?","A","B","C","D","D"],
["What defines us?","A","B","C","D","D"],
["Love level?","A","B","C","D","D"]
]

let qi=0,score=0
function loadQ(){
if(qi>=q.length){
document.getElementById("quizBox").innerHTML=
`Score ${score}/10 💗 <br><button onclick="go('letter1')">Continue</button>`
return
}
let d=q[qi]
document.getElementById("quizBox").innerHTML=
`<p>${d[0]}</p>
<button onclick="ans('${d[1]}')">${d[1]}</button>
<button onclick="ans('${d[2]}')">${d[2]}</button>
<button onclick="ans('${d[3]}')">${d[3]}</button>
<button onclick="ans('${d[4]}')">${d[4]}</button>`
}
function ans(a){
if(a==q[qi][5]) score++
qi++
loadQ()
}
loadQ()

/* LETTER 1 */
function showLetter1(){
let text=`Hii Ashraf 💗
Happy Valentine’s Day…
Door rehna mushkil hota hai but tum meri comfort ho…`
type(text,"l1")
}

/* LETTER 2 */
function showLetter2(){
let text=`Ashraf 💗
Thank you mujhe choose karne ke liye…
Main hamesha tumhare saath rahungi 🫂`
type(text,"l2")
}

/* typing */
function type(t,id){
let i=0
let el=document.getElementById(id)
el.innerHTML=""
let int=setInterval(()=>{
el.innerHTML+=t[i]
i++
if(i>=t.length) clearInterval(int)
},40)
}
