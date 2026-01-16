<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ANGRY PLANNER v7</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Courier+Prime:wght@400;700&display=swap');
        body { font-family: 'Courier Prime', monospace; background-color: #000; color: #fff; transition: background-color 0.3s; }
        .rage-active { background-color: #440000 !important; animation: pulse 1.5s infinite; }
        @keyframes pulse { 0% { opacity: 1; } 50% { opacity: 0.8; } 100% { opacity: 1; } }
        .shame-row { border-left: 4px solid #ff0000; background: #111; margin-bottom: 4px; padding: 4px 8px; font-size: 0.7rem; }
        .angry-table { border-collapse: collapse; width: 100%; font-size: 0.75rem; }
        .angry-table th, .angry-table td { border: 1px solid #333; padding: 8px; text-align: left; }
        .angry-table th { background: #222; color: #ff0000; text-transform: uppercase; }
        input[type="text"] { background: transparent; border: none; color: white; width: 100%; outline: none; }
        input[type="checkbox"] { cursor: pointer; accent-color: #ff0000; width: 22px; height: 22px; }
        .bonus-flash { color: #00ff00; font-weight: bold; animation: fadeOut 2s forwards; }
        @keyframes fadeOut { from { opacity: 1; } to { opacity: 0; } }
    </style>
</head>
<body class="p-4 flex flex-col min-h-screen" onclick="initAudio()">

    <header class="mb-4 border-b-4 border-white pb-2">
        <h1 class="text-4xl font-black italic uppercase tracking-tighter">Angry Planner</h1>
        <p id="insult-box" class="text-[10px] text-red-600 font-bold uppercase mt-1 italic">The Machine doesn't care about your feelings.</p>
    </header>

    <section class="border-2 border-gray-800 p-3 mb-6 bg-black relative">
        <div class="flex justify-between items-center mb-2">
            <span class="text-xs font-bold">👤 YOU vs 🤖 MACHINE</span>
            <div class="flex gap-2 items-center">
                <div id="bonus-notif" class="text-[10px]"></div>
                <span id="user-score" class="text-xs text-green-500 font-bold">0.0h</span>
            </div>
        </div>
        <div class="w-full bg-gray-900 h-1"><div id="user-bar" class="bg-green-500 h-1" style="width: 0%"></div></div>
    </section>

    <section class="mb-6">
        <h2 class="text-xs font-bold mb-2 uppercase text-gray-500">Task Logistics (+15m Bonus per Tick)</h2>
        <table class="angry-table">
            <thead>
                <tr>
                    <th style="width: 15%;">Done</th>
                    <th>Mission/Task</th>
                </tr>
            </thead>
            <tbody>
                <tr><td><input type="checkbox" onchange="claimBonus(this)"></td><td><input type="text" placeholder="CRITICAL TASK 1"></td></tr>
                <tr><td><input type="checkbox" onchange="claimBonus(this)"></td><td><input type="text" placeholder="CRITICAL TASK 2"></td></tr>
                <tr><td><input type="checkbox" onchange="claimBonus(this)"></td><td><input type="text" placeholder="CRITICAL TASK 3"></td></tr>
                <tr><td><input type="checkbox" onchange="claimBonus(this)"></td><td><input type="text" placeholder="DAILY GRIND"></td></tr>
            </tbody>
        </table>
    </section>

    <section class="mb-6 p-4 border-4 border-red-600 bg-black text-center">
        <div id="timer" class="text-5xl font-black mb-4">25:00</div>
        <div class="flex gap-2">
            <button onclick="startRage(1500)" class="flex-1 bg-red-600 text-white font-bold py-3 uppercase active:scale-95 shadow-[4px_4px_0px_white]">Engage Rage</button>
            <button onclick="resetRage()" class="px-4 border border-gray-600 uppercase text-[10px]">Mute</button>
        </div>
    </section>

    <div class="mt-auto">
        <button onclick="addFailure()" class="w-full bg-white text-black font-black py-2 uppercase text-xs mb-4">I Wasted Time (-0.5h Penalty)</button>
        <div id="shame-log" class="max-h-20 overflow-y-auto border-t border-gray-800 pt-2"></div>
    </section>

    <script>
        let countdown, audioCtx, activeSiren;
        let userSeconds = parseFloat(localStorage.getItem('userSeconds')) || 0;
        let history = JSON.parse(localStorage.getItem('angryHistory')) || [];

        function initAudio() { if (!audioCtx) audioCtx = new (window.AudioContext || window.webkitAudioContext)(); }

        function claimBonus(el) {
            if (el.checked) {
                userSeconds += 900; // 15 minutes in seconds
                localStorage.setItem('userSeconds', userSeconds);
                updateLeaderboard();
                playSuccess();
                showBonusMsg("+15M BONUS");
            }
        }

        function showBonusMsg(msg) {
            const div = document.getElementById('bonus-notif');
            div.innerHTML = `<span class="bonus-flash">${msg}</span>`;
            setTimeout(() => div.innerHTML = "", 2000);
        }

        function updateLeaderboard() {
            const userHrs = (userSeconds / 3600).toFixed(1);
            document.getElementById('user-score').innerText = userHrs + " hrs";
            document.getElementById('user-bar').style.width = Math.min((userHrs / 10) * 100, 100) + "%";
            
            const aiHrs = (6.0 + (new Date().getHours() * 0.2)).toFixed(1);
            if (parseFloat(userHrs) >= parseFloat(aiHrs)) {
                document.getElementById('insult-box').innerText = "YOU'RE BEATING THE MACHINE. FOR NOW.";
                document.getElementById('insult-box').style.color = "#00ff00";
            } else {
                document.getElementById('insult-box').innerText = "THE MACHINE IS WINNING. PATHETIC.";
                document.getElementById('insult-box').style.color = "#ff0000";
            }
        }

        function startRage(seconds) {
            resetRage();
            document.body.classList.add('rage-active');
            let timeLeft = seconds;
            countdown = setInterval(() => {
                userSeconds++;
                localStorage.setItem('userSeconds', userSeconds);
                updateLeaderboard();
                const mins = Math.floor(timeLeft / 60);
                const secs = timeLeft % 60;
                document.getElementById('timer').innerText = `${mins}:${secs < 10 ? '0' : ''}${secs}`;
                if (timeLeft-- <= 0) { clearInterval(countdown); activeSiren = playSiren(); }
            }, 1000);
        }

        function resetRage() {
            clearInterval(countdown);
            if (activeSiren) activeSiren.stop();
            document.body.classList.remove('rage-active');
            document.getElementById('timer').innerText = "25:00";
        }

        function playSuccess() {
            if(!audioCtx) return;
            const osc = audioCtx.createOscillator();
            const gain = audioCtx.createGain();
            osc.frequency.setValueAtTime(880, audioCtx.currentTime); 
            gain.gain.exponentialRampToValueAtTime(0.01, audioCtx.currentTime + 0.2);
            osc.connect(gain); gain.connect(audioCtx.destination);
            osc.start(); osc.stop(audioCtx.currentTime + 0.2);
        }

        function playSiren() {
            const osc = audioCtx.createOscillator();
            const gain = audioCtx.createGain();
            osc.type = 'sawtooth';
            osc.frequency.setValueAtTime(100, audioCtx.currentTime);
            osc.frequency.linearRampToValueAtTime(800, audioCtx.currentTime + 0.5);
            osc.frequency.linearRampToValueAtTime(100, audioCtx.currentTime + 1.0);
            osc.loop = true;
            gain.gain.setValueAtTime(0.1, audioCtx.currentTime);
            osc.connect(gain); gain.connect(audioCtx.destination);
            osc.start(); return osc;
        }

        function addFailure() {
            userSeconds = Math.max(0, userSeconds - 1800); // 30 min penalty
            localStorage.setItem('userSeconds', userSeconds);
            const now = new Date();
            history.push({ date: now.toLocaleTimeString([], {hour:'2-digit', minute:'2-digit'}), msg: "Wasted time (-30m penalty)" });
            localStorage.setItem('angryHistory', JSON.stringify(history));
            updateLeaderboard();
            renderHistory();
        }

        function renderHistory() {
            document.getElementById('shame-log').innerHTML = history.slice().reverse().map(e => `<div class="shame-row">${e.date}: ${e.msg}</div>`).join('');
        }

        updateLeaderboard();
        renderHistory();
    </script>
</body>
</html>
