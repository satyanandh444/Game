(function(){
  var E={rock:"✊",paper:"✋",scissors:"✌️"};
  var beats={rock:"scissors",paper:"rock",scissors:"paper"};
  var verb={rock:"Rock smashes scissors",paper:"Paper covers rock",scissors:"Scissors cut paper"};
  var s={you:0,cpu:0,draw:0,streak:0},busy=false;
  var $=function(id){return document.getElementById(id)};
  var btns=document.querySelectorAll(".picks button");
  var START="<strong>Your move</strong><span>Tap a hand, or press R, P or S.</span>";

  function render(){
    $("sYou").textContent=s.you;$("sCpu").textContent=s.cpu;$("sDraw").textContent=s.draw;
    $("streak").textContent="Streak "+s.streak;
  }
  function discs(y,c){$("youDisc").className="disc "+y;$("cpuDisc").className="disc "+c}
  function setBusy(b){busy=b;btns.forEach(function(x){x.disabled=b})}

  function play(pick){
    if(busy)return;
    setBusy(true);
    var keys=Object.keys(E),cpu=keys[Math.floor(Math.random()*3)],res=$("result");
    res.className="result";
    res.innerHTML="<strong>Rock, paper, scissors…</strong><span>&nbsp;</span>";
    discs("","");
    $("youHand").textContent="✊";$("cpuHand").textContent="✊";
    var reduce=window.matchMedia("(prefers-reduced-motion: reduce)").matches;
    $("arena").classList.add("shake");
    setTimeout(function(){
      $("arena").classList.remove("shake");
      $("youHand").textContent=E[pick];$("cpuHand").textContent=E[cpu];
      var cls,title,line;
      if(pick===cpu){s.draw++;s.streak=0;cls="draw";title="It's a draw";line="You both picked "+pick+".";discs("draw","draw");}
      else if(beats[pick]===cpu){s.you++;s.streak++;cls="win";title="You win";line=verb[pick]+".";discs("won","lost");}
      else{s.cpu++;s.streak=0;cls="lose";title="Computer wins";line=verb[cpu]+".";discs("lost","won");}
      res.className="result "+cls;
      res.innerHTML="<strong>"+title+"</strong><span>"+line+"</span>";
      render();setBusy(false);
    },reduce?100:1000);
  }

  btns.forEach(function(b){b.addEventListener("click",function(){play(b.dataset.c)})});
  document.addEventListener("keydown",function(e){
    if(e.ctrlKey||e.metaKey||e.altKey)return;
    var k={r:"rock",p:"paper",s:"scissors"}[e.key.toLowerCase()];
    if(k)play(k);
  });
  $("reset").addEventListener("click",function(){
    s={you:0,cpu:0,draw:0,streak:0};render();discs("","");
    $("youHand").textContent="❔";$("cpuHand").textContent="❔";
    $("result").className="result";$("result").innerHTML=START;
  });
})();
