<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MindSpark - Apprends tout en t'amusant !</title>
    <link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700;800&family=Fredoka+One&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #FF6B6B;
            --secondary: #4ECDC4;
            --accent: #FFE66D;
            --purple: #9B59B6;
            --blue: #3498DB;
            --green: #2ECC71;
            --dark: #2C3E50;
            --light: #F7F9FC;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Nunito', sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            overflow-x: hidden;
            color: var(--dark);
        }

        /* Animations */
        @keyframes float {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(5deg); }
        }

        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        @keyframes slideIn {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @keyframes spin {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }

        /* Navigation */
        .navbar {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            padding: 1rem 2rem;
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            box-shadow: 0 4px 20px rgba(0,0,0,0.1);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-family: 'Fredoka One', cursive;
            font-size: 2rem;
            background: linear-gradient(45deg, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            cursor: pointer;
            transition: transform 0.3s;
        }

        .logo:hover {
            transform: scale(1.05);
        }

        .nav-links {
            display: flex;
            gap: 2rem;
            list-style: none;
        }

        .nav-links a {
            text-decoration: none;
            color: var(--dark);
            font-weight: 700;
            transition: all 0.3s;
            padding: 0.5rem 1rem;
            border-radius: 20px;
        }

        .nav-links a:hover {
            background: var(--accent);
            color: var(--dark);
            transform: translateY(-2px);
        }

        .user-profile {
            display: flex;
            align-items: center;
            gap: 1rem;
            background: var(--light);
            padding: 0.5rem 1rem;
            border-radius: 30px;
            cursor: pointer;
            transition: all 0.3s;
        }

        .user-profile:hover {
            transform: scale(1.05);
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
        }

        .avatar {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--primary), var(--purple));
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
        }

        /* Hero Section */
        .hero {
            margin-top: 80px;
            padding: 4rem 2rem;
            text-align: center;
            color: white;
            position: relative;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            width: 200%;
            height: 200%;
            background: url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='none' fill-rule='evenodd'%3E%3Cg fill='%23ffffff' fill-opacity='0.05'%3E%3Cpath d='M36 34v-4h-2v4h-4v2h4v4h2v-4h4v-2h-4zm0-30V0h-2v4h-4v2h4v4h2V6h4V4h-4zM6 34v-4H4v4H0v2h4v4h2v-4h4v-2H6zM6 4V0H4v4H0v2h4v4h2V6h4V4H6z'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E");
            animation: spin 60s linear infinite;
            opacity: 0.3;
        }

        .hero-content {
            position: relative;
            z-index: 1;
            max-width: 800px;
            margin: 0 auto;
        }

        .hero h1 {
            font-family: 'Fredoka One', cursive;
            font-size: 4rem;
            margin-bottom: 1rem;
            text-shadow: 3px 3px 0px rgba(0,0,0,0.2);
            animation: slideIn 0.8s ease-out;
        }

        .hero p {
            font-size: 1.5rem;
            margin-bottom: 2rem;
            opacity: 0.95;
            animation: slideIn 0.8s ease-out 0.2s both;
        }

        .cta-buttons {
            display: flex;
            gap: 1rem;
            justify-content: center;
            flex-wrap: wrap;
            animation: slideIn 0.8s ease-out 0.4s both;
        }

        .btn {
            padding: 1rem 2rem;
            border: none;
            border-radius: 50px;
            font-size: 1.2rem;
            font-weight: 800;
            cursor: pointer;
            transition: all 0.3s;
            text-decoration: none;
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
        }

        .btn-primary {
            background: var(--accent);
            color: var(--dark);
        }

        .btn-secondary {
            background: white;
            color: var(--purple);
        }

        .btn:hover {
            transform: translateY(-3px) scale(1.05);
            box-shadow: 0 8px 25px rgba(0,0,0,0.3);
        }

        .floating-shapes {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            pointer-events: none;
            overflow: hidden;
        }

        .shape {
            position: absolute;
            opacity: 0.2;
            animation: float 6s ease-in-out infinite;
        }

        .shape:nth-child(1) { top: 10%; left: 10%; font-size: 3rem; animation-delay: 0s; }
        .shape:nth-child(2) { top: 20%; right: 15%; font-size: 4rem; animation-delay: 1s; }
        .shape:nth-child(3) { bottom: 20%; left: 20%; font-size: 3.5rem; animation-delay: 2s; }
        .shape:nth-child(4) { bottom: 10%; right: 10%; font-size: 2.5rem; animation-delay: 3s; }

        /* Age Selector */
        .age-selector {
            background: white;
            padding: 3rem 2rem;
            margin: 2rem auto;
            max-width: 1200px;
            border-radius: 30px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.1);
            position: relative;
            overflow: hidden;
        }

        .age-selector::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(78,205,196,0.1) 0%, transparent 70%);
            animation: pulse 4s ease-in-out infinite;
        }

        .section-title {
            text-align: center;
            font-family: 'Fredoka One', cursive;
            font-size: 2.5rem;
            color: var(--dark);
            margin-bottom: 2rem;
            position: relative;
        }

        .age-cards {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            position: relative;
            z-index: 1;
        }

        .age-card {
            background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
            border-radius: 20px;
            padding: 2rem;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s;
            border: 3px solid transparent;
            position: relative;
            overflow: hidden;
        }

        .age-card::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, transparent 0%, rgba(255,255,255,0.4) 100%);
            opacity: 0;
            transition: opacity 0.3s;
        }

        .age-card:hover::after {
            opacity: 1;
        }

        .age-card:hover {
            transform: translateY(-10px) rotate(2deg);
            border-color: var(--secondary);
            box-shadow: 0 15px 40px rgba(78,205,196,0.3);
        }

        .age-card.active {
            border-color: var(--primary);
            background: linear-gradient(135deg, #ffeaa7 0%, #fab1a0 100%);
        }

        .age-icon {
            font-size: 4rem;
            margin-bottom: 1rem;
            animation: bounce 2s infinite;
        }

        .age-card h3 {
            font-size: 1.5rem;
            color: var(--dark);
            margin-bottom: 0.5rem;
        }

        .age-card p {
            color: #666;
            font-size: 0.9rem;
        }

        /* Learning Modules */
        .modules-section {
            padding: 4rem 2rem;
            max-width: 1400px;
            margin: 0 auto;
        }

        .modules-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .module-card {
            background: white;
            border-radius: 25px;
            overflow: hidden;
            box-shadow: 0 10px 40px rgba(0,0,0,0.1);
            transition: all 0.3s;
            position: relative;
            cursor: pointer;
        }

        .module-card:hover {
            transform: translateY(-10px) scale(1.02);
            box-shadow: 0 20px 60px rgba(0,0,0,0.15);
        }

        .module-header {
            height: 150px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 4rem;
            position: relative;
            overflow: hidden;
        }

        .module-card:nth-child(1) .module-header { background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 100%); }
        .module-card:nth-child(2) .module-header { background: linear-gradient(135deg, #a8edea 0%, #fed6e3 100%); }
        .module-card:nth-child(3) .module-header { background: linear-gradient(135deg, #ffecd2 0%, #fcb69f 100%); }
        .module-card:nth-child(4) .module-header { background: linear-gradient(135deg, #d299c2 0%, #fef9d7 100%); }
        .module-card:nth-child(5) .module-header { background: linear-gradient(135deg, #89f7fe 0%, #66a6ff 100%); }
        .module-card:nth-child(6) .module-header { background: linear-gradient(135deg, #fddb92 0%, #d1fdff 100%); }

        .module-content {
            padding: 1.5rem;
        }

        .module-content h3 {
            font-size: 1.5rem;
            margin-bottom: 0.5rem;
            color: var(--dark);
        }

        .module-content p {
            color: #666;
            margin-bottom: 1rem;
            line-height: 1.6;
        }

        .difficulty-tags {
            display: flex;
            gap: 0.5rem;
            flex-wrap: wrap;
        }

        .tag {
            padding: 0.3rem 0.8rem;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 700;
        }

        .tag-easy { background: #d4edda; color: #155724; }
        .tag-medium { background: #fff3cd; color: #856404; }
        .tag-hard { background: #f8d7da; color: #721c24; }

        /* Accessibility Panel */
        .accessibility-panel {
            position: fixed;
            right: 20px;
            top: 50%;
            transform: translateY(-50%);
            background: white;
            padding: 1rem;
            border-radius: 20px;
            box-shadow: 0 10px 40px rgba(0,0,0,0.2);
            z-index: 999;
            display: flex;
            flex-direction: column;
            gap: 1rem;
        }

        .access-btn {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            border: none;
            cursor: pointer;
            font-size: 1.5rem;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            justify-content: center;
            background: var(--light);
        }

        .access-btn:hover {
            transform: scale(1.1);
            background: var(--accent);
        }

        .access-btn.active {
            background: var(--secondary);
            color: white;
        }

        /* Interactive Game Area */
        .game-container {
            background: white;
            border-radius: 30px;
            padding: 3rem;
            margin: 3rem auto;
            max-width: 1000px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.1);
            display: none;
        }

        .game-container.active {
            display: block;
            animation: slideIn 0.5s ease-out;
        }

        .game-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 2rem;
            flex-wrap: wrap;
            gap: 1rem;
        }

        .score-board {
            display: flex;
            gap: 2rem;
            background: var(--light);
            padding: 1rem 2rem;
            border-radius: 20px;
        }

        .score-item {
            text-align: center;
        }

        .score-value {
            font-size: 2rem;
            font-weight: 800;
            color: var(--primary);
        }

        .score-label {
            font-size: 0.9rem;
            color: #666;
            text-transform: uppercase;
            font-weight: 700;
        }

        .quiz-area {
            background: linear-gradient(135deg, #f5f7fa 0%, #e4e8ec 100%);
            border-radius: 20px;
            padding: 3rem;
            text-align: center;
            min-height: 300px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            position: relative;
            overflow: hidden;
        }

        .question {
            font-size: 2rem;
            font-weight: 700;
            margin-bottom: 2rem;
            color: var(--dark);
            animation: slideIn 0.5s ease-out;
        }

        .answers-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 1rem;
            width: 100%;
            max-width: 600px;
        }

        .answer-btn {
            padding: 1.5rem;
            border: 3px solid transparent;
            border-radius: 15px;
            background: white;
            font-size: 1.2rem;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.3s;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
        }

        .answer-btn:hover {
            transform: translateY(-3px);
            border-color: var(--secondary);
            box-shadow: 0 8px 25px rgba(0,0,0,0.15);
        }

        .answer-btn.correct {
            background: #d4edda;
            border-color: var(--green);
            animation: pulse 0.5s;
        }

        .answer-btn.wrong {
            background: #f8d7da;
            border-color: var(--primary);
            animation: shake 0.5s;
        }

        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            25% { transform: translateX(-10px); }
            75% { transform: translateX(10px); }
        }

        /* Progress Section */
        .progress-section {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            padding: 4rem 2rem;
            margin-top: 4rem;
            color: white;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 2rem;
            max-width: 1200px;
            margin: 3rem auto 0;
        }

        .stat-card {
            background: rgba(255,255,255,0.15);
            backdrop-filter: blur(10px);
            padding: 2rem;
            border-radius: 20px;
            text-align: center;
            border: 2px solid rgba(255,255,255,0.2);
            transition: all 0.3s;
        }

        .stat-card:hover {
            transform: translateY(-5px);
            background: rgba(255,255,255,0.25);
        }

        .stat-icon {
            font-size: 3rem;
            margin-bottom: 1rem;
        }

        .stat-value {
            font-size: 2.5rem;
            font-weight: 800;
            margin-bottom: 0.5rem;
        }

        .stat-label {
            opacity: 0.9;
            font-size: 1rem;
        }

        /* Footer */
        footer {
            background: var(--dark);
            color: white;
            padding: 3rem 2rem 1rem;
            text-align: center;
        }

        .footer-content {
            max-width: 1200px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 3rem;
            margin-bottom: 2rem;
            text-align: left;
        }

        .footer-section h4 {
            font-size: 1.3rem;
            margin-bottom: 1rem;
            color: var(--accent);
        }

        .footer-section ul {
            list-style: none;
        }

        .footer-section li {
            margin-bottom: 0.5rem;
            opacity: 0.8;
            cursor: pointer;
            transition: opacity 0.3s;
        }

        .footer-section li:hover {
            opacity: 1;
            color: var(--secondary);
        }

        .footer-bottom {
            border-top: 1px solid rgba(255,255,255,0.1);
            padding-top: 2rem;
            opacity: 0.6;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .hero h1 { font-size: 2.5rem; }
            .nav-links { display: none; }
            .accessibility-panel {
                right: 10px;
                top: auto;
                bottom: 20px;
                transform: none;
                flex-direction: row;
            }
            .answers-grid { grid-template-columns: 1fr; }
        }

        /* High Contrast Mode */
        body.high-contrast {
            filter: contrast(150%);
        }

        body.high-contrast .module-card,
        body.high-contrast .age-card {
            border: 3px solid black;
        }

        /* Large Text Mode */
        body.large-text {
            font-size: 120%;
        }

        body.large-text .hero h1 {
            font-size: 5rem;
        }

        /* Celebration Animation */
        .celebration {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 9999;
            display: none;
        }

        .confetti {
            position: absolute;
            width: 10px;
            height: 10px;
            background: var(--primary);
            animation: fall linear forwards;
        }

        @keyframes fall {
            to {
                transform: translateY(100vh) rotate(720deg);
                opacity: 0;
            }
        }

        /* Loading Screen */
        .loader {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            z-index: 10000;
            transition: opacity 0.5s;
        }

        .loader.hidden {
            opacity: 0;
            pointer-events: none;
        }

        .loader-spinner {
            width: 80px;
            height: 80px;
            border: 8px solid rgba(255,255,255,0.3);
            border-top-color: white;
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }

        .loader-text {
            color: white;
            margin-top: 2rem;
            font-size: 1.5rem;
            font-weight: 700;
        }
    </style>
</head>
<body>

    <!-- Loading Screen -->
    <div class="loader" id="loader">
        <div class="loader-spinner"></div>
        <div class="loader-text">Chargement de MindSpark...</div>
    </div>

    <!-- Celebration Overlay -->
    <div class="celebration" id="celebration"></div>

    <!-- Accessibility Panel -->
    <div class="accessibility-panel">
        <button class="access-btn" onclick="toggleAudio()" title="Mode Audio" id="audioBtn">🔊</button>
        <button class="access-btn" onclick="toggleContrast()" title="Contraste Élevé" id="contrastBtn">👁️</button>
        <button class="access-btn" onclick="toggleTextSize()" title="Gros Texte" id="textBtn">Aa</button>
        <button class="access-btn" onclick="resetProgress()" title="Réinitialiser" id="resetBtn">🔄</button>
    </div>

    <!-- Navigation -->
    <nav class="navbar">
        <div class="logo" onclick="goHome()">
            <span>🧠</span>
            <span>MindSpark</span>
        </div>
        <ul class="nav-links">
            <li><a href="#accueil" onclick="goHome()">Accueil</a></li>
            <li><a href="#modules" onclick="showModules()">Modules</a></li>
            <li><a href="#progression" onclick="showProgress()">Ma Progression</a></li>
            <li><a href="#aide" onclick="showHelp()">Aide</a></li>
        </ul>
        <div class="user-profile" onclick="showProfile()">
            <div class="avatar" id="userAvatar">🦸</div>
            <span id="userName">Mon Profil</span>
        </div>
    </nav>

    <!-- Hero Section -->
    <section class="hero" id="accueil">
        <div class="floating-shapes">
            <div class="shape">📚</div>
            <div class="shape">🎨</div>
            <div class="shape">🔬</div>
            <div class="shape">🌍</div>
        </div>
        <div class="hero-content">
            <h1>Apprends tout en t'amusant !</h1>
            <p>Des milliers de jeux éducatifs adaptés à ton âge et à tes envies. Mathématiques, langues, sciences, art... tout devient un jeu d'enfant !</p>
            <div class="cta-buttons">
                <button class="btn btn-primary" onclick="startLearning()">
                    <span>🚀</span> Commencer l'aventure
                </button>
                <button class="btn btn-secondary" onclick="showDemo()">
                    <span>▶️</span> Voir la démo
                </button>
            </div>
        </div>
    </section>

    <!-- Age Selector -->
    <section class="age-selector" id="ageSelector">
        <h2 class="section-title">Choisis ton niveau 🎯</h2>
        <div class="age-cards">
            <div class="age-card" onclick="selectAge('petite', this)" data-age="3-5">
                <div class="age-icon">🧸</div>
                <h3>Petite Section</h3>
                <p>3-5 ans : Découvertes et éveil</p>
            </div>
            <div class="age-card" onclick="selectAge('moyenne', this)" data-age="6-8">
                <div class="age-icon">🎒</div>
                <h3>Moyenne Section</h3>
                <p>6-8 ans : Premiers apprentissages</p>
            </div>
            <div class="age-card" onclick="selectAge('grande', this)" data-age="9-11">
                <div class="age-icon">🚀</div>
                <h3>Grande Section</h3>
                <p>9-11 ans : Exploration approfondie</p>
            </div>
            <div class="age-card" onclick="selectAge('college', this)" data-age="12-15">
                <div class="age-icon">🎓</div>
                <h3>Collège</h3>
                <p>12-15 ans : Maîtrise et défis</p>
            </div>
        </div>
    </section>

    <!-- Learning Modules -->
    <section class="modules-section" id="modules">
        <h2 class="section-title" style="color: white;">Choisis ta mission 🎮</h2>
        <div class="modules-grid">
            <div class="module-card" onclick="startModule('maths')">
                <div class="module-header">🔢</div>
                <div class="module-content">
                    <h3>Mathématiques Magiques</h3>
                    <p>Des nombres, des formes, des calculs... deviens un magicien des maths !</p>
                    <div class="difficulty-tags">
                        <span class="tag tag-easy">Facile</span>
                        <span class="tag tag-medium">Moyen</span>
                        <span class="tag tag-hard">Difficile</span>
                    </div>
                </div>
            </div>

            <div class="module-card" onclick="startModule('langues')">
                <div class="module-header">🗣️</div>
                <div class="module-content">
                    <h3>Langues du Monde</h3>
                    <p>Français, anglais, espagnol... apprends à communiquer avec le monde entier !</p>
                    <div class="difficulty-tags">
                        <span class="tag tag-easy">Débutant</span>
                        <span class="tag tag-medium">Intermédiaire</span>
                    </div>
                </div>
            </div>

            <div class="module-card" onclick="startModule('sciences')">
                <div class="module-header">🔬</div>
                <div class="module-content">
                    <h3>Sciences Explorateur</h3>
                    <p>La nature, l'espace, les animaux... découvre les secrets de l'univers !</p>
                    <div class="difficulty-tags">
                        <span class="tag tag-easy">Découverte</span>
                        <span class="tag tag-hard">Expert</span>
                    </div>
                </div>
            </div>

            <div class="module-card" onclick="startModule('art')">
                <div class="module-header">🎨</div>
                <div class="module-content">
                    <h3>Atelier Créatif</h3>
                    <p>Dessin, musique, couleurs... libère ton imagination et crée des chefs-d'œuvre !</p>
                    <div class="difficulty-tags">
                        <span class="tag tag-easy">Libre</span>
                    </div>
                </div>
            </div>

            <div class="module-card" onclick="startModule('logique')">
                <div class="module-header">🧩</div>
                <div class="module-content">
                    <h3>Défis Logique</h3>
                    <p>Casse-têtes, mémoire, réflexion... entraîne ton cerveau avec des défis fun !</p>
                    <div class="difficulty-tags">
                        <span class="tag tag-medium">Réflexion</span>
                        <span class="tag tag-hard">Expert</span>
                    </div>
                </div>
            </div>

            <div class="module-card" onclick="startModule('histoire')">
                <div class="module-header">🏛️</div>
                <div class="module-content">
                    <h3>Voyage dans le Temps</h3>
                    <p>Préhistoire, pharaons, chevaliers... explore l'histoire comme jamais !</p>
                    <div class="difficulty-tags">
                        <span class="tag tag-easy">Histoires</span>
                        <span class="tag tag-medium">Quizz</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Interactive Game Area -->
    <section class="game-container" id="gameArea">
        <div class="game-header">
            <h2 id="gameTitle">Mathématiques Magiques</h2>
            <div class="score-board">
                <div class="score-item">
                    <div class="score-value" id="scoreValue">0</div>
                    <div class="score-label">Points</div>
                </div>
                <div class="score-item">
                    <div class="score-value" id="streakValue">0</div>
                    <div class="score-label">Série</div>
                </div>
                <div class="score-item">
                    <div class="score-value" id="levelValue">1</div>
                    <div class="score-label">Niveau</div>
                </div>
            </div>
        </div>
        
        <div class="quiz-area" id="quizArea">
            <div class="question" id="questionText">Prêt à commencer ?</div>
            <div class="answers-grid" id="answersGrid">
                <button class="answer-btn" onclick="startGame()">🚀 C'est parti !</button>
            </div>
        </div>

        <div style="text-align: center; margin-top: 2rem;">
            <button class="btn btn-secondary" onclick="closeGame()">Retour aux modules</button>
        </div>
    </section>

    <!-- Progress Section -->
    <section class="progress-section" id="progression">
        <h2 class="section-title" style="color: white;">Ta Progression 🏆</h2>
        <div class="stats-grid">
            <div class="stat-card">
                <div class="stat-icon">⭐</div>
                <div class="stat-value" id="totalStars">0</div>
                <div class="stat-label">Étoiles gagnées</div>
            </div>
            <div class="stat-card">
                <div class="stat-icon">🎯</div>
                <div class="stat-value" id="totalGames">0</div>
                <div class="stat-label">Jeux joués</div>
            </div>
            <div class="stat-card">
                <div class="stat-icon">🔥</div>
                <div class="stat-value" id="bestStreak">0</div>
                <div class="stat-label">Meilleure série</div>
            </div>
            <div class="stat-card">
                <div class="stat-icon">⏱️</div>
                <div class="stat-value" id="timeSpent">0h</div>
                <div class="stat-label">Temps d'apprentissage</div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="footer-content">
            <div class="footer-section">
                <h4>À propos</h4>
                <ul>
                    <li>Notre mission</li>
                    <li>L'équipe</li>
                    <li>Pour les parents</li>
                    <li>Pour les enseignants</li>
                </ul>
            </div>
            <div class="footer-section">
                <h4>Ressources</h4>
                <ul>
                    <li>Guide d'utilisation</li>
                    <li>Accessibilité</li>
                    <li>Centre d'aide</li>
                    <li>Blog éducatif</li>
                </ul>
            </div>
            <div class="footer-section">
                <h4>Légal</h4>
                <ul>
                    <li>Confidentialité</li>
                    <li>Conditions d'utilisation</li>
                    <li>Sécurité des enfants</li>
                    <li>Contact</li>
                </ul>
            </div>
        </div>
        <div class="footer-bottom">
            <p>© 2026 MindSpark - Fait avec ❤️ pour tous les apprentis du monde</p>
        </div>
    </footer>

    <script>
        // Game State
        let currentModule = '';
        let currentAge = '';
        let score = 0;
        let streak = 0;
        let level = 1;
        let audioEnabled = true;
        let questions = [];
        let currentQuestionIndex = 0;

        // Question Banks
        const questionBanks = {
            maths: [
                { q: "Combien font 5 + 3 ?", a: ["7", "8", "9", "6"], correct: 1 },
                { q: "Quelle est la forme avec 4 côtés égaux ?", a: ["Cercle", "Triangle", "Carré", "Rectangle"], correct: 2 },
                { q: "Si tu as 10 bonbons et tu en manges 4, il en reste ?", a: ["5", "6", "7", "8"], correct: 1 },
                { q: "Combien de côtés a un triangle ?", a: ["2", "3", "4", "5"], correct: 1 },
                { q: "Quel est le double de 6 ?", a: ["10", "11", "12", "14"], correct: 2 }
            ],
            langues: [
                { q: "Comment dit-on 'chat' en anglais ?", a: ["Dog", "Cat", "Bird", "Fish"], correct: 1 },
                { q: "Quelle est la première lettre de l'alphabet ?", a: ["A", "B", "C", "D"], correct: 0 },
                { q: "Comment dit-on 'merci' en espagnol ?", a: ["Hello", "Gracias", "Bonjour", "Hola"], correct: 1 },
                { q: "Combien de voyelles y a-t-il en français ?", a: ["4", "5", "6", "7"], correct: 2 },
                { q: "Quel mot rime avec 'soleil' ?", a: ["Réveil", "Travail", "Émail", "Tous"], correct: 3 }
            ],
            sciences: [
                { q: "Quelle planète est la plus proche du Soleil ?", a: ["Vénus", "Mars", "Mercure", "Terre"], correct: 2 },
                { q: "Les plantes ont besoin de quoi pour vivre ?", a: ["Eau et lumière", "Rien", "Seulement de l'eau", "Seulement de la terre"], correct: 0 },
                { q: "Quel animal est le plus grand ?", a: ["Éléphant", "Baleine bleue", "Girafe", "Requin"], correct: 1 },
                { q: "Combien de pattes a une araignée ?", a: ["6", "8", "10", "4"], correct: 1 },
                { q: "Quel est l'état de l'eau quand elle gèle ?", a: ["Liquide", "Gaz", "Solide", "Vapeur"], correct: 2 }
            ],
            logique: [
                { q: "Trouve l'intrus : Chien, Chat, Voiture, Lapin", a: ["Chien", "Chat", "Voiture", "Lapin"], correct: 2 },
                { q: "Complète la suite : 2, 4, 6, 8, ...", a: ["9", "10", "12", "14"], correct: 1 },
                { q: "Si A = 1, B = 2, C = 3, combien vaut ABC ?", a: ["6", "123", "3", "12"], correct: 1 },
                { q: "Quelle forme vient après : 🔴🔵🔴🔵🔴 ?", a: ["🔴", "🔵", "🟢", "🟡"], correct: 1 },
                { q: "Paul a 5 ans. Dans 3 ans, il aura ?", a: ["7 ans", "8 ans", "9 ans", "10 ans"], correct: 1 }
            ],
            histoire: [
                { q: "Qui a construit les pyramides ?", a: ["Les Romains", "Les Égyptiens", "Les Grecs", "Les Vikings"], correct: 1 },
                { q: "Quelle invention a été créée avant ?", a: ["Téléphone", "Roue", "Internet", "Avion"], correct: 1 },
                { q: "Comment s'appelaient les chevaliers du Moyen Âge ?", a: ["Samouraïs", "Cavaliers", "Romains", "Vikings"], correct: 1 },
                { q: "Où habitaient les dinosaures ?", a: ["Sur Terre", "Sur Mars", "Dans l'espace", "Sous l'eau"], correct: 0 },
                { q: "Quelle couleur était la Statue de Liberty à l'origine ?", a: ["Verte", "Bleue", "Cuivre (marron)", "Blanche"], correct: 2 }
            ],
            art: [
                { q: "Quelles sont les couleurs primaires ?", a: ["Rouge, Bleu, Jaune", "Vert, Orange, Violet", "Noir, Blanc, Gris", "Rose, Turquoise, Or"], correct: 0 },
                { q: "Quel instrument a des touches blanches et noires ?", a: ["Guitare", "Piano", "Violon", "Flûte"], correct: 1 },
                { q: "Quel artiste a coupé son oreille ?", a: ["Picasso", "Van Gogh", "Monet", "Léonard de Vinci"], correct: 1 },
                { q: "Combien de couleurs y a-t-il dans un arc-en-ciel ?", a: ["5", "6", "7", "8"], correct: 2 },
                { q: "Quelle forme est ronde comme une balle ?", a: ["Carré", "Cercle", "Triangle", "Étoile"], correct: 1 }
            ]
        };

        // Initialize
        window.onload = function() {
            setTimeout(() => {
                document.getElementById('loader').classList.add('hidden');
                speak("Bienvenue sur MindSpark ! Choisis ton âge pour commencer à apprendre en t'amusant.");
            }, 1500);
            
            loadProgress();
        };

        // Navigation Functions
        function goHome() {
            document.getElementById('gameArea').classList.remove('active');
            document.getElementById('ageSelector').scrollIntoView({ behavior: 'smooth' });
        }

        function showModules() {
            document.getElementById('modules').scrollIntoView({ behavior: 'smooth' });
        }

        function showProgress() {
            document.getElementById('progression').scrollIntoView({ behavior: 'smooth' });
        }

        function showHelp() {
            alert("Besoin d'aide ?\n\n1. Choisis ton âge\n2. Sélectionne un module\n3. Réponds aux questions\n4. Gagne des étoiles !\n\nTu peux aussi utiliser les boutons sur le côté droit pour changer les paramètres d'accessibilité.");
        }

        function showProfile() {
            const name = prompt("Comment t'appelles-tu ?") || "Super Apprenant";
            document.getElementById('userName').textContent = name;
            const avatars = ['🦸', '🦄', '🤖', '🐱', '🚀', '🌟', '🎨', '🔬'];
            const randomAvatar = avatars[Math.floor(Math.random() * avatars.length)];
            document.getElementById('userAvatar').textContent = randomAvatar;
            speak(`Bienvenue ${name} ! Prêt à apprendre ?`);
        }

        function startLearning() {
            document.getElementById('ageSelector').scrollIntoView({ behavior: 'smooth' });
            speak("Choisis d'abord ton niveau en cliquant sur une carte.");
        }

        function showDemo() {
            alert("🎬 Démo rapide :\n\n1. Choisis ton âge (3-5 ans, 6-8 ans...)\n2. Clique sur un module (Maths, Langues...)\n3. Réponds aux questions interactives\n4. Gagne des points et des étoiles !\n\nC'est parti !");
        }

        // Age Selection
        function selectAge(age, element) {
            currentAge = age;
            document.querySelectorAll('.age-card').forEach(card => card.classList.remove('active'));
            element.classList.add('active');
            
            const ageTexts = {
                'petite': 'Petite section, parfait pour commencer !',
                'moyenne': 'Moyenne section, tu progresses bien !',
                'grande': 'Grande section, tu es presque un expert !',
                'college': 'Collège, niveau expert !'
            };
            
            speak(ageTexts[age]);
            setTimeout(() => {
                document.getElementById('modules').scrollIntoView({ behavior: 'smooth' });
            }, 500);
        }

        // Module Selection
        function startModule(module) {
            if (!currentAge) {
                alert("Choisis d'abord ton niveau en haut de la page !");
                document.getElementById('ageSelector').scrollIntoView({ behavior: 'smooth' });
                return;
            }
            
            currentModule = module;
            const moduleNames = {
                'maths': 'Mathématiques Magiques',
                'langues': 'Langues du Monde',
                'sciences': 'Sciences Explorateur',
                'art': 'Atelier Créatif',
                'logique': 'Défis Logique',
                'histoire': 'Voyage dans le Temps'
            };
            
            document.getElementById('gameTitle').textContent = moduleNames[module];
            document.getElementById('gameArea').classList.add('active');
            document.getElementById('gameArea').scrollIntoView({ behavior: 'smooth' });
            
            // Reset game state
            score = 0;
            streak = 0;
            level = 1;
            updateScore();
            
            // Prepare questions
            questions = [...questionBanks[module]].sort(() => Math.random() - 0.5);
            currentQuestionIndex = 0;
            
            showQuestion();
        }

        function showQuestion() {
            if (currentQuestionIndex >= questions.length) {
                showVictory();
                return;
            }
            
            const q = questions[currentQuestionIndex];
            document.getElementById('questionText').textContent = q.q;
            
            const grid = document.getElementById('answersGrid');
            grid.innerHTML = '';
            
            q.a.forEach((answer, index) => {
                const btn = document.createElement('button');
                btn.className = 'answer-btn';
                btn.textContent = answer;
                btn.onclick = () => checkAnswer(index, q.correct, btn);
                grid.appendChild(btn);
            });
            
            speak(q.q);
        }

        function checkAnswer(selected, correct, btn) {
            const buttons = document.querySelectorAll('.answer-btn');
            buttons.forEach(b => b.disabled = true);
            
            if (selected === correct) {
                btn.classList.add('correct');
                score += 10 + (streak * 2);
                streak++;
                level = Math.floor(score / 50) + 1;
                speak("Bravo ! C'est correct !");
                createConfetti();
            } else {
                btn.classList.add('wrong');
                buttons[correct].classList.add('correct');
                streak = 0;
                speak("Oups, ce n'est pas ça. La bonne réponse était " + buttons[correct].textContent);
            }
            
            updateScore();
            updateProgress();
            
            setTimeout(() => {
                currentQuestionIndex++;
                showQuestion();
            }, 2000);
        }

        function updateScore() {
            document.getElementById('scoreValue').textContent = score;
            document.getElementById('streakValue').textContent = streak;
            document.getElementById('levelValue').textContent = level;
            
            if (streak > parseInt(localStorage.getItem('bestStreak') || 0)) {
                localStorage.setItem('bestStreak', streak);
            }
        }

        function showVictory() {
            document.getElementById('quizArea').innerHTML = `
                <div style="text-align: center; animation: slideIn 0.5s;">
                    <div style="font-size: 5rem; margin-bottom: 1rem;">🏆</div>
                    <h2 style="color: var(--primary); margin-bottom: 1rem;">Félicitations !</h2>
                    <p style="font-size: 1.3rem; margin-bottom: 2rem;">Tu as terminé le module avec ${score} points !</p>
                    <button class="btn btn-primary" onclick="closeGame()">Continuer l'aventure</button>
                </div>
            `;
            speak(`Félicitations ! Tu as gagné ${score} points !`);
            createConfetti();
            createConfetti();
        }

        function closeGame() {
            document.getElementById('gameArea').classList.remove('active');
            document.getElementById('modules').scrollIntoView({ behavior: 'smooth' });
        }

        function startGame() {
            showQuestion();
        }

        // Accessibility Functions
        function toggleAudio() {
            audioEnabled = !audioEnabled;
            document.getElementById('audioBtn').classList.toggle('active', audioEnabled);
            speak(audioEnabled ? "Audio activé" : "Audio désactivé");
        }

        function toggleContrast() {
            document.body.classList.toggle('high-contrast');
            document.getElementById('contrastBtn').classList.toggle('active');
        }

        function toggleTextSize() {
            document.body.classList.toggle('large-text');
            document.getElementById('textBtn').classList.toggle('active');
        }

        function resetProgress() {
            if (confirm("Veux-tu vraiment recommencer à zéro ?")) {
                localStorage.clear();
                score = 0;
                streak = 0;
                level = 1;
                updateScore();
                updateProgress();
                speak("Progression réinitialisée. Tu peux recommencer !");
            }
        }

        // Text to Speech
        function speak(text) {
            if (!audioEnabled || !window.speechSynthesis) return;
            
            window.speechSynthesis.cancel();
            const utterance = new SpeechSynthesisUtterance(text);
            utterance.lang = 'fr-FR';
            utterance.rate = 0.9;
            utterance.pitch = 1.1;
            window.speechSynthesis.speak(utterance);
        }

        // Confetti Effect
        function createConfetti() {
            const celebration = document.getElementById('celebration');
            celebration.style.display = 'block';
            celebration.innerHTML = '';
            
            const colors = ['#FF6B6B', '#4ECDC4', '#FFE66D', '#9B59B6', '#3498DB', '#2ECC71'];
            
            for (let i = 0; i < 50; i++) {
                const confetti = document.createElement('div');
                confetti.className = 'confetti';
                confetti.style.left = Math.random() * 100 + '%';
                confetti.style.top = -10 + 'px';
                confetti.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
                confetti.style.animationDuration = (Math.random() * 3 + 2) + 's';
                confetti.style.animationDelay = Math.random() * 2 + 's';
                celebration.appendChild(confetti);
            }
            
            setTimeout(() => {
                celebration.style.display = 'none';
            }, 5000);
        }

        // Progress Tracking
        function updateProgress() {
            let totalGames = parseInt(localStorage.getItem('totalGames') || 0);
            let totalStars = parseInt(localStorage.getItem('totalStars') || 0);
            
            if (currentQuestionIndex === 0 && score > 0) {
                totalGames++;
                totalStars += Math.floor(score / 10);
            }
            
            localStorage.setItem('totalGames', totalGames);
            localStorage.setItem('totalStars', totalStars);
            
            document.getElementById('totalGames').textContent = totalGames;
            document.getElementById('totalStars').textContent = totalStars;
            document.getElementById('bestStreak').textContent = localStorage.getItem('bestStreak') || 0;
            
            // Calculate time spent (simulated)
            const hours = Math.floor(totalGames * 0.5);
            document.getElementById('timeSpent').textContent = hours + 'h';
        }

        function loadProgress() {
            document.getElementById('totalGames').textContent = localStorage.getItem('totalGames') || 0;
            document.getElementById('totalStars').textContent = localStorage.getItem('totalStars') || 0;
            document.getElementById('bestStreak').textContent = localStorage.getItem('bestStreak') || 0;
        }

        // Keyboard Navigation
        document.addEventListener('keydown', (e) => {
            if (e.key === 'Escape') {
                closeGame();
            }
        });
    </script>
</body>
</html>

