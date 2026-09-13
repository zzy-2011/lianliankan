(() => {
  'use strict';
  const cv = document.getElementById('game'); const ctx = cv.getContext('2d');
  const W = cv.width, H = cv.height;
  const dpr = Math.max(1, Math.min(3, window.devicePixelRatio || 1));
  cv.width = W * dpr; cv.height = H * dpr; ctx.scale(dpr, dpr);
  const scoreEl = document.getElementById('score'), timeEl = document.getElementById('time');
  const overlay = document.getElementById('overlay'), ovTitle = document.getElementById('ov-title'), ovSub = document.getElementById('ov-sub');
  const COLS = 8, ROWS = 8, CELL = Math.floor(W / COLS);
  const ox = (W - COLS * CELL) / 2, oy = (H - ROWS * CELL) / 2;
  const COLORS = ['#ff5c7a', '#4fd1ff', '#43d97a', '#ffd23f', '#b15cff', '#ff9f43'];
  const SYM = ['🍎', '💧', '🍀', '⭐', '🔮', '🌟'];
  let board, score, timeLeft, over, sel, timer;

  const rnd = () => Math.floor(Math.random() * COLORS.length);
  function newBoard() {
    board = Array.from({ length: ROWS }, () => Array(COLS).fill(0));
    for (let r = 0; r < ROWS; r++) for (let c = 0; c < COLS; c++) {
      let v;
      do { v = rnd(); } while ((c >= 2 && board[r][c - 1] === v && board[r][c - 2] === v) || (r >= 2 && board[r - 1][c] === v && board[r - 2][c] === v));
      board[r][c] = v;
    }
  }
  function findMatches() {
    const m = new Set();
    for (let r = 0; r < ROWS; r++) { let run = 1; for (let c = 1; c < COLS; c++) { if (board[r][c] !== -1 && board[r][c] === board[r][c - 1]) run++; else { if (run >= 3) for (let k = c - run; k < c; k++) m.add(r + ',' + k); run = 1; } } if (run >= 3) for (let k = COLS - run; k < COLS; k++) m.add(r + ',' + k); }
    for (let c = 0; c < COLS; c++) { let run = 1; for (let r = 1; r < ROWS; r++) { if (board[r][c] !== -1 && board[r][c] === board[r - 1][c]) run++; else { if (run >= 3) for (let k = r - run; k < r; k++) m.add(k + ',' + c); run = 1; } } if (run >= 3) for (let k = ROWS - run; k < ROWS; k++) m.add(k + ',' + c); }
    return m;
  }
  function resolve() {
    while (true) {
      const m = findMatches(); if (m.size === 0) break;
      score += m.size * 10; scoreEl.textContent = score;
      m.forEach(k => { const [r, c] = k.split(',').map(Number); board[r][c] = -1; });
      for (let c = 0; c < COLS; c++) {
        const col = [];
        for (let r = ROWS - 1; r >= 0; r--) if (board[r][c] !== -1) col.push(board[r][c]);
        while (col.length < ROWS) col.push(rnd());
        for (let r = ROWS - 1, idx = 0; r >= 0; r--, idx++) board[r][c] = col[idx];
      }
    }
  }
  function trySwap(r1, c1, r2, c2) {
    const t = board[r1][c1]; board[r1][c1] = board[r2][c2]; board[r2][c2] = t;
    if (findMatches().size === 0) { const t2 = board[r1][c1]; board[r1][c1] = board[r2][c2]; board[r2][c2] = t2; return false; }
    resolve(); return true;
  }
  function draw() {
    ctx.fillStyle = '#1a1c3a'; ctx.fillRect(0, 0, W, H);
    for (let r = 0; r < ROWS; r++) for (let c = 0; c < COLS; c++) {
      const x = ox + c * CELL, y = oy + r * CELL;
      ctx.fillStyle = '#22254a'; ctx.fillRect(x + 2, y + 2, CELL - 4, CELL - 4);
      if (board[r][c] >= 0) {
        ctx.fillStyle = COLORS[board[r][c]];
        ctx.beginPath();
        const rad = 8; const w = CELL - 10;
        const bx = x + 5, by = y + 5;
        ctx.moveTo(bx + rad, by); ctx.arcTo(bx + w, by, bx + w, by + w, rad); ctx.arcTo(bx + w, by + w, bx, by + w, rad); ctx.arcTo(bx, by + w, bx, by, rad); ctx.arcTo(bx, by, bx + w, by, rad); ctx.closePath(); ctx.fill();
        ctx.font = (CELL * 0.5) + 'px serif'; ctx.textAlign = 'center'; ctx.textBaseline = 'middle'; ctx.fillText(SYM[board[r][c]], x + CELL / 2, y + CELL / 2);
      }
      if (sel && sel[0] === r && sel[1] === c) { ctx.strokeStyle = '#fff'; ctx.lineWidth = 3; ctx.strokeRect(x + 2, y + 2, CELL - 4, CELL - 4); }
    }
  }
  function cellAt(e) { const rect = cv.getBoundingClientRect(); const px = (e.clientX - rect.left) / rect.width * W, py = (e.clientY - rect.top) / rect.height * H; const c = Math.floor((px - ox) / CELL), r = Math.floor((py - oy) / CELL); if (r < 0 || r >= ROWS || c < 0 || c >= COLS) return null; return [r, c]; }
  function clickHandler(e) {
    if (over) return; const cell = cellAt(e); if (!cell) return; const [r, c] = cell;
    if (!sel) { sel = [r, c]; return; }
    if (sel[0] === r && sel[1] === c) { sel = null; return; }
    if (Math.abs(sel[0] - r) + Math.abs(sel[1] - c) === 1) { trySwap(sel[0], sel[1], r, c); sel = null; }
    else sel = [r, c];
  }
  cv.addEventListener('click', clickHandler);
  cv.addEventListener('touchend', e => { const t = e.changedTouches[0]; const rect = cv.getBoundingClientRect(); const px = (t.clientX - rect.left) / rect.width * W, py = (t.clientY - rect.top) / rect.height * H; const c = Math.floor((px - ox) / CELL), r = Math.floor((py - oy) / CELL); if (r >= 0 && r < ROWS && c >= 0 && c < COLS) clickHandler({ clientX: t.clientX, clientY: t.clientY }); }, { passive: true });
  function reset() {
    newBoard(); score = 0; timeLeft = 60; over = false; sel = null;
    scoreEl.textContent = '0'; timeEl.textContent = '60'; overlay.classList.add('hidden');
    if (timer) clearInterval(timer);
    timer = setInterval(() => { if (!over) { timeLeft--; timeEl.textContent = timeLeft; if (timeLeft <= 0) { over = true; ovTitle.textContent = '时间到'; ovSub.textContent = '得分 ' + score; overlay.classList.remove('hidden'); } } }, 1000);
  }
  document.getElementById('new').addEventListener('click', reset);
  document.getElementById('ov-btn').addEventListener('click', reset);
  function loop() { draw(); requestAnimationFrame(loop); }
  reset(); requestAnimationFrame(loop);
})();
