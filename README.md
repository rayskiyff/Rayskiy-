<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Rayskiy: Последний остров</title>
  <style>
    body {
      margin: 0;
      background: #001f3f;
      color: white;
      font-family: sans-serif;
      text-align: center;
    }

    h1 {
      margin-top: 20px;
    }

    canvas {
      border: 3px solid white;
      margin-top: 20px;
      background-color: #003366;
    }

    .controls {
      margin-top: 20px;
    }

    .btn {
      background: white;
      color: #001f3f;
      border: none;
      padding: 10px 20px;
      margin: 5px;
      border-radius: 10px;
      font-weight: bold;
      font-size: 16px;
    }

    .arrow-grid {
      display: grid;
      grid-template-columns: 60px 60px 60px;
      grid-template-rows: 60px 60px;
      justify-content: center;
      margin-top: 10px;
      gap: 5px;
    }

    .arrow-grid button {
      width: 60px;
      height: 60px;
    }

    .invisible {
      visibility: hidden;
    }
  </style>
</head>
<body>
  <h1>Rayskiy: Последний остров</h1>
  <canvas id="game" width="300" height="300"></canvas>
  <p>Используй стрелки или кнопки ниже для движения</p>

  <div class="controls">
    <div class="arrow-grid">
      <div></div>
      <button class="btn" onclick="move('up')">⬆</button>
      <div></div>
      <button class="btn" onclick="move('left')">⬅</button>
      <button class="btn" onclick="move('down')">⬇</button>
      <button class="btn" onclick="move('right')">➡</button>
    </div>
  </div>

  <script>
    const canvas = document.getElementById("game");
    const ctx = canvas.getContext("2d");

    const player = {
      x: 140,
      y: 140,
      size: 20,
      color: "#00ffcc"
    };

    function drawPlayer() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      ctx.fillStyle = player.color;
      ctx.beginPath();
      ctx.arc(player.x, player.y, player.size, 0, Math.PI * 2);
      ctx.fill();
    }

    function movePlayer(dx, dy) {
      player.x += dx;
      player.y += dy;
      drawPlayer();
    }

    function move(direction) {
      const step = 10;
      if (direction === "up") movePlayer(0, -step);
      else if (direction === "down") movePlayer(0, step);
      else if (direction === "left") movePlayer(-step, 0);
      else if (direction === "right") movePlayer(step, 0);
    }

    document.addEventListener("keydown", (e) => {
      if (e.key === "ArrowUp") move("up");
      if (e.key === "ArrowDown") move("down");
      if (e.key === "ArrowLeft") move("left");
      if (e.key === "ArrowRight") move("right");
    });

    drawPlayer();
  </script>
</body>
</html>
