<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Stopwatch</title>
    <style>
        *{
            margin: 0;
            padding: 0;
        }
        body{
            width: 100%;
            height: 100vh;
            background-image: url(dark-smoke-abstract-space-wallpaper-background-generative-ai-photo.jpg);
            background-position: center;
            background-size: cover;
            display: flex;
            align-items: center;
            justify-content: center;
            font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
            }
            .container{
                padding: 1rem;
                max-width: 300px;
                text-align: center;
                position: relative;
                border-radius: 10px;
               border: 2px groove white;
            }
            .timer-Display{
                padding: 1rem 0;
                font-size: 2rem;
            }
            h1,p{
                color: white;
            }
            button{
                padding: 0.4rem 1rem;
                margin: 0 0.2rem;
                border-radius: 10px;
                border: 1px solid white;
            }
            button:hover{
                background-color: black;
                color: white;
                border: 1px groove red;
            }
            #resetlap{
                margin: 8px;
            }
            .laps{
                color: white;
                text-align: center;
            }
            @media (max-width: 60px) {
  .container {
    flex-direction: column;
  }
}

    </style>
</head>
<body>
    <div class="container">
        <h1>Stopwatch</h1>
        <p class="timer-Display">
           00 : 00 : 00 : 00
        </p>
        <ul class="laps"></ul>
        <button id="start" onclick="start()">Start</button>
        <button id="stop" onclick="stop()">Stop</button>
        <button id="reset" onclick="reset()">Reset</button>
        <button id="lap" onclick="lap()">Lap</button>
        <button id="resetlap" onclick="resetlap()">Reset Lap</button>
        <button id="restart" onclick="restart()">Restart</button>
    </div>
</body>
<script>
    var ms=0, s=0, m=0, h=0
    var timer;
    var display= document.querySelector(".timer-Display")
    var laps= document.querySelector(".laps")
    function start(){
        if(!timer){
            timer= setInterval(run, 10)
        }
    }
    function run(){
        display.innerHTML= getTimer()
        ms++
        if(ms == 100){
            ms= 0
            s++
        }
        if(s == 60){
            s= 0
            m++
        }
        if(m == 60){
            m= 0
            h++
        }
        if(h == 13){
            h=1
        }
    }
    function getTimer(){
        return(h<10 ? "0" +h: h)+ ":" +(m<10 ? "0" +m: m)+ ":" +(s<10 ? "0" +s: s)+ ":" +(ms<10 ? "0" +ms: ms);
    }
    function stop(){
        stopTimer()
    }
    function stopTimer(){
        clearInterval(timer)
        timer= false
    }
    function reset(){
        stopTimer()
        ms= 0
        s= 0
        m= 0
        h= 0
        display.innerHTML= getTimer()
    }
    function restart(){
        if(timer){
            reset();
            start();
        }
    }
    function lap(){
        if(timer){
            var Li= document.createElement("li")
            Li.innerHTML= getTimer()
            laps.appendChild(Li)
        }
    }
    function resetlap(){
        laps.innerHTML= ""
    }
</script>
</html>
