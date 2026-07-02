<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>VAYRO FM | Mağaza Radyosu</title>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;600&family=Playfair+Display:wght@400;600&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --brand-black: #111111;
            --brand-white: #ffffff;
            --brand-bg: #f4f4f4;
            --brand-accent: #C89B7B;
            --brand-border: #e0e0e0;
            --brand-red: #d32f2f;
        }

        body {
            font-family: 'Montserrat', sans-serif;
            background-color: var(--brand-bg);
            color: var(--brand-black);
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            min-height: 100vh;
        }

        .top-navbar {
            width: 100%;
            background-color: var(--brand-white);
            padding: 20px 40px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-sizing: border-box;
            border-bottom: 1px solid var(--brand-border);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .top-navbar .logo {
            font-family: 'Playfair Display', serif;
            font-size: 32px;
            letter-spacing: 4px;
            color: var(--brand-black);
            margin: 0;
        }

        .top-navbar .fm-tag {
            font-family: 'Montserrat', sans-serif;
            font-size: 12px;
            letter-spacing: 2px;
            color: var(--brand-accent);
            vertical-align: super;
        }

        .top-navbar .mock-icons {
            font-size: 20px;
            letter-spacing: 15px;
            color: var(--brand-black);
            font-weight: 300;
        }

        .main-wrapper {
            display: flex;
            flex-direction: column;
            gap: 25px;
            width: 100%;
            max-width: 800px;
            padding: 30px 20px;
            box-sizing: border-box;
            margin-bottom: 20px;
        }

        .container {
            background-color: var(--brand-white);
            padding: 35px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.03);
            border: 1px solid var(--brand-border);
        }

        h2 { 
            font-family: 'Playfair Display', serif;
            font-size: 22px; 
            color: var(--brand-black); 
            border-bottom: 1px solid var(--brand-border); 
            padding-bottom: 15px; 
            margin-top: 0; 
            letter-spacing: 1px; 
            font-weight: 600;
        }
        
        .subtitle { color: #666; font-size: 13px; margin-bottom: 20px; letter-spacing: 0.5px; }
        
        .player-section { 
            background: #fafafa; 
            padding: 25px; 
            border: 1px solid var(--brand-border); 
            margin-bottom: 25px; 
            text-align: center; 
        }
        
        .now-playing { 
            font-family: 'Playfair Display', serif;
            font-size: 20px; 
            color: var(--brand-accent); 
            margin: 20px 0; 
            min-height: 28px; 
            font-style: italic;
        }

        .player-controls { display: flex; justify-content: center; gap: 10px; margin-top: 15px; }
        
        .player-btn { 
            background: var(--brand-white); 
            color: var(--brand-black); 
            border: 1px solid var(--brand-black); 
            padding: 10px 25px; 
            cursor: pointer; 
            font-family: 'Montserrat', sans-serif;
            font-size: 12px;
            letter-spacing: 1px;
            text-transform: uppercase;
            transition: 0.3s; 
        }
        
        .player-btn:hover { background: var(--brand-black); color: var(--brand-white); }
        .player-btn.active-play { background: var(--brand-black); color: var(--brand-white); }
        
        .file-upload-wrapper { position: relative; overflow: hidden; display: inline-block; width: 100%; margin-bottom: 10px;}
        .file-upload-btn { 
            background: var(--brand-white); 
            color: var(--brand-black); 
            padding: 15px; 
            border: 1px dashed var(--brand-black); 
            width: 100%; cursor: pointer; font-size: 13px; box-sizing: border-box; display: block; text-align: center; 
            letter-spacing: 1px;
            text-transform: uppercase;
        }
        .file-upload-btn:hover { background: #f9f9f9; }
        .file-upload-wrapper input[type=file] { font-size: 100px; position: absolute; left: 0; top: 0; opacity: 0; cursor: pointer; height: 100%; }

        /* Yeni Ses Seviyesi (Volume) Ayarı Stili */
        .volume-control {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;
            margin-top: 25px;
            padding-top: 15px;
            border-top: 1px solid var(--brand-border);
        }
        .volume-control input[type="range"] {
            width: 60%;
            cursor: pointer;
            accent-color: var(--brand-black);
            padding: 0;
            border: none;
            background: transparent;
        }
        .volume-icon { font-size: 18px; color: var(--brand-black); }

        .audio-selector { margin-bottom: 20px; display: flex; flex-direction: column; gap: 10px;}
        .audio-selector label { font-weight: 600; color: var(--brand-black); font-size: 13px; letter-spacing: 0.5px; text-transform: uppercase;}
        
        select, input[type="time"], input[type="number"] { 
            padding: 12px; 
            border: 1px solid var(--brand-border); 
            background: var(--brand-white); 
            color: var(--brand-black); 
            width: 100%; 
            box-sizing: border-box;
            font-family: 'Montserrat', sans-serif;
            font-size: 14px;
            outline: none;
        }
        select:focus, input:focus { border-color: var(--brand-black); }
        
        button.btn-primary { 
            background-color: var(--brand-black); 
            color: var(--brand-white); 
            border: none; 
            padding: 18px; 
            font-size: 14px; 
            letter-spacing: 1px;
            cursor: pointer; 
            width: 100%; 
            transition: 0.3s; 
            text-transform: uppercase;
        }
        button.btn-primary:hover { background-color: #333; }
        
        .task-creator { background-color: #fafafa; padding: 25px; border: 1px solid var(--brand-border); display: flex; flex-direction: column; gap: 15px; }
        .task-row { display: flex; align-items: center; gap: 10px; flex-wrap: wrap;}
        .task-row input[type="radio"] { margin-right: 5px; cursor: pointer; accent-color: var(--brand-black); }
        .task-row label { font-size: 13px; cursor: pointer; display: flex; align-items: center; color: var(--brand-black); width: 100%; font-weight: 500;}
        .input-group { display: flex; align-items: center; gap: 10px; margin-left: 25px; width: 100%; }
        .time-input, .interval-input { width: 120px; }
        .interval-input { width: 80px; }
        
        button.btn-add { 
            background-color: var(--brand-white); 
            color: var(--brand-black); 
            border: 1px solid var(--brand-black); 
            padding: 15px; 
            font-size: 13px; 
            cursor: pointer; 
            width: 100%; 
            transition: 0.3s; 
            margin-top: 10px; 
            text-transform: uppercase;
            letter-spacing: 1px;
        }
        button.btn-add:hover { background-color: var(--brand-black); color: var(--brand-white); }

        .task-list { margin-top: 15px; display: flex; flex-direction: column; gap: 10px; }
        .task-item { 
            background: var(--brand-white); 
            border: 1px solid var(--brand-border); 
            padding: 15px; 
            display: flex; 
            justify-content: space-between; 
            align-items: center; 
            border-left: 3px solid var(--brand-accent); 
        }
        .task-info { flex: 1; display: flex; flex-direction: column; gap: 6px; padding-right: 15px; }
        .task-badge { font-size: 10px; font-weight: 600; padding: 4px 10px; display: inline-block; width: fit-content; background: #f0f0f0; color: #333; letter-spacing: 1px; text-transform: uppercase;}
        .task-title { font-size: 14px; font-weight: 600; color: var(--brand-black); }
        .btn-delete { 
            background: transparent; 
            color: var(--brand-red); 
            border: 1px solid var(--brand-red); 
            padding: 6px 15px; 
            cursor: pointer; 
            font-size: 11px; 
            text-transform: uppercase;
            letter-spacing: 1px;
            transition: 0.2s; 
        }
        .btn-delete:hover { background: var(--brand-red); color: var(--brand-white); }
        .empty-state { text-align: center; color: #888; font-size: 13px; padding: 25px; background: #fafafa; border: 1px dashed var(--brand-border); }

        .status { text-align: center; margin-top: 20px; font-size: 13px; color: var(--brand-black); font-weight: 600; letter-spacing: 1px; text-transform: uppercase;}
        .error-text { color: var(--brand-red); }
        .hidden { display: none !important; }
    </style>
</head>
<body>

<div class="top-navbar">
    <h1 class="logo">VAYRO <span class="fm-tag">FM</span></h1>
    <div class="mock-icons">♡⚲👤🛍</div>
</div>

<div class="main-wrapper">
    <div class="container">
        <h2>Radyo Yayını</h2>
        <div class="subtitle">Mağaza İçi Müzik ve Otomatik Anons Yönetimi</div>
        
        <div class="player-section">
            <div class="file-upload-wrapper">
                <div class="file-upload-btn">Müzik Klasörünü Seçin (Playlist Oluştur)</div>
                <input type="file" id="musicFiles" multiple accept="audio/mp3, audio/wav, audio/m4a">
            </div>
            
            <div class="now-playing" id="nowPlaying">Müzik Bekleniyor...</div>
            
            <div class="player-controls">
                <button class="player-btn" onclick="prevTrack()">Önceki</button>
                <button class="player-btn active-play" id="playPauseBtn" onclick="togglePlayPause()">Başlat</button>
                <button class="player-btn" onclick="nextTrack()">Sonraki</button>
            </div>

            <!-- Yeni Eklenen Ses Seviyesi Kontrolü -->
            <div class="volume-control">
                <span class="volume-icon">🔉</span>
                <input type="range" id="volumeSlider" min="0" max="1" step="0.01" value="0.7" title="Radyo Ses Seviyesi">
                <span class="volume-icon">🔊</span>
            </div>
            <div style="font-size: 11px; color: #888; margin-top: 15px; letter-spacing: 0.5px;">*Anons girdiğinde müzik otomatik olarak kısılır.</div>
        </div>

        <div class="audio-selector">
            <label for="audioSelect">Anons Tetikleyici:</label>
            <select id="audioSelect">
                <option value="kapanis">Kapanış Anonsu (10 Dk. Uyarısı)</option>
                <option value="kampanya">Kampanya Anonsu (%50 İndirim Kırmızı Etiket)</option>
            </select>
        </div>

        <button class="btn-primary" onclick="triggerAnnouncement(document.getElementById('audioSelect').value)">Seçili Anonsu Şimdi Çal</button>
        <div class="status" id="statusText">SİSTEM YAYINA HAZIR</div>
    </div>

    <div class="container">
        <h2>Yayın Akışı Planlama</h2>
        
        <div class="task-creator">
            <div style="font-size: 12px; color: #666; margin-bottom: 5px; text-transform: uppercase; letter-spacing: 1px;">Otomasyon Kuralı Seçin</div>
            
            <div class="task-row">
                <label><input type="radio" name="scheduleType" value="time" checked onchange="toggleInputTypes()"> Belirli Saatte 1 Kez Çal</label>
                <div id="timeInputs" class="input-group">
                    <input type="time" id="timeInput" class="time-input">
                </div>
            </div>

            <div class="task-row">
                <label><input type="radio" name="scheduleType" value="interval" onchange="toggleInputTypes()"> Gün Boyu Düzenli Tekrarla</label>
                <div id="intervalInputs" class="input-group hidden">
                    <input type="number" id="intervalInput" class="interval-input" min="1" max="240" placeholder="Örn: 30">
                    <span style="font-size: 12px; color: #666;">Dk. bir</span>
                </div>
            </div>

            <div class="task-row">
                <label><input type="radio" name="scheduleType" value="range" onchange="toggleInputTypes()"> İki Saat Arasında Tekrarla (Kapanış/Yoğunluk)</label>
                <div id="rangeInputs" class="input-group hidden">
                    <input type="time" id="rangeStart" class="time-input">
                    <span style="color:#666;">-</span>
                    <input type="time" id="rangeEnd" class="time-input">
                    <span style="margin-left:5px; color:#666;">her</span>
                    <input type="number" id="rangeInterval" class="interval-input" min="1" max="60" placeholder="Örn:10">
                    <span style="font-size: 12px; color: #666;">dk</span>
                </div>
            </div>

            <button class="btn-add" onclick="addTask()">Yayın Akışına Ekle</button>
        </div>

        <h2 style="margin-top: 35px;">Planlanan Anonslar</h2>
        <div id="taskList" class="task-list">
            <div class="empty-state" id="emptyState">Şu an planlanmış bir anons bulunmuyor.</div>
        </div>
    </div>
</div>

<script>
    let musicPlaylist = [];
    let currentTrackIndex = 0;
    const backgroundMusic = new Audio();
    const playPauseBtn = document.getElementById('playPauseBtn');
    const nowPlayingText = document.getElementById('nowPlaying');
    
    // Ses Seviyesi Değişkenleri
    const volumeSlider = document.getElementById('volumeSlider');
    let userVolume = parseFloat(volumeSlider.value);
    let isDucking = false;

    backgroundMusic.volume = userVolume;

    // Ses Çubuğu Hareket Ettiğinde
    volumeSlider.addEventListener('input', function() {
        userVolume = parseFloat(this.value);
        if (!isDucking) {
            backgroundMusic.volume = userVolume;
        }
    });
    
    document.getElementById('musicFiles').addEventListener('change', function(e) {
        musicPlaylist = Array.from(e.target.files);
        if(musicPlaylist.length > 0) {
            currentTrackIndex = 0;
            loadAndPlayTrack(currentTrackIndex);
        }
    });

    function loadAndPlayTrack(index) {
        if(musicPlaylist.length === 0) return;
        if(index >= musicPlaylist.length) index = 0; 
        if(index < 0) index = musicPlaylist.length - 1; 
        
        currentTrackIndex = index;
        const file = musicPlaylist[index];
        backgroundMusic.src = URL.createObjectURL(file);
        
        nowPlayingText.innerText = file.name.replace(/\.[^/.]+$/, "");
        
        backgroundMusic.play();
        playPauseBtn.innerText = "Duraklat";
    }

    backgroundMusic.addEventListener('ended', () => { nextTrack(); });

    function togglePlayPause() {
        if(musicPlaylist.length === 0) { alert("Lütfen önce klasörden müzik seçin!"); return; }
        if (backgroundMusic.paused) {
            backgroundMusic.play();
            playPauseBtn.innerText = "Duraklat";
        } else {
            backgroundMusic.pause();
            playPauseBtn.innerText = "Başlat";
        }
    }

    function nextTrack() { loadAndPlayTrack(currentTrackIndex + 1); }
    function prevTrack() { loadAndPlayTrack(currentTrackIndex - 1); }

    // Akıllı Ducking Sistemi (Kullanıcı sesine göre ayarlanır)
    let fadeInterval;
    function fadeOutMusic() {
        isDucking = true;
        clearInterval(fadeInterval);
        let targetVolume = userVolume * 0.15; // Müziği ayarlanan sesin %15'ine düşürür
        
        fadeInterval = setInterval(() => {
            if (backgroundMusic.volume > targetVolume + 0.05) {
                backgroundMusic.volume -= 0.05;
            } else {
                backgroundMusic.volume = targetVolume;
                clearInterval(fadeInterval);
            }
        }, 100);
    }

    function fadeInMusic() {
        clearInterval(fadeInterval);
        fadeInterval = setInterval(() => {
            if (backgroundMusic.volume < userVolume - 0.05) {
                backgroundMusic.volume += 0.05;
            } else {
                backgroundMusic.volume = userVolume;
                isDucking = false;
                clearInterval(fadeInterval);
            }
        }, 100);
    }

    const statusText = document.getElementById('statusText');
    const audioSelect = document.getElementById('audioSelect');
    let scheduledTasks = []; 
    let currentAudio = null; 

    function triggerAnnouncement(audioFileKey) {
        if (currentAudio) {
            currentAudio.pause();
            currentAudio.currentTime = 0;
        }

        if (!backgroundMusic.paused) { fadeOutMusic(); }

        statusText.className = 'status'; 
        statusText.innerHTML = 'JİNGLE ÇALINIYOR...';
        
        const chime = new Audio('jingle.mp3');
        currentAudio = chime;
        
        chime.play().then(() => {
            chime.onended = () => { playMainAudio(audioFileKey); };
        }).catch((e) => {
            playMainAudio(audioFileKey);
        });
    }

    function playMainAudio(audioFileKey) {
        statusText.innerHTML = 'ANONS YAYINDA...';
        
        const mainAudio = new Audio(audioFileKey + '.mp3');
        currentAudio = mainAudio;

        mainAudio.play().then(() => {
            mainAudio.onended = () => {
                statusText.innerHTML = 'SİSTEM YAYINA HAZIR';
                currentAudio = null;
                if (!backgroundMusic.paused) { fadeInMusic(); }
            };
        }).catch((e) => {
            statusText.className = 'status error-text';
            statusText.innerHTML = `⚠️ HATA: ${audioFileKey}.mp3 BULUNAMADI!`;
            currentAudio = null;
            fadeInMusic(); 
        });
    }

    function toggleInputTypes() {
        const type = document.querySelector('input[name="scheduleType"]:checked').value;
        document.getElementById('timeInputs').classList.add('hidden');
        document.getElementById('intervalInputs').classList.add('hidden');
        document.getElementById('rangeInputs').classList.add('hidden');

        if (type === 'time') document.getElementById('timeInputs').classList.remove('hidden');
        if (type === 'interval') document.getElementById('intervalInputs').classList.remove('hidden');
        if (type === 'range') document.getElementById('rangeInputs').classList.remove('hidden');
    }

    function addTask() {
        const audioKey = audioSelect.value;
        const audioName = audioSelect.options[audioSelect.selectedIndex].text;
        const type = document.querySelector('input[name="scheduleType"]:checked').value;

        const task = {
            id: Date.now().toString(),
            audioKey: audioKey,
            audioName: audioName,
            type: type,
            lastPlayedMinute: null
        };

        if (type === 'time') {
            const timeVal = document.getElementById('timeInput').value;
            if (!timeVal) { alert('Lütfen bir saat seçin!'); return; }
            task.value = timeVal;
            task.label = `SAAT: ${timeVal}`;

        } else if (type === 'interval') {
            const intervalVal = document.getElementById('intervalInput').value;
            if (!intervalVal || intervalVal <= 0) { alert('Lütfen dakika girin!'); return; }
            task.value = parseInt(intervalVal);
            task.label = `DÖNGÜ: ${intervalVal} DK`;
            
            task.timerId = setInterval(() => { triggerAnnouncement(task.audioKey); }, task.value * 60 * 1000);
            triggerAnnouncement(task.audioKey);

        } else if (type === 'range') {
            const start = document.getElementById('rangeStart').value;
            const end = document.getElementById('rangeEnd').value;
            const intervalVal = parseInt(document.getElementById('rangeInterval').value);

            if (!start || !end || !intervalVal || intervalVal <= 0) {
                alert('Tüm alanları doldurun!'); return;
            }

            let triggerTimes = [];
            let [startH, startM] = start.split(':').map(Number);
            let [endH, endM] = end.split(':').map(Number);
            let startTotal = startH * 60 + startM;
            let endTotal = endH * 60 + endM;

            if (endTotal < startTotal) endTotal += 24 * 60; 

            for (let t = startTotal; t <= endTotal; t += intervalVal) {
                let h = Math.floor(t / 60) % 24;
                let m = t % 60;
                let timeStr = `${h.toString().padStart(2, '0')}:${m.toString().padStart(2, '0')}`;
                triggerTimes.push(timeStr);
            }

            task.value = triggerTimes; 
            task.label = `ARALIK: ${start}-${end} / ${intervalVal} DK`;
        }

        scheduledTasks.push(task);
        renderTasks();
    }

    function removeTask(id) {
        const taskIndex = scheduledTasks.findIndex(t => t.id === id);
        if (taskIndex > -1) {
            if (scheduledTasks[taskIndex].timerId) {
                clearInterval(scheduledTasks[taskIndex].timerId);
            }
            scheduledTasks.splice(taskIndex, 1);
            renderTasks();
        }
    }

    function renderTasks() {
        const taskListDiv = document.getElementById('taskList');
        const emptyState = document.getElementById('emptyState');
        
        document.querySelectorAll('.task-item').forEach(el => el.remove());

        if (scheduledTasks.length === 0) {
            emptyState.style.display = 'block';
            return;
        } else {
            emptyState.style.display = 'none';
        }

        scheduledTasks.forEach(task => {
            const item = document.createElement('div');
            item.className = 'task-item';
            
            item.innerHTML = `
                <div class="task-info">
                    <span class="task-badge">${task.label}</span>
                    <div class="task-title">${task.audioName}</div>
                </div>
                <button class="btn-delete" onclick="removeTask('${task.id}')">Sil</button>
            `;
            taskListDiv.appendChild(item);
        });
    }

    setInterval(() => {
        const now = new Date();
        const currentHours = now.getHours().toString().padStart(2, '0');
        const currentMinutes = now.getMinutes().toString().padStart(2, '0');
        const currentTime = `${currentHours}:${currentMinutes}`;

        scheduledTasks.forEach(task => {
            if (task.type === 'time' && task.value === currentTime) {
                if (task.lastPlayedMinute !== currentTime) {
                    task.lastPlayedMinute = currentTime;
                    triggerAnnouncement(task.audioKey);
                }
            }
            else if (task.type === 'range' && Array.isArray(task.value) && task.value.includes(currentTime)) {
                if (task.lastPlayedMinute !== currentTime) {
                    task.lastPlayedMinute = currentTime;
                    triggerAnnouncement(task.audioKey);
                }
            }
        });
    }, 5000);

</script>

</body>
</html>
