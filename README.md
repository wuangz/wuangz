<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Merry Christmas</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            background: linear-gradient(to bottom, #001f3f, #0074D9);
            color: white;
            font-family: 'Arial', sans-serif;
            text-align: center;
            overflow: hidden;
        }
        h1 {
            font-size: 60px;
            margin-top: 100px;
        }
        p {
            font-size: 24px;
            margin: 20px auto;
            max-width: 600px;
        }
        .button {
            display: inline-block;
            margin-top: 20px;
            padding: 15px 30px;
            background-color: #FF4136;
            color: white;
            text-decoration: none;
            border-radius: 5px;
            font-size: 20px;
            box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.2);
        }
        .button:hover {
            background-color: #85144b;
        }
        canvas {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
        }
    </style>
</head>
<body>
    <h1>Merry Christmas 2024!</h1>
    <p>Chúc bạn và gia đình một mùa Giáng Sinh an lành, ấm áp và tràn đầy yêu thương!</p>
    <a href="https://www.youtube.com/watch?v=E8gmARGvPlI" class="button" target="_blank">Nghe nhạc Giáng Sinh</a>
    
    <!-- Canvas for Snow Effect -->
    <canvas id="snow"></canvas>

    <script>
        const canvas = document.getElementById('snow');
        const ctx = canvas.getContext('2d');

        // Resize canvas
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        const snowflakes = [];

        function createSnowflakes() {
            for (let i = 0; i < 200; i++) {
                snowflakes.push({
                    x: Math.random() * canvas.width,
                    y: Math.random() * canvas.height,
                    radius: Math.random() * 4 + 1,
                    speed: Math.random() * 3 + 1
                });
            }
        }

        function drawSnowflakes() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            ctx.fillStyle = "white";

            snowflakes.forEach(flake => {
                ctx.beginPath();
                ctx.arc(flake.x, flake.y, flake.radius, 0, Math.PI * 2);
                ctx.fill();
            });
        }

        function updateSnowflakes() {
            snowflakes.forEach(flake => {
                flake.y += flake.speed;
                if (flake.y > canvas.height) {
                    flake.y = 0;
                    flake.x = Math.random() * canvas.width;
                }
            });
        }

        function animate() {
            drawSnowflakes();
            updateSnowflakes();
            requestAnimationFrame(animate);
        }

        createSnowflakes();
        animate();

        window.addEventListener('resize', () => {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
            snowflakes.length = 0;
            createSnowflakes();
        });
    </script>
</body>
</html>
