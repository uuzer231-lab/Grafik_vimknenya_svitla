<!DOCTYPE html>
<html lang="uk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Графіки відключень світла — Львівська область</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --bg-color: #0f172a;
            --card-bg: #1e293b;
            --card-border: #334155;
            --text-main: #f8fafc;
            --text-muted: #94a3b8;
            --accent-light: #22c55e;
            --accent-light-bg: rgba(34, 197, 94, 0.15);
            --accent-dark: #ef4444;
            --accent-dark-bg: rgba(239, 68, 68, 0.15);
            --primary-blue: #3b82f6;
            --primary-hover: #2563eb;
            --radius-lg: 20px;
            --radius-md: 12px;
            --shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.3);
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Inter', sans-serif;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-main);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 20px 12px;
        }

        .container {
            width: 100%;
            max-width: 800px;
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        /* HEADER */
        header {
            background: var(--card-bg);
            border: 1px solid var(--card-border);
            border-radius: var(--radius-lg);
            padding: 20px 24px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: var(--shadow);
            flex-wrap: wrap;
            gap: 15px;
        }

        .brand-title {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .brand-title i {
            color: #f59e0b;
            font-size: 1.8rem;
        }

        .brand-title h1 {
            font-size: 1.3rem;
            font-weight: 700;
        }

        .update-badge {
            background: rgba(59, 130, 246, 0.15);
            border: 1px solid var(--primary-blue);
            color: #60a5fa;
            padding: 6px 14px;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 6px;
        }

        /* SELECTOR BAR */
        .controls-card {
            background: var(--card-bg);
            border: 1px solid var(--card-border);
            border-radius: var(--radius-lg);
            padding: 16px 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            gap: 15px;
            flex-wrap: wrap;
        }

        .group-selector-wrapper {
            display: flex;
            align-items: center;
            gap: 10px;
            flex: 1;
            min-width: 200px;
        }

        .group-selector-wrapper label {
            font-size: 0.95rem;
            color: var(--text-muted);
            white-space: nowrap;
        }

        select {
            background: #0f172a;
            color: #fff;
            border: 1px solid var(--card-border);
            padding: 10px 16px;
            border-radius: var(--radius-md);
            font-size: 1rem;
            font-weight: 600;
            outline: none;
            cursor: pointer;
            width: 100%;
            transition: border-color 0.2s;
        }

        select:focus {
            border-color: var(--primary-blue);
        }

        .date-tabs {
            display: flex;
            background: #0f172a;
            padding: 4px;
            border-radius: var(--radius-md);
            border: 1px solid var(--card-border);
        }

        .tab-btn {
            background: transparent;
            border: none;
            color: var(--text-muted);
            padding: 8px 16px;
            border-radius: 8px;
            font-size: 0.9rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.2s;
        }

        .tab-btn.active {
            background: var(--primary-blue);
            color: #fff;
        }

        /* STATUS DISPLAY */
        .status-card {
            background: var(--card-bg);
            border: 1px solid var(--card-border);
            border-radius: var(--radius-lg);
            padding: 24px;
            text-align: center;
            position: relative;
            overflow: hidden;
            box-shadow: var(--shadow);
        }

        .status-card.light-on {
            border-color: var(--accent-light);
            background: linear-gradient(180deg, var(--card-bg) 0%, rgba(34, 197, 94, 0.05) 100%);
        }

        .status-card.light-off {
            border-color: var(--accent-dark);
            background: linear-gradient(180deg, var(--card-bg) 0%, rgba(239, 68, 68, 0.05) 100%);
        }

        .status-icon-wrapper {
            width: 70px;
            height: 70px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 15px;
            font-size: 2rem;
        }

        .light-on .status-icon-wrapper {
            background: var(--accent-light-bg);
            color: var(--accent-light);
        }

        .light-off .status-icon-wrapper {
            background: var(--accent-dark-bg);
            color: var(--accent-dark);
        }

        .status-title {
            font-size: 1.8rem;
            font-weight: 800;
            margin-bottom: 8px;
        }

        .light-on .status-title { color: var(--accent-light); }
        .light-off .status-title { color: var(--accent-dark); }

        .status-timer {
            font-size: 1.05rem;
            color: var(--text-muted);
        }

        .status-timer span {
            color: var(--text-main);
            font-weight: 700;
        }

        /* TIMELINE CARD */
        .timeline-card {
            background: var(--card-bg);
            border: 1px solid var(--card-border);
            border-radius: var(--radius-lg);
            padding: 24px;
            box-shadow: var(--shadow);
        }

        .section-title {
            font-size: 1.1rem;
            font-weight: 700;
            margin-bottom: 16px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .timeline-bar {
            height: 28px;
            background: var(--accent-light);
            border-radius: 8px;
            position: relative;
            overflow: hidden;
            display: flex;
            margin-bottom: 12px;
            border: 1px solid rgba(255,255,255,0.1);
        }

        .timeline-segment-off {
            position: absolute;
            top: 0;
            bottom: 0;
            background: var(--accent-dark);
        }

        .timeline-labels {
            display: flex;
            justify-content: space-between;
            color: var(--text-muted);
            font-size: 0.75rem;
            padding: 0 2px;
        }

        /* OUTAGE LIST */
        .outage-intervals {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin-top: 15px;
        }

        .interval-badge {
            background: var(--accent-dark-bg);
            border: 1px solid var(--accent-dark);
            color: var(--accent-dark);
            padding: 8px 14px;
            border-radius: var(--radius-md);
            font-weight: 700;
            font-size: 0.95rem;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .empty-outage {
            background: var(--accent-light-bg);
            border: 1px solid var(--accent-light);
            color: var(--accent-light);
            padding: 12px;
            border-radius: var(--radius-md);
            text-align: center;
            font-weight: 600;
            width: 100%;
        }

        .no-data-msg {
            text-align: center;
            padding: 30px 10px;
            color: var(--text-muted);
        }

        .no-data-msg i {
            font-size: 2.5rem;
            margin-bottom: 10px;
            display: block;
            color: #64748b;
        }

        /* LEGEND */
        .legend {
            display: flex;
            gap: 20px;
            justify-content: center;
            margin-top: 15px;
            font-size: 0.85rem;
            color: var(--text-muted);
        }

        .legend-item {
            display: flex;
            align-items: center;
            gap: 6px;
        }

        .legend-box {
            width: 12px;
            height: 12px;
            border-radius: 3px;
        }

        @media (max-width: 600px) {
            header {
                flex-direction: column;
                align-items: flex-start;
            }
            .controls-card {
                flex-direction: column;
                align-items: stretch;
            }
            .date-tabs {
                width: 100%;
            }
            .tab-btn {
                flex: 1;
            }
        }
    </style>
</head>
<body>

<div class="container">
    <header>
        <div class="brand-title">
            <i class="fa-solid fa-bolt"></i>
            <h1>Світло Львівщина</h1>
        </div>
        <div class="update-badge" id="updateBadge">
            <i class="fa-solid fa-clock-rotate-left"></i>
            <span id="updateTimeText">Завантаження...</span>
        </div>
    </header>

    <div class="controls-card">
        <div class="group-selector-wrapper">
            <label for="groupSelect"><i class="fa-solid fa-layer-group"></i> Група:</label>
            <select id="groupSelect">
                <option value="1.1">Група 1.1</option>
                <option value="1.2">Група 1.2</option>
                <option value="2.1">Група 2.1</option>
                <option value="2.2">Група 2.2</option>
                <option value="3.1">Група 3.1</option>
                <option value="3.2">Група 3.2</option>
                <option value="4.1">Група 4.1</option>
                <option value="4.2">Група 4.2</option>
                <option value="5.1">Група 5.1</option>
                <option value="5.2">Група 5.2</option>
                <option value="6.1">Група 6.1</option>
                <option value="6.2">Група 6.2</option>
            </select>
        </div>

        <div class="date-tabs">
            <button class="tab-btn active" id="btnToday" onclick="switchDay('today')">Сьогодні</button>
            <button class="tab-btn" id="btnTomorrow" onclick="switchDay('tomorrow')">Завтра</button>
        </div>
    </div>

    <div class="status-card" id="statusCard">
        <div class="status-icon-wrapper" id="statusIcon">
            <i class="fa-solid fa-lightbulb"></i>
        </div>
        <div class="status-title" id="statusTitle">Завантаження...</div>
        <div class="status-timer" id="statusTimer">Розрахунок статусу...</div>
    </div>

    <div class="timeline-card">
        <div class="section-title">
            <span>Графік на день</span>
            <span style="font-size: 0.85rem; color: var(--text-muted); font-weight: normal;" id="selectedGroupLabel">Група 1.1</span>
        </div>

        <div id="timelineContent">
            <div class="timeline-bar" id="timelineBar"></div>
            <div class="timeline-labels">
                <span>00:00</span>
                <span>04:00</span>
                <span>08:00</span>
                <span>12:00</span>
                <span>16:00</span>
                <span>20:00</span>
                <span>24:00</span>
            </div>

            <div class="legend">
                <div class="legend-item">
                    <div class="legend-box" style="background: var(--accent-light);"></div>
                    <span>Світло є</span>
                </div>
                <div class="legend-item">
                    <div class="legend-box" style="background: var(--accent-dark);"></div>
                    <span>Немає світла</span>
                </div>
            </div>

            <div style="margin-top: 20px;">
                <div style="font-size: 0.9rem; color: var(--text-muted); margin-bottom: 8px;">Інтервали відключень:</div>
                <div class="outage-intervals" id="outageBadges"></div>
            </div>
        </div>

        <div id="noDataContent" class="no-data-msg" style="display: none;">
            <i class="fa-regular fa-calendar-xmark"></i>
            <div>Графік на завтра ще не оголошено Львівобленерго.</div>
        </div>
    </div>
</div>

<script>
    // ЖОРСТКО ЗАФІКСОВАНИЙ ЧАС ОНОВЛЕННЯ ГРАФІКА
    const LAST_UPDATED = new Date('2026-10-18T14:30:00');

    // ТВОЇ ВКАЗАНІ ГРАФІКИ НА СЬОГОДНІ
    const scheduleToday = {
        "1.1": ["20:00-22:30"],
        "1.2": ["11:00-14:00"],
        "2.1": ["17:00-20:00"],
        "2.2": ["11:00-14:00"],
        "3.1": ["17:00-20:00"],
        "3.2": ["14:00-17:00"],
        "4.1": ["20:00-22:30"],
        "4.2": ["10:00-12:00", "21:00-22:30"],
        "5.1": ["12:00-15:00"],
        "5.2": ["14:00-17:00"],
        "6.1": ["15:00-18:00"],
        "6.2": ["18:00-21:00"]
    };

    // ГРАФІК НА ЗАВТРА (ПОКИ НЕМАЄ)
    const scheduleTomorrow = null;

    let currentDay = 'today';
    let selectedGroup = localStorage.getItem('selectedGroup') || '1.1';

    const groupSelect = document.getElementById('groupSelect');
    groupSelect.value = selectedGroup;

    groupSelect.addEventListener('change', (e) => {
        selectedGroup = e.target.value;
        localStorage.setItem('selectedGroup', selectedGroup);
        render();
    });

    function switchDay(day) {
        currentDay = day;
        document.getElementById('btnToday').classList.toggle('active', day === 'today');
        document.getElementById('btnTomorrow').classList.toggle('active', day === 'tomorrow');
        render();
    }

    function parseTime(timeStr) {
        const [h, m] = timeStr.split(':').map(Number);
        return h * 60 + m;
    }

    function formatMinutes(min) {
        const h = Math.floor(min / 60).toString().padStart(2, '0');
        const m = (min % 60).toString().padStart(2, '0');
        return `${h}:${m}`;
    }

    function getIntervalsInMinutes(group, day) {
        const schedule = day === 'today' ? scheduleToday : scheduleTomorrow;
        if (!schedule || !schedule[group]) return [];
        return schedule[group].map(str => {
            const [startStr, endStr] = str.split('-');
            return {
                start: parseTime(startStr),
                end: parseTime(endStr),
                raw: str
            };
        });
    }

    function updateRelativeTime() {
        const now = new Date();
        const diffMs = now - LAST_UPDATED;
        const diffMins = Math.floor(diffMs / (1000 * 60));
        
        let text = "";
        if (diffMins < 1) {
            text = "Оновлено щойно";
        } else if (diffMins < 60) {
            text = `Оновлено ${diffMins} хв тому`;
        } else {
            const hours = Math.floor(diffMins / 60);
            text = `Оновлено ${hours} год тому`;
        }
        document.getElementById('updateTimeText').innerText = text;
    }

    function renderStatus() {
        const statusCard = document.getElementById('statusCard');
        const statusIcon = document.getElementById('statusIcon');
        const statusTitle = document.getElementById('statusTitle');
        const statusTimer = document.getElementById('statusTimer');

        if (currentDay === 'tomorrow') {
            statusCard.className = 'status-card';
            statusIcon.innerHTML = '<i class="fa-solid fa-circle-question"></i>';
            statusTitle.innerText = "Статус невідомий";
            statusTitle.style.color = "var(--text-main)";
            statusTimer.innerHTML = "Графік на завтра ще очікується";
            return;
        }

        const now = new Date();
        const currentMin = now.getHours() * 60 + now.getMinutes();
        const currentSec = now.getSeconds();
        const intervals = getIntervalsInMinutes(selectedGroup, 'today');

        let isOff = false;
        let activeInterval = null;
        let nextInterval = null;

        for (let i = 0; i < intervals.length; i++) {
            const inv = intervals[i];
            if (currentMin >= inv.start && currentMin < inv.end) {
                isOff = true;
                activeInterval = inv;
                break;
            }
            if (inv.start > currentMin) {
                if (!nextInterval || inv.start < nextInterval.start) {
                    nextInterval = inv;
                }
            }
        }

        if (isOff) {
            statusCard.className = 'status-card light-off';
            statusIcon.innerHTML = '<i class="fa-solid fa-lightbulb"></i>';
            statusTitle.innerText = "СВІТЛА НЕМАЄ";

            const remainingSec = (activeInterval.end - currentMin - 1) * 60 + (60 - currentSec);
            const rMin = Math.floor(remainingSec / 60);
            const rSec = remainingSec % 60;
            statusTimer.innerHTML = `З'явиться через: <span>${rMin} хв ${rSec} с</span> (о ${formatMinutes(activeInterval.end)})`;
        } else {
            statusCard.className = 'status-card light-on';
            statusIcon.innerHTML = '<i class="fa-solid fa-lightbulb"></i>';
            statusTitle.innerText = "СВІТЛО Є";

            if (nextInterval) {
                const remainingSec = (nextInterval.start - currentMin - 1) * 60 + (60 - currentSec);
                const rMin = Math.floor(remainingSec / 60);
                const rSec = remainingSec % 60;
                statusTimer.innerHTML = `Вимкнуть через: <span>${rMin} хв ${rSec} с</span> (о ${formatMinutes(nextInterval.start)})`;
            } else {
                statusTimer.innerHTML = "До кінця дня вимкнень більше не планується";
            }
        }
    }

    function renderTimeline() {
        document.getElementById('selectedGroupLabel').innerText = `Група ${selectedGroup}`;
        const timelineContent = document.getElementById('timelineContent');
        const noDataContent = document.getElementById('noDataContent');
        const timelineBar = document.getElementById('timelineBar');
        const outageBadges = document.getElementById('outageBadges');

        const intervals = getIntervalsInMinutes(selectedGroup, currentDay);

        if (currentDay === 'tomorrow' && !scheduleTomorrow) {
            timelineContent.style.display = 'none';
            noDataContent.style.display = 'block';
            return;
        }

        timelineContent.style.display = 'block';
        noDataContent.style.display = 'none';
        timelineBar.innerHTML = '';
        outageBadges.innerHTML = '';

        intervals.forEach(inv => {
            const leftPct = (inv.start / 1440) * 100;
            const widthPct = ((inv.end - inv.start) / 1440) * 100;

            const segment = document.createElement('div');
            segment.className = 'timeline-segment-off';
            segment.style.left = `${leftPct}%`;
            segment.style.width = `${widthPct}%`;
            timelineBar.appendChild(segment);

            const badge = document.createElement('div');
            badge.className = 'interval-badge';
            badge.innerHTML = `<i class="fa-solid fa-plug-circle-xmark"></i> ${inv.raw}`;
            outageBadges.appendChild(badge);
        });

        if (intervals.length === 
