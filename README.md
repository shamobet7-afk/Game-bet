
<html lang="am">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Game Bet - Ultimate Gaming Experience</title>
    <style>
        /* CSS RESET & VARIABLES */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        :root {
            --bg-dark: #0f1923;
            --bg-card: #1f2937;
            --primary-yellow: #facc15;
            --accent-green: #22c55e;
            --accent-blue: #3b82f6;
            --text-light: #f3f4f6;
            --text-gray: #9ca3af;
        }

        body {
            background-color: var(--bg-dark);
            color: var(--text-light);
            display: flex;
            flex-direction: column;
            min-height: 100vh;
        }

        /* HEADER & NAVIGATION */
        header {
            background-color: #111827;
            padding: 15px 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 2px solid #1f2937;
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .logo {
            font-size: 28px;
            font-weight: 800;
            color: var(--primary-yellow);
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .logo span {
            color: var(--accent-blue);
        }

        nav ul {
            display: flex;
            list-style: none;
            gap: 20px;
        }

        nav a {
            color: var(--text-light);
            text-decoration: none;
            font-weight: 600;
            font-size: 15px;
            transition: color 0.3s;
        }

        nav a:hover, nav a.active {
            color: var(--primary-yellow);
        }

        .user-actions {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .balance-box {
            background: #1f2937;
            padding: 8px 15px;
            border-radius: 20px;
            border: 1px solid var(--primary-yellow);
            font-weight: bold;
            color: var(--primary-yellow);
        }

        .btn {
            padding: 9px 18px;
            border: none;
            border-radius: 5px;
            font-weight: bold;
            cursor: pointer;
            transition: transform 0.2s, background 0.3s;
        }

        .btn-deposit {
            background-color: var(--accent-green);
            color: #fff;
        }

        .btn-deposit:hover {
            background-color: #16a34a;
            transform: scale(1.03);
        }

        /* HERO PROMO BANNER */
        .hero {
            background: linear-gradient(rgba(15, 25, 35, 0.8), rgba(15, 25, 35, 0.8)), 
                        url('https://images.unsplash.com/photo-1511193311914-0346f16efe90?auto=format&fit=crop&w=1200&q=80');
            background-size: cover;
            background-position: center;
            padding: 60px 5%;
            text-align: center;
            border-bottom: 1px solid #1f2937;
        }

        .hero h1 {
            font-size: 42px;
            margin-bottom: 10px;
            color: var(--primary-yellow);
        }

        .hero p {
            font-size: 18px;
            color: var(--text-gray);
            margin-bottom: 20px;
        }

        /* MAIN CONTAINER & CATEGORIES */
        .container {
            padding: 30px 5%;
            flex-grow: 1;
        }

        .category-bar {
            display: flex;
            gap: 15px;
            margin-bottom: 25px;
            overflow-x: auto;
            padding-bottom: 10px;
        }

        .cat-btn {
            background: var(--bg-card);
            color: var(--text-light);
            padding: 10px 20px;
            border-radius: 8px;
            border: 1px solid #374151;
            cursor: pointer;
            white-space: nowrap;
            font-weight: 600;
        }

        .cat-btn.active, .cat-btn:hover {
            background: var(--accent-blue);
            border-color: var(--accent-blue);
        }

        /* GAME GRID */
        .games-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
            gap: 20px;
        }

        .game-card {
            background-color: var(--bg-card);
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 4px 15px rgba(0,0,0,0.3);
            transition: transform 0.3s, box-shadow 0.3s;
            position: relative;
            display: flex;
            flex-direction: column;
        }

        .game-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 25px rgba(250, 204, 21, 0.2);
        }

        .game-img {
            width: 100%;
            height: 150px;
            object-fit: cover;
        }

        .game-info {
            padding: 15px;
            text-align: center;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            flex-grow: 1;
        }

        .game-title {
            font-size: 16px;
            font-weight: bold;
            margin-bottom: 10px;
        }

        .btn-play {
            background: var(--primary-yellow);
            color: #000;
            width: 100%;
            padding: 8px 0;
            font-weight: 700;
        }

        .btn-play:hover {
            background: #eab308;
        }

        /* MODAL (GAME WINDOW) */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.85);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }

        .modal-content {
            background: var(--bg-card);
            width: 90%;
            max-width: 700px;
            border-radius: 15px;
            padding: 20px;
            text-align: center;
            position: relative;
            box-shadow: 0 0 30px rgba(0,0,0,0.8);
        }

        .close-btn {
            position: absolute;
            top: 15px;
            right: 20px;
            font-size: 24px;
            color: var(--text-gray);
            cursor: pointer;
        }

        .game-frame {
            background: #000;
            height: 300px;
            border-radius: 10px;
            margin: 20px 0;
            display: flex;
            align-items: center;
            justify-content: center;
            border: 1px solid #374151;
        }

        /* FOOTER */
        footer {
            background-color: #0b1118;
            padding: 20px 5%;
            text-align: center;
            color: var(--text-gray);
            font-size: 14px;
            border-top: 1px solid #1f2937;
        }
    </style>
