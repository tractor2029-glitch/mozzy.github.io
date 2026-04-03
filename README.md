<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ускорение компьютера</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&display=swap" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        :root {
            --bg-dark: #050507;
            --bg-card: #0f111a;
            --bg-card-hover: #161a29;
            --primary-blue: #2563eb;
            --secondary-blue: #3b82f6;
            --accent-cyan: #06b6d4;
            --text-main: #e2e8f0;
            --text-muted: #94a3b8;
            --border-color: #1e293b;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', sans-serif;
            background-color: var(--bg-dark);
            color: var(--text-main);
            line-height: 1.6;
            overflow-x: hidden;
        }

        /* Utility */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        h1, h2, h3 {
            color: #fff;
            margin-bottom: 1rem;
        }

        h2 {
            font-size: 2.2rem;
            position: relative;
            display: inline-block;
            margin-bottom: 3rem;
        }

        h2::after {
            content: '';
            position: absolute;
            left: 0;
            bottom: -10px;
            width: 60px;
            height: 4px;
            background: var(--secondary-blue);
            border-radius: 2px;
        }

        p {
            color: var(--text-muted);
            margin-bottom: 1.5rem;
        }

        section {
            padding: 80px 0;
        }

        /* Header */
        header {
            background: rgba(5, 5, 7, 0.95);
            backdrop-filter: blur(10px);
            position: fixed;
            top: 0;
            width: 100%;
            z-index: 1000;
            border-bottom: 1px solid var(--border-color);
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            height: 70px;
        }

        .logo {
            font-size: 1.2rem;
            font-weight: 700;
            color: #fff;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .logo span {
            color: var(--secondary-blue);
        }

        .nav-links {
            display: flex;
            gap: 30px;
        }

        .nav-links a {
            color: var(--text-muted);
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s;
        }

        .nav-links a:hover {
            color: var(--secondary-blue);
        }

        /* Hero */
        .hero {
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            background: radial-gradient(circle at 50% 50%, rgba(37, 99, 235, 0.15) 0%, transparent 50%);
            position: relative;
        }

        .hero-content {
            text-align: center;
            max-width: 800px;
        }

        .hero h1 {
            font-size: 3.5rem;
            line-height: 1.2;
            margin-bottom: 1.5rem;
            background: linear-gradient(to right, #fff, #60a5fa);
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
            color: transparent;
        }

        .hero p {
            font-size: 1.25rem;
            margin-bottom: 2.5rem;
        }

        .btn {
            display: inline-block;
            padding: 12px 30px;
            background: var(--primary-blue);
            color: #fff;
            border-radius: 50px;
            text-decoration: none;
            font-weight: 600;
            transition: all 0.3s;
            box-shadow: 0 4px 20px rgba(37, 99, 235, 0.4);
        }

        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(37, 99, 235, 0.6);
            background: #3b82f6;
        }

        .scroll-down {
            position: absolute;
            bottom: 40px;
            left: 50%;
            transform: translateX(-50%);
            animation: bounce 2s infinite;
        }

        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% {transform: translateY(0) translateX(-50%);}
            40% {transform: translateY(-15px) translateX(-50%);}
            60% {transform: translateY(-7px) translateX(-50%);}
        }

        /* Cards */
        .grid-3 {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            margin-bottom: 40px;
        }

        .card {
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            border-radius: 16px;
            padding: 30px;
            transition: all 0.3s;
            position: relative;
            overflow: hidden;
        }

        .card:hover {
            transform: translateY(-5px);
            border-color: var(--primary-blue);
            background: var(--bg-card-hover);
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
        }

        .card-icon {
            width: 50px;
            height: 50px;
            background: rgba(37, 99, 235, 0.1);
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 20px;
        }

        .card-icon svg {
            width: 24px;
            height: 24px;
            stroke: var(--secondary-blue);
        }

        .card h3 {
            font-size: 1.4rem;
            margin-bottom: 10px;
        }

        /* Steps */
        .step {
            display: flex;
            gap: 30px;
            margin-bottom: 40px;
            align-items: flex-start;
        }

        .step-number {
            min-width: 50px;
            height: 50px;
            background: var(--primary-blue);
            color: #fff;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 700;
            font-size: 1.5rem;
            flex-shrink: 0;
        }

        .step-content h3 {
            margin-top: 5px;
        }

        .step-content .code-block {
            background: #050507;
            padding: 15px;
            border-radius: 8px;
            border: 1px solid var(--border-color);
            font-family: monospace;
            color: var(--text-main);
            margin-bottom: 10px;
        }

        /* Survey Section */
        .survey-stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
            gap: 40px;
            margin-top: 40px;
        }

        .chart-container {
            background: var(--bg-card);
            padding: 20px;
            border-radius: 16px;
            border: 1px solid var(--border-color);
            height: 400px;
            position: relative;
        }

        /* Footer */
        footer {
            background: #020305;
            padding: 40px 0;
            border-top: 1px solid var(--border-color);
            text-align: center;
            color: var(--text-muted);
        }

        /* Animation classes */
        .fade-in {
            opacity: 0;
            transform: translateY(30px);
            transition: opacity 0.6s ease-out, transform 0.6s ease-out;
        }

        .fade-in.visible {
            opacity: 1;
            transform: translateY(0);
        }

        /* Mobile */
        @media (max-width: 768px) {
            .hero h1 { font-size: 2.5rem; }
            .nav-links { display: none; }
            .step { flex-direction: column; gap: 15px; }
            .survey-stats { grid-template-columns: 1fr; }
        }
    </style>
