# Love-Message-
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>A Special Message For You</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background: linear-gradient(135deg, #ffe6e6, #ffb3b3);
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            overflow: hidden;
        }
        .card {
            background: rgba(255, 255, 255, 0.9);
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            text-align: center;
            max-width: 450px;
            width: 90%;
            z-index: 10;
            transition: transform 0.5s ease;
        }
        h1 {
            color: #d63031;
            margin-bottom: 20px;
            font-size: 2rem;
        }
        p {
            color: #2d3436;
            font-size: 1.1rem;
            line-height: 1.6;
            min-height: 80px;
            margin-bottom: 25px;
        }
        .btn {
            background: #d63031;
            color: white;
            border: none;
            padding: 12px 28px;
            font-size: 1rem;
            border-radius: 25px;
            cursor: pointer;
            font-weight: bold;
            transition: background 0.3s, transform 0.2s;
            outline: none;
        }
        .btn:hover {
            background: #e17055;
            transform: scale(1.05);
        }
        .heart {
            position: absolute;
            color: #d63031;
            font-size: 20px;
            pointer-events: none;
            animation: float 4s linear infinite;
            opacity: 0;
        }
        @keyframes float {
            0% {
                transform: translateY(100vh) scale(0);
                opacity: 0;
            }
            10% {
                opacity: 0.8;
            }
            90% {
                opacity: 0.8;
            }
            100% {
                transform: translateY(-10vh) scale(1.5);
                opacity: 0;
            }
        }
    </style>
</head>
<body>

    <div class="card">
        <h1 id="title">Hello Beautiful! ❤️</h1>
        <p id="text">I have a secret confession to make... Click the button below to read it.</p>
        <button class="btn" id="actionBtn" onclick="revealMessage()">Reveal Secret</button>
    </div>

    <script>
        const message = "You make my world brighter every single day. Thank you for being you, for your beautiful smile, and for filling my life with so much love. I love you more than words can describe! Forever and always. ✨";
        let index = 0;
        let isTyping = false;

        function revealMessage() {
            if (isTyping) return;
            isTyping = true;
            
            document.getElementById("title").innerText = "My Confession 💖";
            const textElement = document.getElementById("text");
            textElement.innerText = "";
            
            const btn = document.getElementById("actionBtn");
            btn.style.display = "none";

            typeWriter(textElement);
            setInterval(createHeart, 300);
        }

        function typeWriter(element) {
            if (index < message.length) {
                element.innerHTML += message.charAt(index);
                index++;
                setTimeout(() => typeWriter(element), 50);
            }
        }

        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.innerHTML = '❤️';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = (Math.random() * 2 + 3) + 's';
            heart.style.fontSize = (Math.random() * 15 + 15) + 'px';
            document.body.appendChild(heart);

            setTimeout(() => {
                heart.remove();
            }, 5000);
        }
    </script>
</body>
</html>
