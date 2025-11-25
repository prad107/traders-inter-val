[readme (5).md](https://github.com/user-attachments/files/23737220/readme.5.md)
# interval traders learning app

A Pen created on CodePen.

Original URL: [https://codepen.io/Shabirah-Newton/pen/KwzyGVr](https://codepen.io/Shabirah-Newton/pen/KwzyGVr).
[license (3).txt](https://github.com/user-attachments/files/23737223/license.3.txt)The MIT License (MIT)

Copyright (c) 2025 Prada   (https://codepen.io/Shabirah-Newton/pen/KwzyGVr)
Fork of an original work interval traders learning app (https://codepen.io/Shabirah-Newton/pen/JoXraKq)

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER[index (2).html](https://github.com/user-attachments/files/23737224/index.2.html)
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Interval Traders — Learn Trading</title>
  <meta name="description" content="Interval Traders — interactive, beginner-friendly trading lessons and simulator." />
  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;800&display=swap" rel="stylesheet">
  <!-- Chart.js (for simple price charts) -->
  <script src="https://cdn.jsdelivr.net/npm/chart.js@4.3.0/dist/chart.umd.min.js"></script>
  <style>
    :root{
      --bg:#0b0f12;
      --card:#0f1720;
      --muted:#9aa4b2;
      --accent:#d4af37; /* gold */
      --glass: rgba(255,255,255,0.03);
      font-family: 'Inter', system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial;
    }
    *{box-sizing:border-box}
    body{margin:0;background:linear-gradient(180deg,#050607 0%, #0b0f12 100%);color:#e6eef6;min-height:100vh}
    header{display:flex;align-items:center;justify-content:space-between;padding:18px 28px;border-bottom:1px solid rgba(255,255,255,0.03);backdrop-filter:blur(6px)}
    .brand{display:flex;gap:12px;align-items:center}
    .logo{width:44px;height:44px;border-radius:8px;background:linear-gradient(135deg,var(--accent),#f7d78a);display:flex;align-items:center;justify-content:center;font-weight:800;color:#081018}
    h1{margin:0;font-size:16px}
    .sub{color:var(--muted);font-size:12px}
    .container{padding:28px;max-width:1100px;margin:20px auto;display:grid;grid-template-columns:360px 1fr;gap:20px}
    /* Sidebar */
    .sidebar{background:var(--card);padding:18px;border-radius:12px;box-shadow:0 6px 24px rgba(2,6,23,0.6)}
    .profile{display:flex;gap:12px;align-items:center}
    .avatar{width:56px;height:56px;border-radius:10px;background:linear-gradient(180deg,#11151a,#0b1015);display:flex;align-items:center;justify-content:center;font-weight:700;color:var(--accent)}
    .stat{margin-top:14px;display:flex;gap:8px;flex-wrap:wrap}
    .stat button{background:var(--glass);border:1px solid rgba(255,255,255,0.03);padding:8px 10px;border-radius:8px;color:var(--muted);font-size:13px}
    nav.lesson-list{margin-top:18px}
    nav.lesson-list button{display:block;width:100%;text-align:left;padding:10px;border-radius:8px;border:0;background:transparent;color:#e6eef6;margin-bottom:8px}
    nav.lesson-list button.active{background:linear-gradient(90deg,rgba(212,175,55,0.12),rgba(212,175,55,0.06));border:1px solid rgba(212,175,55,0.12)}
    /* Main */
    .main{display:flex;flex-direction:column;gap:18px}
    .card{background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));padding:18px;border-radius:12px}
    .chart-wrap{height:320px}
    .controls{display:flex;gap:8px;align-items:center}
    .btn{background:transparent;border:1px solid rgba(255,255,255,0.06);padding:8px 12px;border-radius:10px;color:var(--accent);cursor:pointer}
    .btn.primary{background:linear-gradient(90deg,var(--accent),#f3d87a);color:#081018;border:0}
    .sim-actions{display:flex;gap:10px;align-items:center}
    .lesson{line-height:1.5;color:var(--muted)}
    /* Quiz */
    .quiz{display:grid;gap:10px}
    .option{padding:10px;border-radius:8px;border:1px solid rgba(255,255,255,0.03);cursor:pointer}
    .option.correct{border-color:rgba(56,181,74,0.6);background:rgba(56,181,74,0.06)}
    .option.wrong{border-color:rgba(220,80,80,0.6);background:rgba(220,80,80,0.06)}
    footer{padding:18px;text-align:center;color:var(--muted);font-size:13px}
    /* Responsive */
    @media (max-width:900px){.container{grid-template-columns:1fr;padding:12px}.sidebar{order:2}.main{order:1}}
  </style>
</head>
<body>
  <header>
    <div class="brand">
      <div class="logo">IT</div>
      <div>
        <h1>Interval Traders</h1>
        <div class="sub">Learn trading with hands-on intervals & simulator</div>
      </div>
    </div>
    <div style="display:flex;gap:12px;align-items:center">
      <div class="sub">Balance: <strong id="balance">$10,000</strong></div>
      <button class="btn" id="resetBtn" title="Reset simulator">Reset</button>
    </div>
  </header>

  <main class="container">
    <aside class="sidebar card">
      <div class="profile">
        <div class="avatar">IT</div>
        <div>
          <div style="font-weight:700">Welcome, trainee</div>
          <div class="sub">Beginner • 0 XP</div>
        </div>
      </div>

      <div class="stat">
        <button id="newTradeBtn">New Trade</button>
        <button id="viewLessonsBtn">Lessons</button>
        <button id="openQuizBtn">Quick Quiz</button>
      </div>

      <nav class="lesson-list" aria-label="Lessons">
        <button class="active" data-lesson="0">1. Intro to Intervals</button>
        <button data-lesson="1">2. Reading Price Action</button>
        <button data-lesson="2">3. Risk & Position Sizing</button>
        <button data-lesson="3">4. Trading Plan</button>
        <button data-lesson="4">5. Simulator Practice</button>
      </nav>

      <div style="margin-top:14px;color:var(--muted);font-size:13px">Tip: Use the simulator to test strategies without risk.</div>
    </aside>

    <section class="main">
      <div class="card">
        <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:10px">
          <div>
            <div style="font-weight:700">Live Demo Chart</div>
            <div class="sub">Simulated price feed — practice with intervals</div>
          </div>
          <div class="controls">
            <select id="intervalSelect" class="btn" style="padding:8px;border-radius:8px">
              <option value="1">1s</option>
              <option value="5" selected>5s</option>
              <option value="10">10s</option>
              <option value="30">30s</option>
            </select>
            <button class="btn" id="pauseBtn">Pause</button>
            <button class="btn primary" id="buyBtn">Buy</button>
            <button class="btn" id="sellBtn">Sell</button>
          </div>
        </div>
        <div class="chart-wrap">
          <canvas id="priceChart" aria-label="Simulated price chart"></canvas>
        </div>
      </div>

      <div class="card" id="lessonCard">
        <div style="display:flex;justify-content:space-between;align-items:flex-start">
          <div>
            <div style="font-weight:700" id="lessonTitle">1. Intro to Intervals</div>
            <div class="sub" id="lessonSub">Understand interval-based decision making.</div>
          </div>
          <div style="text-align:right">
            <div class="sub">Progress</div>
            <div style="font-weight:700" id="progress">0 / 5</div>
          </div>
        </div>
        <hr style="border:none;border-top:1px solid rgba(255,255,255,0.03);margin:12px 0">
        <div class="lesson" id="lessonBody">
          <p><strong>What is an interval?</strong> An interval is a fixed timeframe (like 1s, 5s, 1m) you use to observe price changes. Short intervals show noise; longer intervals show trends.</p>
          <p>Practice: Use the simulator below. Hit <strong>Buy</strong> or <strong>Sell</strong> and watch how price moves. Use small position sizes first.</p>
        </div>
      </div>

      <div class="card" id="quizCard" style="display:none">
        <div style="font-weight:700;margin-bottom:8px">Quick Quiz</div>
        <div class="quiz" id="quizArea">
          <!-- dynamic -->
        </div>
        <div style="margin-top:10px;display:flex;gap:8px;justify-content:flex-end">
          <button class="btn" id="nextQuizBtn">Next</button>
        </div>
      </div>

      <div class="card" id="tradeLogCard">
        <div style="display:flex;justify-content:space-between;align-items:center">
          <div style="font-weight:700">Trade Log</div>
          <div class="sub">Recent simulated trades</div>
        </div>
        <div id="tradeLog" style="margin-top:12px;color:var(--muted);font-size:14px">No trades yet.</div>
      </div>

    </section>
  </main>

  <footer>
    Built for beginners • Interval Traders — practice, learn, repeat.
  </footer>

  <script>
    // Simple single-file learning app logic
    // Data + state
    const ctx = document.getElementById('priceChart').getContext('2d');
    let balance = 10000;
    let positions = [];
    let tradeLog = [];
    let paused = false;
    let price = 100; // starting price
    let priceHistory = Array.from({length:40}, (_,i)=>price + Math.sin(i/4)*2 + (Math.random()-0.5));

    // Chart setup
    const chart = new Chart(ctx, {
      type:'line',
      data:{labels: priceHistory.map((_,i)=>i), datasets:[{label:'Price',data:priceHistory,pointRadius:0,tension:0.2}]},
      options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{display:false}} ,scales:{x:{display:false},y:{beginAtZero:false,ticks:{callback: v => '$' + v.toFixed(2)}}}}
    });

    // UI refs
    const balanceEl = document.getElementById('balance');
    const buyBtn = document.getElementById('buyBtn');
    const sellBtn = document.getElementById('sellBtn');
    const pauseBtn = document.getElementById('pauseBtn');
    const resetBtn = document.getElementById('resetBtn');
    const tradeLogEl = document.getElementById('tradeLog');
    const progressEl = document.getElementById('progress');

    function updateUI(){
      balanceEl.textContent = '$' + balance.toFixed(2);
      if(tradeLog.length===0) tradeLogEl.textContent = 'No trades yet.';
      else tradeLogEl.innerHTML = tradeLog.slice().reverse().map(t=>`<div style="padding:8px;border-bottom:1px dashed rgba(255,255,255,0.02)"><strong>${t.type}</strong> @ $${t.price.toFixed(2)} — P&L: <strong>$${t.pnl.toFixed(2)}</strong></div>`).join('');
      progressEl.textContent = Math.min(5, tradeLog.length) + ' / 5';
    }

    // Simulated price tick
    function tick(){
      if(paused) return;
      // simple random walk with momentum
      const drift = (Math.random()-0.48) * 0.6;
      const momentum = (price - priceHistory[priceHistory.length-2] || 0) * 0.15;
      price += drift + momentum + (Math.random()-0.5)*0.8;
      price = Math.max(0.1, price);
      priceHistory.push(price);
      if(priceHistory.length>200) priceHistory.shift();
      chart.data.labels = priceHistory.map((_,i)=>i);
      chart.data.datasets[0].data = priceHistory;
      chart.update('none');
      // update open positions unrealized P&L
      positions.forEach(p=>{ p.unrealized = (price - p.entry) * (p.type==='Buy'?1:-1) * p.size; });
      // small auto-close: positions older than 30 ticks close
      const now = Date.now();
      const autoClose = [];
      positions.forEach(p=>{ if(now - p.time > 30000) autoClose.push(p); });
      autoClose.forEach(p=>closePosition(p));
    }

    // Position functions
    function openPosition(type, size=1){
      const exposure = size * price;
      if(exposure > balance * 0.5){ alert('Position too large for demo — reduce size.'); return; }
      const pos = {type,entry:price,size,unrealized:0,time:Date.now()};
      positions.push(pos);
      tradeLog.push({type,price, size, pnl:0});
      updateUI();
    }
    function closePosition(p){
      const idx = positions.indexOf(p);
      if(idx===-1) return;
      const pnl = (price - p.entry) * (p.type==='Buy'?1:-1) * p.size;
      balance += pnl;
      tradeLog.push({type: p.type==='Buy'?'Sell (closed long)':'Buy (closed short)', price, pnl, size:p.size});
      positions.splice(idx,1);
      updateUI();
    }

    buyBtn.addEventListener('click', ()=>{
      openPosition('Buy', 1);
    });
    sellBtn.addEventListener('click', ()=>{
      openPosition('Sell', 1);
    });
    pauseBtn.addEventListener('click', ()=>{
      paused = !paused; pauseBtn.textContent = paused? 'Resume' : 'Pause';
    });
    resetBtn.addEventListener('click', ()=>{
      if(!confirm('Reset simulator?')) return;
      balance = 10000; positions=[]; tradeLog=[]; price = 100; priceHistory = Array.from({length:40}, (_,i)=>price + Math.sin(i/4)*2 + (Math.random()-0.5)); chart.data.datasets[0].data = priceHistory; chart.update(); updateUI();
    });

    // Auto-tick interval controlled by select
    const intervalSelect = document.getElementById('intervalSelect');
    let tickInterval = 5000; // ms
    function setTickInterval(){
      const s = Number(intervalSelect.value);
      tickInterval = Math.max(200, s*1000);
      if(window._tickTimer) clearInterval(window._tickTimer);
      window._tickTimer = setInterval(tick, tickInterval);
    }
    intervalSelect.addEventListener('change', setTickInterval);

    // Lessons & quiz (simple static)
    const lessons = [
      {title:'Intro to Intervals', body:`Intervals are timeframes you observe to make decisions. Short intervals show noise, long intervals show trends. Try switching intervals to see the difference.`},
      {title:'Reading Price Action', body:`Look for higher highs and higher lows for uptrends. Candles and wicks show where price rejected levels.`},
      {title:'Risk & Position Sizing', body:`Only risk a small % of your balance on any trade. Use stop-losses and calculate position size.`},
      {title:'Trading Plan', body:`Decide entry, stop, and target before you trade. Discipline > prediction.`},
      {title:'Simulator Practice', body:`Use the simulator. Keep a log. Learn from losing trades.`}
    ];
    document.querySelectorAll('.lesson-list button').forEach(btn=>btn.addEventListener('click', e=>{
      document.querySelectorAll('.lesson-list button').forEach(b=>b.classList.remove('active'));
      e.currentTarget.classList.add('active');
      const i = Number(e.currentTarget.dataset.lesson);
      document.getElementById('lessonTitle').textContent = (i+1)+'. '+lessons[i].title;
      document.getElementById('lessonBody').textContent = lessons[i].body;
      document.getElementById('lessonSub').textContent = lessons[i].title;
    }));

    // Quick quiz
    const quizData = [
      {q:'Which interval shows more noise?', a:['1s','1h','1d','1w'], correct:0},
      {q:'What should you set before entering a trade?', a:['Stop loss','Random guess','Only target','Nothing'], correct:0},
      {q:'A risk management rule is to:', a:['Risk everything','Risk a small %','Never use stop loss','Double down always'], correct:1}
    ];
    let quizIndex = 0;
    const quizArea = document.getElementById('quizArea');
    function renderQuiz(){
      const q = quizData[quizIndex];
      quizArea.innerHTML = `<div style="font-weight:700">${q.q}</div>` + q.a.map((opt,ix)=>`<div class="option" data-ix="${ix}">${opt}</div>`).join('');
      quizArea.querySelectorAll('.option').forEach(o=>o.addEventListener('click', (ev)=>{
        const chosen = Number(ev.currentTarget.dataset.ix);
        if(chosen === q.correct){ ev.currentTarget.classList.add('correct'); }
        else{ ev.currentTarget.classList.add('wrong'); quizArea.querySelector(`[data-ix="${q.correct}"]`)?.classList.add('correct'); }
      }));
    }
    document.getElementById('openQuizBtn').addEventListener('click', ()=>{
      document.getElementById('quizCard').style.display='block';
      renderQuiz();
    });
    document.getElementById('nextQuizBtn').addEventListener('click', ()=>{
      quizIndex = (quizIndex+1) % quizData.length; renderQuiz();
    });

    // New trade quick open
    document.getElementById('newTradeBtn').addEventListener('click', ()=>{
      // quick demo: open a Buy and auto close after 8 seconds
      openPosition('Buy', 1);
      setTimeout(()=>{ if(positions.length) closePosition(positions[0]); }, 8000);
    });

    // Start
    setTickInterval(); updateUI();

    // small accessibility: keyboard shortcuts
    window.addEventListener('keydown', (e)=>{
      if(e.key==='b') openPosition('Buy',1);
      if(e.key==='s') openPosition('Sell',1);
      if(e.key===' ') { paused = !paused; pauseBtn.textContent = paused? 'Resume':'Pause'; }
    });

    // Helpful message for beginners
    console.log('Interval Traders demo loaded — press B to buy, S to sell, space to pause.');
  </script>
</body>
</html>
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.


learn how to trade in minutes 