</head>
<body>

    <!-- Header -->
    <header>
        <div class="container">
            <nav>
                <div class="logo">
                    <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                        <path d="M12 2v4M12 18v4M4.93 4.93l2.83 2.83M16.24 16.24l2.83 2.83M2 12h4M18 12h4M4.93 19.07l2.83-2.83M16.24 7.76l2.83-2.83"/>
                    </svg>
                    PC<span>Speed</span>
                </div>
                <div class="nav-links">
                    <a href="#reasons">Причины</a>
                    <a href="#solutions">Решения</a>
                    <a href="#survey">Статистика</a>
                    <a href="#hardware">Апгрейд</a>
                </div>
            </nav>
        </div>
    </header>

    <!-- Hero -->
    <section class="hero">
        <div class="container hero-content">
            <h1 class="fade-in">Способы увеличения быстродействия компьютера</h1>
            <p class="fade-in">Практическое руководство для любого пользователя. Как вернуть скорость вашему ПК без лишних затрат и сложных настроек.</p>
            <div class="fade-in">
                <a href="#solutions" class="btn">Начать ускорение</a>
            </div>
        </div>
        <div class="scroll-down">
            <svg width="30" height="30" viewBox="0 0 24 24" fill="none" stroke="var(--secondary-blue)" stroke-width="2">
                <path d="M7 13l5 5 5-5M7 6l5 5 5-5"/>
            </svg>
        </div>
    </section>

    <!-- Reasons -->
    <section id="reasons">
        <div class="container">
            <h2 class="fade-in">Почему ПК тормозит?</h2>
            <div class="grid-3">
                <div class="card fade-in">
                    <div class="card-icon">
                        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="3" width="18" height="18" rx="2" ry="2"/><line x1="9" y1="3" x2="9" y2="21"/></svg>
                    </div>
                    <h3>Перегрузка ПО</h3>
                    <p>Каждая установленная программа оставляет свои невидимые следы в системе даже после удаления. Чем больше программ прошло через компьютер, тем тяжелее ему работать.</p>
                </div>
                <div class="card fade-in">
                    <div class="card-icon">
                        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M13 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V9z"/><polyline points="13 2 13 9 20 9"/></svg>
                    </div>
                    <h3>Цифровой мусор</h3>
                    <p>Временные файлы, кэш браузеров и забытые установщики игр незаметно засоряют память компьютера, мешая системе находить важные данные.</p>
                </div>
                <div class="card fade-in">
                    <div class="card-icon">
                        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"/><line x1="12" y1="8" x2="12" y2="12"/><line x1="12" y1="16" x2="12.01" y2="16"/></svg>
                    </div>
                    <h3>Автозагрузка</h3>
                    <p>Десятки программ запускаются вместе с Windows, потребляя ресурсы в фоне. Вы закрываете приложение, а оно все равно работает, отнимая ресурсы.</p>
                </div>
            </div>
            <div class="grid-3" style="margin-top: 10px;">
                <div class="card fade-in">
                    <div class="card-icon">
                        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M18.36 6.64a9 9 0 1 1-12.73 0"/><line x1="12" y1="2" x2="12" y2="12"/></svg>
                    </div>
                    <h3>Вирусы</h3>
                    <p>Вредоносное ПО может скрытно использовать вычислительную мощность вашего процессора для своих задач или шпионить за вами.</p>
                </div>
                <div class="card fade-in">
                    <div class="card-icon">
                        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"/></svg>
                    </div>
                    <h3>Перегрев</h3>
                    <p>Пыль и старая термопаста заставляют процессор снижать частоты (троттлинг), чтобы не сгореть. Регулярная чистка может вернуть производительность.</p>
                </div>
                <div class="card fade-in">
                    <div class="card-icon">
                        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="4 17 10 11 4 5"/><line x1="12" y1="19" x2="20" y2="19"/></svg>
                    </div>
                    <h3>Устаревание</h3>
                    <p>Современные приложения требуют больше ресурсов. Старый HDD и мало ОЗУ становятся узким местом при запуске современных задач.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Solutions -->
    <section id="solutions" style="background: var(--bg-card);">
        <div class="container">
            <h2 class="fade-in">Как ускорить ПК?</h2>
            
            <div class="step fade-in">
                <div class="step-number">1</div>
                <div class="step-content">
                    <h3>Очистка диска</h3>
                    <p>Удалите временные файлы и очистите корзину. Диск С должен иметь хотя бы 10-15 Гб свободного места.</p>
                    <div class="code-block">
                        Пуск → Введите "очистка диска" → Выберите диск C → Отметьте галочками все пункты → ОК.
                    </div>
                    <p style="font-size: 0.9rem;">Не храните фильмы и игры на диске C. Переносите их на диск D или внешние накопители.</p>
                </div>
            </div>

            <div class="step fade-in">
                <div class="step-number">2</div>
                <div class="step-content">
                    <h3>Отключение автозагрузки</h3>
                    <p>Ускорьте запуск системы, убрав лишнее.</p>
                    <div class="code-block">
                        Нажмите Ctrl + Shift + Esc → Вкладка "Автозагрузка" → Нажмите ПКМ на ненужные программы → "Отключить".
                    </div>
                    <p style="font-size: 0.9rem;">Важно: отключайте только известные программы (торренты, мессенджеры). Системные процессы не трогайте.</p>
                </div>
            </div>

            <div class="step fade-in">
                <div class="step-number">3</div>
                <div class="step-content">
                    <h3>Защита от вирусов</h3>
                    <p>Используйте бесплатный антивирус (Защитник Windows, Kaspersky Free, Avast).</p>
                    <p>Регулярно запускайте полную проверку системы (раз в месяц). Это снимет лишнюю нагрузку, вызванную вредоносным ПО.</p>
                </div>
            </div>

            <div class="step fade-in">
                <div class="step-number">4</div>
                <div class="step-content">
                    <h3>Обновление ПО</h3>
                    <p>Обновления Windows закрывают "дыры" безопасности и исправляют ошибки производительности. Не игнорируйте их!</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Hardware -->
    <section id="hardware">
        <div class="container">
            <h2 class="fade-in">Аппаратный апгрейд</h2>
            <div class="grid-3">
                <div class="card fade-in">
                    <h3>Замена HDD на SSD</h3>
                    <p>Самый эффективный способ. SSD работает на основе чипов памяти и увеличивает скорость загрузки в 5-10 раз. Программы начинают открываться мгновенно.</p>
                </div>
                <div class="card fade-in">
                    <h3>Увеличение ОЗУ</h3>
                    <p>Оперативная память хранит данные запущенных программ. Если памяти мало (4 Гб), добавьте планку до 8 или 16 Гб для комфортной работы с браузером и приложениями.</p>
                </div>
                <div class="card fade-in">
                    <h3>Чистка от пыли</h3>
                    <p>Продуйте компьютер сжатым воздухом и замените термопасту на процессоре (раз в 2-3 года). Это устранит перегрев и вернет стабильную работу на высоких частотах.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Survey -->
    <section id="survey" style="background: var(--bg-card);">
        <div class="container">
            <h2 class="fade-in">Статистика использования ПК</h2>
            <p class="fade-in">Результаты опроса студентов о проблемах с производительностью компьютеров.</p>
            
            <div class="survey-stats">
                <div class="chart-container fade-in">
                    <canvas id="usageChart"></canvas>
                </div>
                <div class="chart-container fade-in">
                    <canvas id="problemsChart"></canvas>
                </div>
                <div class="chart-container fade-in">
                    <canvas id="knowledgeChart"></canvas>
                </div>
                <div class="chart-container fade-in">
                    <canvas id="desireChart"></canvas>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="container">
            <p>&copy; 2026 PC Speed Guide. Все права защищены.</p>
            <p style="font-size: 0.9rem; margin-top: 10px;">Источники: Семакин И.Г., Microsoft Support, Касперский Е.В., Гребенюк Е.И.</p>
        </div>
    </footer>

    <script>
        // Animation Observer
        const observerOptions = { threshold: 0.1 };
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, observerOptions);

        document.querySelectorAll('.fade-in').forEach(el => observer.observe(el));

        // Charts Configuration
        Chart.defaults.color = '#94a3b8';
        Chart.defaults.borderColor = '#1e293b';
        
        // 1. Usage Chart (Doughnut)
        const usageCtx = document.getElementById('usageChart').getContext('2d');
        new Chart(usageCtx, {
            type: 'doughnut',
            data: {
                labels: ['Ежедневно', 'Несколько раз в неделю', 'Редко', 'Практически не использую'],
                datasets: [{
                    data: [45, 35, 15, 5],
                    backgroundColor: ['#3b82f6', '#2563eb', '#1e40af', '#0f172a'],
                    borderWidth: 0
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    title: { display: true, text: 'Частота использования ПК', color: '#fff', font: { size: 16 } },
                    legend: { position: 'bottom' }
                }
            }
        });

        // 2. Problems Chart (Pie)
        const problemsCtx = document.getElementById('problemsChart').getContext('2d');
        new Chart(problemsCtx, {
            type: 'pie',
            data: {
                labels: ['Да, сталкивался', 'Нет, не сталкивался', 'Затрудняюсь ответить'],
                datasets: [{
                    data: [75, 20, 5],
                    backgroundColor: ['#06b6d4', '#3b82f6', '#475569'],
                    borderWidth: 0
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    title: { display: true, text: 'Сталкивались ли с замедлением ПК?', color: '#fff', font: { size: 16 } },
                    legend: { position: 'bottom' }
                }
            }
        });

        // 3. Knowledge Chart (Bar)
        const knowledgeCtx = document.getElementById('knowledgeChart').getContext('2d');
        new Chart(knowledgeCtx, {
            type: 'bar',
            data: {
                labels: ['Новичок', 'Начинающий', 'Средний', 'Эксперт'],
                datasets: [{
                    label: 'Уровень знаний',
                    data: [15, 25, 45, 15],
                    backgroundColor: '#2563eb',
                    borderRadius: 5
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    title: { display: true, text: 'Уровень знаний студентов', color: '#fff', font: { size: 16 } },
                    legend: { display: false }
                },
                scales: {
                    y: { beginAtZero: true, grid: { color: '#1e293b' } },
                    x: { grid: { display: false } }
                }
            }
        });

        // 4. Desire Chart (Bar)
        const desireCtx = document.getElementById('desireChart').getContext('2d');
        new Chart(desireCtx, {
            type: 'bar',
            data: {
                labels: ['Да, очень хочу', 'Возможно', 'Нет', 'Уже знаю'],
                datasets: [{
                    label: 'Желание получить инструкцию',
                    data: [30, 35, 20, 15],
                    backgroundColor: ['#06b6d4', '#3b82f6', '#1e40af', '#0f172a'],
                    borderRadius: 5
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    title: { display: true, text: 'Нужна ли инструкция?', color: '#fff', font: { size: 16 } },
                    legend: { display: false }
                },
                scales: {
                    y: { beginAtZero: true, grid: { color: '#1e293b' } },
                    x: { grid: { display: false } }
                }
            }
        });
    </script>
</body>
</html>