</head>
<body>

    <!-- HEADER -->
    <header>
        <div class="logo">GAME<span>BET</span></div>
        <nav>
            <ul>
                <li><a href="#" class="active">Home</a></li>
                <li><a href="#">Sports</a></li>
                <li><a href="#">Live Casino</a></li>
                <li><a href="#">Slots</a></li>
                <li><a href="#">Promotions</a></li>
            </ul>
        </nav>
        <div class="user-actions">
            <div class="balance-box">ETB <span id="user-balance">1,500.00</span></div>
            <button class="btn btn-deposit">+ Deposit</button>
        </div>
    </header>

    <!-- HERO SECTION -->
    <section class="hero">
        <h1>Welcome to Game Bet!</h1>
        <p>Play the best online games, crash games, and sports betting with instant payouts.</p>
        <button class="btn btn-deposit" style="padding: 12px 25px; font-size: 16px;">Claim 100% Bonus</button>
    </section>

    <!-- MAIN GAME SECTION -->
    <main class="container">
        <!-- CATEGORIES -->
        <div class="category-bar">
            <button class="cat-btn active">All Games</button>
            <button class="cat-btn">Crash Games</button>
            <button class="cat-btn">Slots</button>
            <button class="cat-btn">Roulette</button>
            <button class="cat-btn">Card Games</button>
        </div>

        <!-- GAMES GRID -->
        <div class="games-grid">
            
            <div class="game-card">
                <img src="https://images.unsplash.com/photo-1509198397868-475647b2a1e5?auto=format&fit=crop&w=400&q=80" class="game-img" alt="Aviator">
                <div class="game-info">
                    <div class="game-title">Aviator Crash</div>
                    <button class="btn btn-play" onclick="openGame('Aviator Crash')">PLAY NOW</button>
                </div>
            </div>

            <div class="game-card">
                <img src="https://images.unsplash.com/photo-1606167668584-78701c57f13d?auto=format&fit=crop&w=400&q=80" class="game-img" alt="European Roulette">
                <div class="game-info">
                    <div class="game-title">European Roulette</div>
                    <button class="btn btn-play" onclick="openGame('European Roulette')">PLAY NOW</button>
                </div>
            </div>

            <div class="game-card">
                <img src="https://images.unsplash.com/photo-1518609878373-06d740f60d8b?auto=format&fit=crop&w=400&q=80" class="game-img" alt="Slots">
                <div class="game-info">
                    <div class="game-title">Fortune Slots 777</div>
                    <button class="btn btn-play" onclick="openGame('Fortune Slots 777')">PLAY NOW</button>
                </div>
            </div>

            <div class="game-card">
                <img src="https://images.unsplash.com/photo-1541278107931-e006523892df?auto=format&fit=crop&w=400&q=80" class="game-img" alt="Football Betting">
                <div class="game-info">
                    <div class="game-title">Live Football Bet</div>
                    <button class="btn btn-play" onclick="openGame('Live Football Bet')">PLAY NOW</button>
                </div>
            </div>

            <div class="game-card">
                <img src="https://images.unsplash.com/photo-1511193311914-0346f16efe90?auto=format&fit=crop&w=400&q=80" class="game-img" alt="Poker">
                <div class="game-info">
                    <div class="game-title">Texas Hold'em Poker</div>
                    <button class="btn btn-play" onclick="openGame('Texas Hold\'em Poker')">PLAY NOW</button>
                </div>
            </div>

        </div>
    </main>

    <!-- GAME MODAL WINDOW -->
    <div class="modal" id="gameModal">
        <div class="modal-content">
            <span class="close-btn" onclick="closeGame()">&times;</span>
            <h2 id="modal-title">Game Title</h2>
            <div class="game-frame">
                <p style="color: var(--primary-yellow); font-size: 20px;">[ Game Engine Loading / Demo Play ]</p>
            </div>
            <button class="btn btn-deposit" onclick="alert('Bet Placed Successfully!')">Place Bet / Play</button>
        </div>
    </div>

    <!-- FOOTER -->
    <footer>
        <p>&copy; 2026 Game Bet Platform. All rights reserved. 18+ Play Responsibly.</p>
    </footer>

    <!-- JAVASCRIPT -->
    <script>
        function openGame(title) {
            document.getElementById('modal-title').innerText = title;
            document.getElementById('gameModal').style.display = 'flex';
        }

        function closeGame() {
            document.getElementById('gameModal').style.display = 'none';
        }

        // Close modal when clicking outside of modal content
        window.onclick = function(event) {
            let modal = document.getElementById('gameModal');
            if (event.target == modal) {
                modal.style.display = "none";
            }
        }
    </script>
</body>
</html>
