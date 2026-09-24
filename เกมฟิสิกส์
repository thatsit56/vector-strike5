<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vector Strike: Ultimate Physics & Math Hub</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome for icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts: Kanit for clean Thai typography -->
    <link href="https://fonts.googleapis.com/css2?family=Kanit:wght@300;400;600;700;800&display=swap" rel="stylesheet">

    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Kanit', 'sans-serif'],
                    },
                    colors: {
                        cyber: {
                            dark: '#0a0e17',
                            card: '#121929',
                            border: '#1e293b',
                            cyan: '#00f0ff',
                            pink: '#ff0055',
                            yellow: '#ffb700',
                            purple: '#7000ff',
                            green: '#00ff66'
                        }
                    }
                }
            }
        }
    </script>

    <style>
        body {
            background-color: #060911;
            color: #f1f5f9;
            font-family: 'Kanit', sans-serif;
            overflow-x: hidden;
            user-select: none;
        }

        /* Custom scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
            height: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #0a0e17;
        }
        ::-webkit-scrollbar-thumb {
            background: #1e293b;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #00f0ff;
        }

        /* Neon glow effects */
        .glow-cyan {
            box-shadow: 0 0 15px rgba(0, 240, 255, 0.4);
        }
        .glow-pink {
            box-shadow: 0 0 15px rgba(255, 0, 85, 0.4);
        }
        .glow-purple {
            box-shadow: 0 0 15px rgba(112, 0, 255, 0.4);
        }
        .text-glow-cyan {
            text-shadow: 0 0 8px rgba(0, 240, 255, 0.6);
        }
        .text-glow-pink {
            text-shadow: 0 0 8px rgba(255, 0, 85, 0.6);
        }

        /* Glassmorphism */
        .glass-panel {
            background: rgba(18, 25, 41, 0.85);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        /* Canvas scaling */
        canvas {
            display: block;
            touch-action: none;
        }

        /* Animation classes */
        .pulse-slow {
            animation: pulse 3s infinite ease-in-out;
        }
        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.6; }
        }
    </style>
</head>
<body class="min-h-screen flex flex-col justify-between relative bg-cyber-dark text-slate-100">

    <!-- TOP NAVBAR -->
    <header class="glass-panel sticky top-0 z-40 px-4 py-3 border-b border-slate-800">
        <div class="max-w-7xl mx-auto flex flex-wrap justify-between items-center gap-4">
            
            <!-- Logo -->
            <div class="flex items-center space-x-3 cursor-pointer" onclick="switchMode('lobby')">
                <div class="w-10 h-10 rounded-xl bg-gradient-to-tr from-cyber-cyan to-cyber-purple flex items-center justify-center text-slate-900 font-extrabold text-xl shadow-lg glow-cyan">
                    <i class="fa-solid font-bold fa-crosshairs text-slate-950"></i>
                </div>
                <div>
                    <h1 class="font-black text-xl tracking-wider text-transparent bg-clip-text bg-gradient-to-r from-cyber-cyan via-white to-cyber-pink">
                        VECTOR STRIKE
                    </h1>
                    <p class="text-xs text-slate-400 font-medium">Ultimate Physics & Math Hub</p>
                </div>
            </div>

            <!-- Profile Badge & Controls -->
            <div class="flex items-center space-x-4">
                <div class="glass-panel px-4 py-1.5 rounded-xl flex items-center gap-3 border border-slate-700">
                    <div class="text-right">
                        <div class="flex items-center justify-end gap-2">
                            <span id="player-title" class="text-xs px-2 py-0.5 rounded-md bg-cyber-purple/40 text-cyber-cyan border border-cyber-cyan/30 font-semibold">นักเรียน</span>
                            <span id="player-name-display" class="font-bold text-sm text-slate-200">Player</span>
                            <button onclick="editPlayerName()" class="text-xs text-slate-400 hover:text-cyber-cyan"><i class="fa-solid fa-pen"></i></button>
                        </div>
                        <div class="flex items-center gap-2 text-xs mt-0.5">
                            <span class="text-cyber-yellow font-bold">Lv.<span id="player-level">1</span></span>
                            <div class="w-24 bg-slate-800 h-2 rounded-full overflow-hidden border border-slate-700">
                                <div id="xp-bar" class="bg-gradient-to-r from-cyber-yellow to-cyber-cyan h-full transition-all duration-300" style="width: 0%"></div>
                            </div>
                            <span class="text-slate-400 text-[10px]"><span id="player-xp">0</span>/<span id="player-max-xp">20</span> XP</span>
                        </div>
                    </div>
                </div>

                <!-- Sound Toggle -->
                <button id="sound-btn" onclick="toggleSound()" class="w-10 h-10 rounded-xl glass-panel flex items-center justify-center hover:border-cyber-cyan text-slate-300 transition-colors">
                    <i class="fa-solid fa-volume-high text-cyber-cyan" id="sound-icon"></i>
                </button>
            </div>
        </div>
    </header>

    <!-- MAIN CONTAINER -->
    <main class="flex-1 max-w-7xl w-full mx-auto p-4 flex flex-col relative justify-center">

        <!-- LOBBY VIEW -->
        <section id="view-lobby" class="space-y-6 animate-fade-in">
            <div class="text-center space-y-2 py-4">
                <h2 class="text-3xl md:text-5xl font-extrabold text-transparent bg-clip-text bg-gradient-to-r from-cyber-cyan via-purple-300 to-cyber-pink">
                    เลือกโหมดการปฏิบัติการ
                </h2>
                <p class="text-slate-400 max-w-xl mx-auto text-sm md:text-base">
                    เรียนรู้ฟิสิกส์และคณิตศาสตร์อย่างสนุกสนานผ่านการยิงขีปนาวุธ การประลองปัญญา และห้องทดลองจำลอง
                </p>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
                
                <!-- Mode 1: Artillery Duel -->
                <div onclick="switchMode('artillery')" class="glass-panel p-6 rounded-2xl border-slate-800 hover:border-cyber-cyan cursor-pointer transition-all hover:-translate-y-2 group flex flex-col justify-between relative overflow-hidden">
                    <div class="absolute -right-6 -bottom-6 text-slate-800/20 group-hover:text-cyber-cyan/10 transition-colors text-9xl font-black">1</div>
                    <div class="space-y-4">
                        <div class="w-12 h-12 rounded-xl bg-cyber-pink/20 text-cyber-pink flex items-center justify-center text-2xl group-hover:scale-110 transition-transform">
                            <i class="fa-solid fa-cannon"></i>
                        </div>
                        <div>
                            <span class="text-xs font-semibold uppercase tracking-wider text-cyber-pink">1v1 Turn-Based</span>
                            <h3 class="text-xl font-bold text-slate-100 mt-1">Artillery Duel</h3>
                            <p class="text-xs text-slate-400 mt-2 leading-relaxed">
                                ดวลยิงปืนใหญ่กับ AI คำนวณองศาและความเร็วด้วยสูตรโพรเจกไทล์ ปรับตามลมและแรงโน้มถ่วง!
                            </p>
                        </div>
                    </div>
                    <div class="mt-6 pt-4 border-t border-slate-800/80 flex justify-between items-center text-xs text-cyber-cyan font-semibold">
                        <span>เริ่มการดวล AI</span>
                        <i class="fa-solid fa-arrow-right group-hover:translate-x-1 transition-transform"></i>
                    </div>
                </div>

                <!-- Mode 2: Quiz Arena -->
                <div onclick="switchMode('quiz')" class="glass-panel p-6 rounded-2xl border-slate-800 hover:border-cyber-yellow cursor-pointer transition-all hover:-translate-y-2 group flex flex-col justify-between relative overflow-hidden">
                    <div class="absolute -right-6 -bottom-6 text-slate-800/20 group-hover:text-cyber-yellow/10 transition-colors text-9xl font-black">2</div>
                    <div class="space-y-4">
                        <div class="w-12 h-12 rounded-xl bg-cyber-yellow/20 text-cyber-yellow flex items-center justify-center text-2xl group-hover:scale-110 transition-transform">
                            <i class="fa-solid fa-brain"></i>
                        </div>
                        <div>
                            <span class="text-xs font-semibold uppercase tracking-wider text-cyber-yellow">30+ คำถามประลอง</span>
                            <h3 class="text-xl font-bold text-slate-100 mt-1">Quiz Arena</h3>
                            <p class="text-xs text-slate-400 mt-2 leading-relaxed">
                                ทดสอบความรู้ฟิสิกส์และเวกเตอร์ ตอบต่อเนื่องไม่มีขัดจังหวะ พร้อมเฉลยละเอียดเมื่อจบเกม!
                            </p>
                        </div>
                    </div>
                    <div class="mt-6 pt-4 border-t border-slate-800/80 flex justify-between items-center text-xs text-cyber-yellow font-semibold">
                        <span>เข้าสู่แบบทดสอบ</span>
                        <i class="fa-solid fa-arrow-right group-hover:translate-x-1 transition-transform"></i>
                    </div>
                </div>

                <!-- Mode 3: Fundamental Revision -->
                <div onclick="switchMode('revision')" class="glass-panel p-6 rounded-2xl border-slate-800 hover:border-cyber-cyan cursor-pointer transition-all hover:-translate-y-2 group flex flex-col justify-between relative overflow-hidden">
                    <div class="absolute -right-6 -bottom-6 text-slate-800/20 group-hover:text-cyber-cyan/10 transition-colors text-9xl font-black">3</div>
                    <div class="space-y-4">
                        <div class="w-12 h-12 rounded-xl bg-cyber-cyan/20 text-cyber-cyan flex items-center justify-center text-2xl group-hover:scale-110 transition-transform">
                            <i class="fa-solid fa-book-bookmark"></i>
                        </div>
                        <div>
                            <span class="text-xs font-semibold uppercase tracking-wider text-cyber-cyan">ทบทวนเนื้อหา</span>
                            <h3 class="text-xl font-bold text-slate-100 mt-1">Fundamental Hub</h3>
                            <p class="text-xs text-slate-400 mt-2 leading-relaxed">
                                รวมการแปลงหน่วย, ความชันกราฟ s-t / v-t, เวกเตอร์, แรง G และความเฉื่อย ครบจบในที่เดียว
                            </p>
                        </div>
                    </div>
                    <div class="mt-6 pt-4 border-t border-slate-800/80 flex justify-between items-center text-xs text-cyber-cyan font-semibold">
                        <span>เปิดคลังความรู้</span>
                        <i class="fa-solid fa-arrow-right group-hover:translate-x-1 transition-transform"></i>
                    </div>
                </div>

                <!-- Mode 4: Sandbox Lab -->
                <div onclick="switchMode('sandbox')" class="glass-panel p-6 rounded-2xl border-slate-800 hover:border-cyber-green cursor-pointer transition-all hover:-translate-y-2 group flex flex-col justify-between relative overflow-hidden">
                    <div class="absolute -right-6 -bottom-6 text-slate-800/20 group-hover:text-cyber-green/10 transition-colors text-9xl font-black">4</div>
                    <div class="space-y-4">
                        <div class="w-12 h-12 rounded-xl bg-cyber-green/20 text-cyber-green flex items-center justify-center text-2xl group-hover:scale-110 transition-transform">
                            <i class="fa-solid fa-flask"></i>
                        </div>
                        <div>
                            <span class="text-xs font-semibold uppercase tracking-wider text-cyber-green">ห้องทดลองอิสระ</span>
                            <h3 class="text-xl font-bold text-slate-100 mt-1">Sandbox Lab</h3>
                            <p class="text-xs text-slate-400 mt-2 leading-relaxed">
                                ปรับแต่ง gravity, แรงลม, ค่าสัมฤทธิ์สะท้อนอิสระ พร้อมมาตรวัดเวกเตอร์สดเรียลไทม์!
                            </p>
                        </div>
                    </div>
                    <div class="mt-6 pt-4 border-t border-slate-800/80 flex justify-between items-center text-xs text-cyber-green font-semibold">
                        <span>เปิด Sandbox</span>
                        <i class="fa-solid fa-arrow-right group-hover:translate-x-1 transition-transform"></i>
                    </div>
                </div>

            </div>
        </section>

        <!-- MODE 1: ARTILLERY DUEL -->
        <section id="view-artillery" class="hidden flex-col gap-4">
            
            <!-- Top Controls Bar -->
            <div class="glass-panel p-3 rounded-2xl flex flex-wrap justify-between items-center gap-3">
                <button onclick="switchMode('lobby')" class="px-3 py-1.5 rounded-lg bg-slate-800 hover:bg-slate-700 text-xs font-semibold flex items-center gap-2">
                    <i class="fa-solid fa-chevron-left"></i> เมนูหลัก
                </button>

                <!-- AI Difficulty Selector -->
                <div class="flex items-center gap-2 text-xs">
                    <span class="text-slate-400 font-medium">ระดับ AI:</span>
                    <select id="ai-difficulty" onchange="changeAIDifficulty()" class="bg-slate-900 border border-slate-700 text-cyber-cyan font-bold rounded-lg px-2 py-1 outline-none focus:border-cyber-cyan">
                        <option value="easy">Easy (+1 XP / -0 XP)</option>
                        <option value="normal" selected>Normal (+3 XP / -1 XP)</option>
                        <option value="hard">Hard (+5 XP / -2 XP)</option>
                        <option value="nightmare">Nightmare (+10 XP / -5 XP)</option>
                        <option value="hell">Hell (+25 XP / -20 XP)</option>
                    </select>
                </div>

                <!-- Match Telemetry Info -->
                <div class="flex items-center gap-4 text-xs">
                    <div class="flex items-center gap-1.5 text-slate-300">
                        <i class="fa-solid fa-earth-americas text-cyber-cyan"></i>
                        <span>g = <b id="match-g" class="text-cyber-cyan">9.8</b> m/s²</span>
                    </div>
                    <div class="flex items-center gap-1.5 text-slate-300">
                        <i class="fa-solid fa-wind text-cyber-yellow"></i>
                        <span>ลม = <b id="match-wind" class="text-cyber-yellow">0.0</b> m/s</span>
                    </div>
                    <button onclick="resetArtilleryMatch()" class="px-2.5 py-1 rounded-lg bg-cyber-pink/20 hover:bg-cyber-pink/30 text-cyber-pink text-xs font-semibold">
                        <i class="fa-solid fa-rotate-right"></i> รีเซ็ตสนาม
                    </button>
                </div>
            </div>

            <!-- Game Canvas Container -->
            <div class="relative w-full rounded-2xl overflow-hidden glass-panel border border-slate-800 h-[480px] md:h-[520px]">
                <canvas id="artilleryCanvas" class="w-full h-full"></canvas>

                <!-- Floating Collapsible Control Dock -->
                <div id="control-dock" class="absolute bottom-3 left-1/2 -translate-x-1/2 w-[95%] max-w-2xl glass-panel p-3 md:p-4 rounded-xl border border-slate-700/80 shadow-2xl transition-all duration-300">
                    <div class="flex justify-between items-center mb-2">
                        <span id="turn-indicator" class="text-xs font-extrabold text-cyber-cyan flex items-center gap-2">
                            <span class="w-2 h-2 rounded-full bg-cyber-cyan animate-ping"></span> ตาของคุณในการยิง!
                        </span>
                        <button onclick="toggleDock()" class="text-xs text-slate-400 hover:text-white px-2 py-0.5 rounded bg-slate-800/80">
                            <i id="dock-toggle-icon" class="fa-solid fa-chevron-down"></i> <span id="dock-toggle-text">ซ่อนแท่นควบคุม</span>
                        </button>
                    </div>

                    <div id="dock-content" class="grid grid-cols-1 sm:grid-cols-3 gap-3 items-center">
                        <div>
                            <label class="block text-[11px] text-slate-400 mb-1">มุมยิง Angle θ (0-90°):</label>
                            <div class="flex items-center gap-2">
                                <input type="number" id="input-angle" min="0" max="90" value="45" class="w-full bg-slate-900 border border-slate-700 rounded-lg px-3 py-1.5 text-cyber-cyan font-bold text-sm focus:outline-none focus:border-cyber-cyan">
                                <span class="text-xs text-slate-400">°</span>
                            </div>
                        </div>

                        <div>
                            <label class="block text-[11px] text-slate-400 mb-1">ความเร็วปลาย Velocity u (m/s):</label>
                            <div class="flex items-center gap-2">
                                <input type="number" id="input-velocity" min="5" max="150" value="65" class="w-full bg-slate-900 border border-slate-700 rounded-lg px-3 py-1.5 text-cyber-yellow font-bold text-sm focus:outline-none focus:border-cyber-yellow">
                                <span class="text-xs text-slate-400">m/s</span>
                            </div>
                        </div>

                        <div class="sm:col-span-1 flex items-end">
                            <button id="fire-btn" onclick="firePlayerArtillery()" class="w-full py-2 bg-gradient-to-r from-cyber-pink to-cyber-purple hover:brightness-125 rounded-lg text-white font-extrabold text-sm shadow-lg glow-pink transition-all">
                                <i class="fa-solid fa-rocket mr-1"></i> ยิงขีปนาวุธ!
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- MODE 2: QUIZ ARENA -->
        <section id="view-quiz" class="hidden flex-col gap-4 max-w-3xl mx-auto w-full">
            <div class="glass-panel p-4 rounded-2xl flex justify-between items-center">
                <button onclick="switchMode('lobby')" class="px-3 py-1.5 rounded-lg bg-slate-800 hover:bg-slate-700 text-xs font-semibold">
                    <i class="fa-solid fa-chevron-left"></i> เมนูหลัก
                </button>
                <div class="text-center">
                    <span class="text-xs text-slate-400 block">แบบทดสอบวิชาฟิสิกส์ & เวกเตอร์</span>
                    <span class="text-sm font-bold text-cyber-yellow">ข้อที่ <span id="quiz-current-idx">1</span> / <span id="quiz-total-idx">10</span></span>
                </div>
                <div class="text-right text-xs">
                    <span class="text-slate-400">คะแนนสะสม:</span>
                    <span id="quiz-live-score" class="font-bold text-cyber-green ml-1">0</span>
                </div>
            </div>

            <!-- Question Card -->
            <div id="quiz-question-box" class="glass-panel p-6 md:p-8 rounded-2xl border border-slate-800 space-y-6 relative overflow-hidden">
                <div class="flex justify-between items-center text-xs">
                    <span id="quiz-difficulty-tag" class="px-2.5 py-1 rounded-full bg-cyber-cyan/20 text-cyber-cyan font-bold uppercase tracking-wider">Easy</span>
                    <span class="text-slate-500"><i class="fa-regular fa-clock mr-1"></i> คลิกคำตอบแล้วระบบจะข้ามไปข้อถัดไปทันที</span>
                </div>

                <h3 id="quiz-question-text" class="text-lg md:text-xl font-bold text-slate-100 leading-relaxed">
                    คำถามจะปรากฏขึ้นตรงนี้...
                </h3>

                <!-- Choices Grid -->
                <div id="quiz-choices-container" class="grid grid-cols-1 gap-3 pt-2">
                    <!-- Dynamic choice buttons inserted via JS -->
                </div>
            </div>

            <!-- Quiz End Summary Modal View (Hidden by default) -->
            <div id="quiz-summary-box" class="hidden glass-panel p-6 md:p-8 rounded-2xl border border-slate-800 space-y-6">
                <div class="text-center space-y-2">
                    <div class="w-16 h-16 rounded-2xl bg-cyber-green/20 text-cyber-green flex items-center justify-center text-3xl mx-auto">
                        <i class="fa-solid fa-trophy"></i>
                    </div>
                    <h3 class="text-2xl font-black text-slate-100">สรุปผลแบบทดสอบ</h3>
                    <p class="text-sm text-slate-400">คุณทำแบบทดสอบเสร็จสิ้นเรียบร้อยแล้ว!</p>
                </div>

                <div class="grid grid-cols-2 gap-4 text-center">
                    <div class="glass-panel p-4 rounded-xl border border-slate-800">
                        <span class="text-xs text-slate-400 block">คะแนนที่ได้</span>
                        <span id="quiz-summary-score" class="text-2xl font-black text-cyber-cyan">0 / 10</span>
                    </div>
                    <div class="glass-panel p-4 rounded-xl border border-slate-800">
                        <span class="text-xs text-slate-400 block">XP ที่ได้รับ</span>
                        <span id="quiz-summary-xp" class="text-2xl font-black text-cyber-yellow">+0 XP</span>
                    </div>
                </div>

                <!-- Comprehensive Review & Explanations -->
                <div class="space-y-4">
                    <h4 class="font-bold text-sm text-slate-300 border-b border-slate-800 pb-2">เฉลยและคำอธิบายสูตรละเอียด:</h4>
                    <div id="quiz-review-list" class="space-y-3 max-h-80 overflow-y-auto pr-2">
                        <!-- Dynamic items generated via JS -->
                    </div>
                </div>

                <div class="flex gap-3 pt-2">
                    <button onclick="startQuizSession()" class="flex-1 py-2.5 rounded-xl bg-cyber-cyan text-slate-900 font-extrabold hover:brightness-110">
                        <i class="fa-solid fa-rotate-right mr-1"></i> ทำอีกครั้ง
                    </button>
                    <button onclick="switchMode('lobby')" class="flex-1 py-2.5 rounded-xl bg-slate-800 text-slate-200 font-bold hover:bg-slate-700">
                        กลับเมนูหลัก
                    </button>
                </div>
            </div>
        </section>

        <!-- MODE 3: FUNDAMENTAL REVISION -->
        <section id="view-revision" class="hidden flex-col gap-6">
            <div class="glass-panel p-4 rounded-2xl flex justify-between items-center">
                <button onclick="switchMode('lobby')" class="px-3 py-1.5 rounded-lg bg-slate-800 hover:bg-slate-700 text-xs font-semibold">
                    <i class="fa-solid fa-chevron-left"></i> เมนูหลัก
                </button>
                <h3 class="text-lg font-bold text-cyber-cyan">Fundamental Physics Revision</h3>
                <div></div>
            </div>

            <!-- Revision Cards Grid -->
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                
                <!-- Card 1: Unit Conversion -->
                <div class="glass-panel p-5 rounded-2xl border border-slate-800 space-y-3">
                    <div class="flex items-center gap-3 text-cyber-cyan">
                        <i class="fa-solid fa-[#00f0ff] fa-arrows-rotate text-xl"></i>
                        <h4 class="font-bold text-base">1. การแปลงหน่วยความเร็ว (km/h ↔ m/s)</h4>
                    </div>
                    <p class="text-xs text-slate-300 leading-relaxed">
                        สูตรทางฟิสิกส์ส่วนใหญ่ใช้หน่วย SI คือเมตรต่อวินาที (m/s) เทคนิคการแปลงหน่วยรวดเร็ว:
                    </p>
                    <div class="bg-slate-900/80 p-3 rounded-xl border border-slate-800 text-xs font-mono space-y-1">
                        <p class="text-cyber-yellow">• จาก km/h เป็น m/s ให้คูณด้วย <b class="text-white">5/18</b> (หรือหาร 3.6)</p>
                        <p class="text-cyber-cyan">• จาก m/s เป็น km/h ให้คูณด้วย <b class="text-white">18/5</b> (หรือคูณ 3.6)</p>
                        <p class="text-slate-400 text-[11px] mt-2">ตัวอย่าง: 90 km/h = 90 × (5/18) = 25 m/s</p>
                    </div>
                </div>

                <!-- Card 2: Graph Slopes -->
                <div class="glass-panel p-5 rounded-2xl border border-slate-800 space-y-3">
                    <div class="flex items-center gap-3 text-cyber-yellow">
                        <i class="fa-solid fa-chart-line text-xl"></i>
                        <h4 class="font-bold text-base">2. ความชันและพื้นที่ใต้กราฟ (s-t / v-t)</h4>
                    </div>
                    <p class="text-xs text-slate-300 leading-relaxed">
                        การตีความกราฟการเคลื่อนที่แนวตรงที่ออกสอบบ่อยที่สุด:
                    </p>
                    <div class="bg-slate-900/80 p-3 rounded-xl border border-slate-800 text-xs font-mono space-y-1">
                        <p class="text-cyber-cyan">• กราฟ s-t (ระยะทาง-เวลา): ความชัน (Slope) = <b class="text-white">ความเร็ว (v)</b></p>
                        <p class="text-cyber-pink">• กราฟ v-t (ความเร็ว-เวลา): ความชัน (Slope) = <b class="text-white">ความเร่ง (a)</b></p>
                        <p class="text-cyber-green">• กราฟ v-t: พื้นที่ใต้กราฟ = <b class="text-white">การกระจัด/ระยะทาง (s)</b></p>
                    </div>
                </div>

                <!-- Card 3: Vectors & Projectile Formulas -->
                <div class="glass-panel p-5 rounded-2xl border border-slate-800 space-y-3">
                    <div class="flex items-center gap-3 text-cyber-pink">
                        <i class="fa-solid fa-vector-square text-xl"></i>
                        <h4 class="font-bold text-base">3. องค์ประกอบเวกเตอร์ & โพรเจกไทล์</h4>
                    </div>
                    <p class="text-xs text-slate-300 leading-relaxed">
                        การแตกแรงความเร็วต้น u ทำมุม θ กับแนวระดับ:
                    </p>
                    <div class="bg-slate-900/80 p-3 rounded-xl border border-slate-800 text-xs font-mono space-y-1">
                        <p class="text-slate-200">• แกน x: uₓ = u cos(θ) &nbsp;|&nbsp; (ความเร็วคงที่, aₓ = 0)</p>
                        <p class="text-slate-200">• แกน y: uᵧ = u sin(θ) &nbsp;|&nbsp; (มีความเร่ง g ดึงลง)</p>
                        <p class="text-cyber-cyan">• ระยะไกลสุด R = (u² sin(2θ)) / g (เมื่อยิงระดับเดียวกัน)</p>
                    </div>
                </div>

                <!-- Card 4: Newton's Laws & G-Force -->
                <div class="glass-panel p-5 rounded-2xl border border-slate-800 space-y-3">
                    <div class="flex items-center gap-3 text-cyber-purple">
                        <i class="fa-solid fa-atom text-xl"></i>
                        <h4 class="font-bold text-base">4. กฎนิวตัน ความเฉื่อย และแรง G</h4>
                    </div>
                    <p class="text-xs text-slate-300 leading-relaxed">
                        ความเข้าใจเรื่องมวล แรง และการต้านทานการเคลื่อนที่:
                    </p>
                    <div class="bg-slate-900/80 p-3 rounded-xl border border-slate-800 text-xs font-mono space-y-1">
                        <p class="text-slate-200">• กฎข้อที่ 1 (ΣF = 0): ความเฉื่อย (Inertia) วัตถุรักษาสภาพนิ่ง/คงที่</p>
                        <p class="text-slate-200">• กฎข้อที่ 2 (ΣF = ma): แรงดึงต้านแรงโน้มถ่วง</p>
                        <p class="text-cyber-yellow">• G-force = ความเร่งที่ได้รับ / g (เช่น 2g = 19.6 m/s²)</p>
                    </div>
                </div>

            </div>
        </section>

        <!-- MODE 4: SANDBOX LAB -->
        <section id="view-sandbox" class="hidden flex-col gap-4">
            <div class="glass-panel p-3 rounded-2xl flex flex-wrap justify-between items-center gap-3">
                <button onclick="switchMode('lobby')" class="px-3 py-1.5 rounded-lg bg-slate-800 hover:bg-slate-700 text-xs font-semibold">
                    <i class="fa-solid fa-chevron-left"></i> เมนูหลัก
                </button>
                <span class="text-xs font-bold text-cyber-green uppercase tracking-widest"><i class="fa-solid fa-flask mr-1"></i> Sandbox Lab (Zero XP Mode)</span>
                <button onclick="clearSandboxCanvas()" class="px-3 py-1 rounded-lg bg-slate-800 hover:bg-slate-700 text-xs font-semibold text-slate-300">
                    <i class="fa-solid fa-trash mr-1"></i> ล้างรอยทาง
                </button>
            </div>

            <div class="grid grid-cols-1 lg:grid-cols-4 gap-4">
                <!-- Interactive Canvas -->
                <div class="lg:col-span-3 glass-panel rounded-2xl overflow-hidden h-[450px] relative">
                    <canvas id="sandboxCanvas" class="w-full h-full cursor-crosshair"></canvas>
                    
                    <!-- Realtime Telemetry HUD Overlay -->
                    <div class="absolute top-3 left-3 glass-panel p-3 rounded-xl border border-slate-800 text-xs font-mono space-y-1">
                        <div class="text-cyber-cyan font-bold mb-1">REALTIME VECTOR TELEMETRY</div>
                        <div>Vx: <span id="sb-tele-vx" class="text-slate-200">0.0</span> m/s</div>
                        <div>Vy: <span id="sb-tele-vy" class="text-slate-200">0.0</span> m/s</div>
                        <div>Hmax (ความสูงสูงสุด): <span id="sb-tele-hmax" class="text-cyber-yellow">0.0</span> m</div>
                        <div>Estimated Range: <span id="sb-tele-range" class="text-cyber-green">0.0</span> m</div>
                    </div>
                </div>

                <!-- Sandbox Parameters Controls -->
                <div class="glass-panel p-4 rounded-2xl border border-slate-800 space-y-4 text-xs">
                    <h4 class="font-bold text-sm text-cyber-green border-b border-slate-800 pb-2">ปรับแต่งพารามิเตอร์</h4>

                    <div>
                        <label class="flex justify-between text-slate-300 mb-1">
                            <span>แรงโน้มถ่วง g (m/s²):</span>
                            <b id="sb-val-g" class="text-cyber-cyan">9.8</b>
                        </label>
                        <input type="range" id="sb-slider-g" min="0" max="30" step="0.5" value="9.8" oninput="updateSandboxParams()" class="w-full accent-cyber-cyan">
                    </div>

                    <div>
                        <label class="flex justify-between text-slate-300 mb-1">
                            <span>แรงลม Wind (m/s):</span>
                            <b id="sb-val-wind" class="text-cyber-yellow">0.0</b>
                        </label>
                        <input type="range" id="sb-slider-wind" min="-15" max="15" step="0.5" value="0" oninput="updateSandboxParams()" class="w-full accent-cyber-yellow">
                    </div>

                    <div>
                        <label class="flex justify-between text-slate-300 mb-1">
                            <span>ความยืดหยุ่น Bounce (e):</span>
                            <b id="sb-val-bounce" class="text-cyber-pink">0.6</b>
                        </label>
                        <input type="range" id="sb-slider-bounce" min="0" max="1" step="0.05" value="0.6" oninput="updateSandboxParams()" class="w-full accent-cyber-pink">
                    </div>

                    <div class="pt-2">
                        <label class="block text-slate-300 mb-1">มุมยิง Launch Angle (°):</label>
                        <input type="number" id="sb-input-angle" value="45" min="0" max="90" class="w-full bg-slate-900 border border-slate-700 rounded-lg px-2.5 py-1.5 text-cyber-cyan font-bold">
                    </div>

                    <div>
                        <label class="block text-slate-300 mb-1">ความเร็วต้น Velocity (m/s):</label>
                        <input type="number" id="sb-input-vel" value="60" min="5" max="150" class="w-full bg-slate-900 border border-slate-700 rounded-lg px-2.5 py-1.5 text-cyber-yellow font-bold">
                    </div>

                    <button onclick="fireSandboxBall()" class="w-full py-2 bg-cyber-green text-slate-950 font-extrabold rounded-lg hover:brightness-110 shadow-lg glow-green mt-2">
                        <i class="fa-solid fa-play mr-1"></i> ยิงวัตถุทดลอง!
                    </button>
                </div>
            </div>
        </section>

    </main>

    <!-- FOOTER -->
    <footer class="glass-panel border-t border-slate-800 py-3 text-center text-xs text-slate-500">
        <p>Vector Strike: Ultimate Physics & Math Hub © 2026 | พัฒนาเพื่อการเรียนรู้วิทยาศาสตร์และคณิตศาสตร์อย่างสร้างสรรค์</p>
    </footer>

    <script>
        /* Web Audio API Sound Generator */
        let audioCtx = null;
        let soundEnabled = true;

        function initAudio() {
            if (!audioCtx) {
                audioCtx = new (window.AudioContext || window.webkitAudioContext)();
            }
        }

        function toggleSound() {
            soundEnabled = !soundEnabled;
            const icon = document.getElementById('sound-icon');
            if (soundEnabled) {
                icon.className = "fa-solid fa-volume-high text-cyber-cyan";
            } else {
                icon.className = "fa-solid fa-volume-xmark text-slate-500";
            }
        }

        function playSound(type) {
            if (!soundEnabled) return;
            initAudio();
            if (!audioCtx) return;

            const osc = audioCtx.createOscillator();
            const gain = audioCtx.createGain();
            osc.connect(gain);
            gain.connect(audioCtx.destination);

            const now = audioCtx.currentTime;

            if (type === 'fire') {
                osc.type = 'sawtooth';
                osc.frequency.setValueAtTime(300, now);
                osc.frequency.exponentialRampToValueAtTime(40, now + 0.3);
                gain.gain.setValueAtTime(0.3, now);
                gain.gain.linearRampToValueAtTime(0.01, now + 0.3);
                osc.start(now);
                osc.stop(now + 0.3);
            } else if (type === 'explode') {
                osc.type = 'square';
                osc.frequency.setValueAtTime(100, now);
                osc.frequency.exponentialRampToValueAtTime(20, now + 0.5);
                gain.gain.setValueAtTime(0.4, now);
                gain.gain.linearRampToValueAtTime(0.01, now + 0.5);
                osc.start(now);
                osc.stop(now + 0.5);
            } else if (type === 'hit') {
                osc.type = 'triangle';
                osc.frequency.setValueAtTime(500, now);
                osc.frequency.exponentialRampToValueAtTime(150, now + 0.15);
                gain.gain.setValueAtTime(0.2, now);
                gain.gain.linearRampToValueAtTime(0.01, now + 0.15);
                osc.start(now);
                osc.stop(now + 0.15);
            } else if (type === 'win') {
                osc.type = 'sine';
                osc.frequency.setValueAtTime(400, now);
                osc.frequency.setValueAtTime(600, now + 0.1);
                osc.frequency.setValueAtTime(800, now + 0.2);
                gain.gain.setValueAtTime(0.2, now);
                gain.gain.linearRampToValueAtTime(0.01, now + 0.4);
                osc.start(now);
                osc.stop(now + 0.4);
            } else if (type === 'click') {
                osc.type = 'sine';
                osc.frequency.setValueAtTime(800, now);
                gain.gain.setValueAtTime(0.05, now);
                gain.gain.linearRampToValueAtTime(0.01, now + 0.05);
                osc.start(now);
                osc.stop(now + 0.05);
            }
        }

        // PLAYER STATE & PROGRESSION
        let player = {
            name: "นักเรียนฟิสิกส์",
            level: 1,
            xp: 0,
            maxXp: 20
        };

        function loadPlayerProfile() {
            const saved = localStorage.getItem('vector_strike_profile');
            if (saved) {
                try {
                    player = JSON.parse(saved);
                } catch(e) {}
            }
            updateProfileUI();
        }

        function savePlayerProfile() {
            localStorage.setItem('vector_strike_profile', JSON.stringify(player));
        }

        function getTitleForLevel(level) {
            if (level <= 3) return "นักเรียน";
            if (level <= 6) return "นักฟิสิกส์";
            if (level <= 8) return "ราชาฟิสิกส์";
            if (level === 9) return "เงามหาเทพฟิสิกส์";
            return "มหาเทพฟิสิกส์";
        }

        function addXP(amount) {
            if (amount <= 0 && player.xp === 0) return;
            player.xp += amount;

            // Handle Level Up
            while (player.xp >= player.maxXp && player.level < 10) {
                player.xp -= player.maxXp;
                player.level++;
                player.maxXp = 20 + (player.level - 1) * 10;
                playSound('win');
            }

            // Cap at Max Level 10
            if (player.level >= 10) {
                player.level = 10;
                player.xp = Math.min(player.xp, player.maxXp);
            }

            if (player.xp < 0) player.xp = 0;

            savePlayerProfile();
            updateProfileUI();
        }

        function updateProfileUI() {
            document.getElementById('player-name-display').innerText = player.name;
            document.getElementById('player-level').innerText = player.level;
            document.getElementById('player-xp').innerText = player.xp;
            document.getElementById('player-max-xp').innerText = player.maxXp;
            document.getElementById('player-title').innerText = getTitleForLevel(player.level);

            const pct = Math.min(100, Math.max(0, (player.xp / player.maxXp) * 100));
            document.getElementById('xp-bar').style.width = pct + '%';
        }

        function editPlayerName() {
            const newName = prompt("กรุณาระบุชื่อของคุณ:", player.name);
            if (newName && newName.trim() !== '') {
                player.name = newName.trim();
                savePlayerProfile();
                updateProfileUI();
            }
        }

        // NAVIGATION
        function switchMode(mode) {
            playSound('click');
            const views = ['lobby', 'artillery', 'quiz', 'revision', 'sandbox'];
            views.forEach(v => {
                const el = document.getElementById(`view-${v}`);
                if (v === mode) {
                    el.classList.remove('hidden');
                    el.classList.add('flex');
                } else {
                    el.classList.add('hidden');
                    el.classList.remove('flex');
                }
            });

            if (mode === 'artillery') {
                initArtilleryGame();
            } else if (mode === 'quiz') {
                startQuizSession();
            } else if (mode === 'sandbox') {
                initSandboxGame();
            }
        }

        // MODE 1: ARTILLERY DUEL ENGINE
        let artCanvas, artCtx;
        let artState = {
            playerHp: 100,
            botHp: 100,
            playerPos: { x: 80, y: 0 },
            botPos: { x: 700, y: 0 },
            g: 9.8,
            wind: 0,
            terrain: [],
            projectiles: [],
            ghostTrajectory: [],
            isPlayerTurn: true,
            isFiring: false,
            difficulty: 'normal'
        };

        const AI_CONFIGS = {
            easy: { name: 'Easy', winXp: 1, loseXp: 0, errorMargin: 12 },
            normal: { name: 'Normal', winXp: 3, loseXp: -1, errorMargin: 6 },
            hard: { name: 'Hard', winXp: 5, loseXp: -2, errorMargin: 2.5 },
            nightmare: { name: 'Nightmare', winXp: 10, loseXp: -5, errorMargin: 0.8 },
            hell: { name: 'Hell', winXp: 25, loseXp: -20, errorMargin: 0.0 }
        };

        function initArtilleryGame() {
            artCanvas = document.getElementById('artilleryCanvas');
            artCtx = artCanvas.getContext('2d');

            // Resize canvas to container
            artCanvas.width = artCanvas.parentElement.clientWidth;
            artCanvas.height = artCanvas.parentElement.clientHeight;

            resetArtilleryMatch();
            requestAnimationFrame(artilleryLoop);
        }

        function resetArtilleryMatch() {
            artState.playerHp = 100;
            artState.botHp = 100;
            artState.g = parseFloat((8.0 + Math.random() * 4.0).toFixed(1));
            artState.wind = parseFloat((-5.0 + Math.random() * 10.0).toFixed(1));
            artState.projectiles = [];
            artState.ghostTrajectory = [];
            artState.isPlayerTurn = true;
            artState.isFiring = false;

            document.getElementById('match-g').innerText = artState.g;
            document.getElementById('match-wind').innerText = artState.wind;
            document.getElementById('turn-indicator').innerHTML = `<span class="w-2 h-2 rounded-full bg-cyber-cyan animate-ping"></span> ตาของคุณในการยิง!`;

            // Generate Terrain
            artState.terrain = [];
            const cols = artCanvas.width;
            let h = artCanvas.height - 120;
            for (let i = 0; i <= cols; i += 10) {
                h += (Math.random() - 0.5) * 8;
                h = Math.max(artCanvas.height - 200, Math.min(artCanvas.height - 50, h));
                artState.terrain.push({ x: i, y: h });
            }

            artState.playerPos = { x: 80, y: getTerrainY(80) - 15 };
            artState.botPos = { x: artCanvas.width - 80, y: getTerrainY(artCanvas.width - 80) - 15 };
        }

        function getTerrainY(x) {
            for (let i = 0; i < artState.terrain.length - 1; i++) {
                if (x >= artState.terrain[i].x && x <= artState.terrain[i+1].x) {
                    return artState.terrain[i].y;
                }
            }
            return artCanvas.height - 80;
        }

        function changeAIDifficulty() {
            artState.difficulty = document.getElementById('ai-difficulty').value;
        }

        function toggleDock() {
            const content = document.getElementById('dock-content');
            const icon = document.getElementById('dock-toggle-icon');
            const txt = document.getElementById('dock-toggle-text');

            if (content.classList.contains('hidden')) {
                content.classList.remove('hidden');
                icon.className = "fa-solid fa-chevron-down";
                txt.innerText = "ซ่อนแท่นควบคุม";
            } else {
                content.classList.add('hidden');
                icon.className = "fa-solid fa-chevron-up";
                txt.innerText = "แสดงแท่นควบคุม";
            }
        }

        function firePlayerArtillery() {
            if (artState.isFiring || !artState.isPlayerTurn) return;

            const angleDeg = parseFloat(document.getElementById('input-angle').value) || 45;
            const velocity = parseFloat(document.getElementById('input-velocity').value) || 65;

            const rad = angleDeg * Math.PI / 180;
            const vx = velocity * Math.cos(rad);
            const vy = -velocity * Math.sin(rad);

            artState.projectiles.push({
                x: artState.playerPos.x,
                y: artState.playerPos.y,
                vx: vx,
                vy: vy,
                isPlayer: true,
                trail: []
            });

            artState.ghostTrajectory = [];
            artState.isFiring = true;
            playSound('fire');
        }

        function triggerAITurn() {
            document.getElementById('turn-indicator').innerHTML = `<span class="w-2 h-2 rounded-full bg-cyber-pink animate-ping"></span> AI กำลังคำนวณเวกเตอร์การยิง...`;

            setTimeout(() => {
                const config = AI_CONFIGS[artState.difficulty];
                const dx = artState.playerPos.x - artState.botPos.x; // negative
                const dy = artState.playerPos.y - artState.botPos.y;

                // Physics perfect angle calculation
                let angleDeg = 135;
                let velocity = 70;

                // Perfect physics trajectory math for 100% Hell AI
                const absDx = Math.abs(dx);
                const g = artState.g;
                // Solve v for 45 deg optimal
                let perfectV = Math.sqrt((g * absDx * absDx) / (absDx - dy));
                if (isNaN(perfectV) || perfectV < 20) perfectV = 65;

                // Apply difficulty error margin offset
                const err = (Math.random() - 0.5) * config.errorMargin * 8;
                velocity = perfectV + err;
                angleDeg = 135 + (Math.random() - 0.5) * config.errorMargin;

                const rad = angleDeg * Math.PI / 180;
                const vx = velocity * Math.cos(rad);
                const vy = -velocity * Math.sin(rad);

                artState.projectiles.push({
                    x: artState.botPos.x,
                    y: artState.botPos.y,
                    vx: vx,
                    vy: vy,
                    isPlayer: false,
                    trail: []
                });

                artState.isFiring = true;
                playSound('fire');
            }, 1000);
        }

        function artilleryLoop() {
            if (!artCtx) return;

            // Clear
            artCtx.fillStyle = '#0a0e17';
            artCtx.fillRect(0, 0, artCanvas.width, artCanvas.height);

            // Draw Sky Grid
            artCtx.strokeStyle = 'rgba(30, 41, 59, 0.4)';
            artCtx.lineWidth = 1;
            for (let x = 0; x < artCanvas.width; x += 40) {
                artCtx.beginPath(); artCtx.moveTo(x, 0); artCtx.lineTo(x, artCanvas.height); artCtx.stroke();
            }
            for (let y = 0; y < artCanvas.height; y += 40) {
                artCtx.beginPath(); artCtx.moveTo(0, y); artCtx.lineTo(artCanvas.width, y); artCtx.stroke();
            }

            // Draw Terrain
            artCtx.fillStyle = '#121929';
            artCtx.strokeStyle = '#00f0ff';
            artCtx.lineWidth = 2;
            artCtx.beginPath();
            artCtx.moveTo(0, artCanvas.height);
            artState.terrain.forEach(pt => artCtx.lineTo(pt.x, pt.y));
            artCtx.lineTo(artCanvas.width, artCanvas.height);
            artCtx.closePath();
            artCtx.fill();
            artCtx.stroke();

            // Draw Player Cannon
            artCtx.fillStyle = '#00f0ff';
            artCtx.fillRect(artState.playerPos.x - 12, artState.playerPos.y - 10, 24, 15);
            // Player HP bar
            artCtx.fillStyle = '#1e293b';
            artCtx.fillRect(artState.playerPos.x - 20, artState.playerPos.y - 25, 40, 6);
            artCtx.fillStyle = '#00ff66';
            artCtx.fillRect(artState.playerPos.x - 20, artState.playerPos.y - 25, (artState.playerHp / 100) * 40, 6);

            // Draw Bot Cannon
            artCtx.fillStyle = '#ff0055';
            artCtx.fillRect(artState.botPos.x - 12, artState.botPos.y - 10, 24, 15);
            // Bot HP bar
            artCtx.fillStyle = '#1e293b';
            artCtx.fillRect(artState.botPos.x - 20, artState.botPos.y - 25, 40, 6);
            artCtx.fillStyle = '#ff0055';
            artCtx.fillRect(artState.botPos.x - 20, artState.botPos.y - 25, (artState.botHp / 100) * 40, 6);

            // Draw Ghost Trajectory Trail
            if (artState.ghostTrajectory.length > 1) {
                artCtx.strokeStyle = 'rgba(0, 240, 255, 0.3)';
                artCtx.setLineDash([4, 4]);
                artCtx.beginPath();
                artCtx.moveTo(artState.ghostTrajectory[0].x, artState.ghostTrajectory[0].y);
                artState.ghostTrajectory.forEach(pt => artCtx.lineTo(pt.x, pt.y));
                artCtx.stroke();
                artCtx.setLineDash([]);
            }

            // Update & Draw Projectiles
            const dt = 0.15;
            for (let i = artState.projectiles.length - 1; i >= 0; i--) {
                const p = artState.projectiles[i];
                p.trail.push({ x: p.x, y: p.y });
                if (p.isPlayer) artState.ghostTrajectory.push({ x: p.x, y: p.y });

                p.vx += artState.wind * 0.05 * dt;
                p.vy += artState.g * dt;

                p.x += p.vx * dt;
                p.y += p.vy * dt;

                // Draw Trail
                artCtx.strokeStyle = p.isPlayer ? '#00f0ff' : '#ff0055';
                artCtx.lineWidth = 2;
                artCtx.beginPath();
                for (let j = 0; j < p.trail.length; j++) {
                    if (j === 0) artCtx.moveTo(p.trail[j].x, p.trail[j].y);
                    else artCtx.lineTo(p.trail[j].x, p.trail[j].y);
                }
                artCtx.stroke();

                // Draw Bullet
                artCtx.fillStyle = '#ffffff';
                artCtx.beginPath();
                artCtx.arc(p.x, p.y, 4, 0, Math.PI * 2);
                artCtx.fill();

                // Check Hit Terrain or Out of Bounds
                const terrainY = getTerrainY(p.x);
                if (p.y >= terrainY || p.x < 0 || p.x > artCanvas.width) {
                    playSound('explode');
                    
                    // Check Hit Targets
                    const distPlayer = Math.hypot(p.x - artState.playerPos.x, p.y - artState.playerPos.y);
                    const distBot = Math.hypot(p.x - artState.botPos.x, p.y - artState.botPos.y);

                    if (distBot < 35) {
                        artState.botHp = Math.max(0, artState.botHp - 35);
                        playSound('hit');
                    }
                    if (distPlayer < 35) {
                        artState.playerHp = Math.max(0, artState.playerHp - 35);
                        playSound('hit');
                    }

                    artState.projectiles.splice(i, 1);
                    artState.isFiring = false;

                    // Check Victory / Defeat
                    const cfg = AI_CONFIGS[artState.difficulty];
                    if (artState.botHp <= 0) {
                        playSound('win');
                        alert(`ยินดีด้วย! คุณเอาชนะ AI (${cfg.name}) รับ +${cfg.winXp} XP`);
                        addXP(cfg.winXp);
                        resetArtilleryMatch();
                    } else if (artState.playerHp <= 0) {
                        playSound('explode');
                        alert(`คุณพ่ายแพ้ต่อ AI (${cfg.name}) หัก ${cfg.loseXp} XP`);
                        addXP(cfg.loseXp);
                        resetArtilleryMatch();
                    } else {
                        // Switch Turn
                        artState.isPlayerTurn = !artState.isPlayerTurn;
                        if (artState.isPlayerTurn) {
                            document.getElementById('turn-indicator').innerHTML = `<span class="w-2 h-2 rounded-full bg-cyber-cyan animate-ping"></span> ตาของคุณในการยิง!`;
                        } else {
                            triggerAITurn();
                        }
                    }
                }
            }

            requestAnimationFrame(artilleryLoop);
        }

        // MODE 2: QUIZ ARENA SYSTEM
        const QUIZ_DATABASE = [
            {
                q: "วัตถุเคลื่อนที่ด้วยความเร็วคงตัว 72 km/h เป็นเวลา 10 วินาที จะได้ระยะทางกี่เมตร?",
                choices: ["200 เมตร", "720 เมตร", "500 เมตร", "100 เมตร"],
                ans: 0,
                diff: "Easy",
                exp: "สูตร s = v × t | แปลงหน่วย 72 km/h = 72 × (5/18) = 20 m/s ดังนั้น s = 20 × 10 = 200 เมตร"
            },
            {
                q: "กราฟระหว่างความเร็วกับเวลา (v-t) ความชัน (Slope) ของกราฟแสดงถึงปริมาณใด?",
                choices: ["ระยะทาง (s)", "ความเร่ง (a)", "การกระจัด (Δx)", "แรง (F)"],
                ans: 1,
                diff: "Easy",
                exp: "ความชันของกราฟ v-t คือ dv/dt ซึ่งเท่ากับ ความเร่ง (a)"
            },
            {
                q: "วัตถุยิงแบบโพรเจกไทล์ทำมุมเท่าใดกับแนวระดับ จึงจะได้ระยะทางตามแนวระดับ (Range) ไกลที่สุด?",
                choices: ["30 องศา", "45 องศา", "60 องศา", "90 องศา"],
                ans: 1,
                diff: "Easy",
                exp: "สูตร R = (u² sin 2θ) / g จะได้ค่าสูงสุดเมื่อ sin(2θ) = 1 ซึ่ง 2θ = 90° นั่นคือ θ = 45°"
            },
            {
                q: "ข้อใดเป็นปริมาณเวกเตอร์ทั้งหมด?",
                choices: ["อัตราเร็ว, ระยะทาง, มวล", "ความเร็ว, การกระจัด, แรง", "พลังงาน, ความเร็ว, เวลา", "งาน, แรง, อุณหภูมิ"],
                ans: 1,
                diff: "Easy",
                exp: "ปริมาณเวกเตอร์ต้องมีทั้งขนาดและทิศทาง ได้แก่ ความเร็ว การกระจัด และแรง"
            },
            {
                q: "ปล่อยวัตถุตกแบบเสรีใต้แรงโน้มถ่วง g = 9.8 m/s² เมื่อเวลาผ่านไป 3 วินาที วัตถุมีความเร็วกี่ m/s?",
                choices: ["9.8 m/s", "19.6 m/s", "29.4 m/s", "44.1 m/s"],
                ans: 2,
                diff: "Medium",
                exp: "สูตร v = u + gt | u = 0 ดังนั้น v = 0 + (9.8 × 3) = 29.4 m/s"
            },
            {
                q: "แรง 3 N และ 4 N กระทำต่อวัตถุชิ้นเดียวกันทำมุม 90 องศาต่อกัน ขนาดของแรงลัพธ์คือเท่าใด?",
                choices: ["1 N", "5 N", "7 N", "12 N"],
                ans: 1,
                diff: "Medium",
                exp: "ตามทฤษฎีบทพีทาโกรัส R = √(3² + 4²) = √(9 + 16) = √25 = 5 N"
            },
            {
                q: "พื้นที่ใต้กราฟระหว่างความเร็วกับเวลา (v-t) มีค่าเท่ากับปริมาณใด?",
                choices: ["ความเร่ง", "การกระจัด/ระยะทาง", "ความเฉื่อย", "กำลัง"],
                ans: 1,
                diff: "Easy",
                exp: "พื้นที่ใต้กราฟ v-t คือการอินทิเกรต v dt ซึ่งเท่ากับ การกระจัดหรือระยะทาง"
            },
            {
                q: "นักบินอวกาศเจอแรง G ขนาด 3g ขณะยานเร่งขึ้นสู่อวกาศ หมายความว่าอย่างไร?",
                choices: ["น้ำหนักปรากฏเพิ่มขึ้นเป็น 3 เท่าของปกติ", "มวลเพิ่มขึ้นเป็น 3 เท่า", "ความเร็วเป็น 3 m/s", "ไม่มีแรงโน้มถ่วง"],
                ans: 0,
                diff: "Medium",
                exp: "แรง 3g หมายถึงความเร่ง 3 เท่าของแรงโน้มถ่วงโลก ทำให้น้ำหนักปรากฏเพิ่มขึ้นเป็น 3 เท่า"
            },
            {
                q: "เวกเตอร์ A มีขนาด 10 หน่วย ทำมุม 60° กับแกน X ขนาดขององค์ประกอบแนวแกน X (Ax) คือเท่าใด?",
                choices: ["5 หน่วย", "8.66 หน่วย", "10 หน่วย", "0 หน่วย"],
                ans: 0,
                diff: "Hard",
                exp: "Ax = A cos(60°) = 10 × 0.5 = 5 หน่วย"
            },
            {
                q: "กฎข้อที่ 1 ของนิวตัน (ΣF = 0) อธิบายถึงคุณสมบัติใดของวัตถุ?",
                choices: ["ความเร่ง", "ความเฉื่อย (Inertia)", "แรงปฏิกิริยา", "โมเมนตัม"],
                ans: 1,
                diff: "Easy",
                exp: "กฎข้อที่ 1 ของนิวตันเรียกอีกอย่างว่า กฎแห่งความเฉื่อย วัตถุจะรักษา狀態เดิมถ้าไม่มีแรงลัพธ์มากระทำ"
            }
        ];

        let quizState = {
            currentIdx: 0,
            score: 0,
            answers: []
        };

        function startQuizSession() {
            quizState.currentIdx = 0;
            quizState.score = 0;
            quizState.answers = [];

            document.getElementById('quiz-summary-box').classList.add('hidden');
            document.getElementById('quiz-question-box').classList.remove('hidden');

            renderQuizQuestion();
        }

        function renderQuizQuestion() {
            const total = QUIZ_DATABASE.length;
            const item = QUIZ_DATABASE[quizState.currentIdx];

            document.getElementById('quiz-current-idx').innerText = quizState.currentIdx + 1;
            document.getElementById('quiz-total-idx').innerText = total;
            document.getElementById('quiz-live-score').innerText = quizState.score;

            document.getElementById('quiz-difficulty-tag').innerText = item.diff;
            document.getElementById('quiz-question-text').innerText = item.q;

            const container = document.getElementById('quiz-choices-container');
            container.innerHTML = '';

            item.choices.forEach((c, idx) => {
                const btn = document.createElement('button');
                btn.className = "w-full p-4 rounded-xl glass-panel border border-slate-800 hover:border-cyber-cyan text-left text-sm font-semibold text-slate-200 transition-all flex items-center justify-between group";
                btn.innerHTML = `
                    <span>${c}</span>
                    <i class="fa-solid fa-chevron-right text-slate-600 group-hover:text-cyber-cyan transition-colors"></i>
                `;
                btn.onclick = () => selectQuizAnswer(idx);
                container.appendChild(btn);
            });
        }

        function selectQuizAnswer(choiceIdx) {
            playSound('click');
            const item = QUIZ_DATABASE[quizState.currentIdx];
            const isCorrect = (choiceIdx === item.ans);

            if (isCorrect) quizState.score++;

            quizState.answers.push({
                question: item.q,
                selected: choiceIdx,
                selectedText: item.choices[choiceIdx],
                correctText: item.choices[item.ans],
                isCorrect: isCorrect,
                exp: item.exp
            });

            quizState.currentIdx++;

            // INSTANT ADVANCE to next question or show summary
            if (quizState.currentIdx < QUIZ_DATABASE.length) {
                renderQuizQuestion();
            } else {
                finishQuizSession();
            }
        }

        function finishQuizSession() {
            document.getElementById('quiz-question-box').classList.add('hidden');
            document.getElementById('quiz-summary-box').classList.remove('hidden');

            const total = QUIZ_DATABASE.length;
            const xpEarned = quizState.score * 3;

            document.getElementById('quiz-summary-score').innerText = `${quizState.score} / ${total}`;
            document.getElementById('quiz-summary-xp').innerText = `+${xpEarned} XP`;

            addXP(xpEarned);

            // Build detailed review list
            const reviewList = document.getElementById('quiz-review-list');
            reviewList.innerHTML = '';

            quizState.answers.forEach((ans, idx) => {
                const div = document.createElement('div');
                div.className = `p-3 rounded-xl border text-xs space-y-1 ${ans.isCorrect ? 'bg-cyber-green/10 border-cyber-green/30' : 'bg-cyber-pink/10 border-cyber-pink/30'}`;
                
                div.innerHTML = `
                    <div class="flex justify-between font-bold">
                        <span class="text-slate-200">ข้อที่ ${idx + 1}: ${ans.question}</span>
                        <span class="${ans.isCorrect ? 'text-cyber-green' : 'text-cyber-pink'}">${ans.isCorrect ? '✓ ถูกต้อง' : '✗ ผิด'}</span>
                    </div>
                    <div class="text-slate-400">คำตอบของคุณ: <b class="${ans.isCorrect ? 'text-cyber-green' : 'text-cyber-pink'}">${ans.selectedText}</b></div>
                    ${!ans.isCorrect ? `<div class="text-cyber-cyan">คำตอบที่ถูกต้อง: <b>${ans.correctText}</b></div>` : ''}
                    <div class="text-slate-300 font-mono text-[11px] mt-1 pt-1 border-t border-slate-800">💡 คำอธิบาย: ${ans.exp}</div>
                `;
                reviewList.appendChild(div);
            });
        }

        // MODE 4: SANDBOX LAB ENGINE
        let sbCanvas, sbCtx;
        let sbState = {
            g: 9.8,
            wind: 0,
            bounce: 0.6,
            balls: []
        };

        function initSandboxGame() {
            sbCanvas = document.getElementById('sandboxCanvas');
            sbCtx = sbCanvas.getContext('2d');

            sbCanvas.width = sbCanvas.parentElement.clientWidth;
            sbCanvas.height = sbCanvas.parentElement.clientHeight;

            requestAnimationFrame(sandboxLoop);
        }

        function updateSandboxParams() {
            sbState.g = parseFloat(document.getElementById('sb-slider-g').value);
            sbState.wind = parseFloat(document.getElementById('sb-slider-wind').value);
            sbState.bounce = parseFloat(document.getElementById('sb-slider-bounce').value);

            document.getElementById('sb-val-g').innerText = sbState.g;
            document.getElementById('sb-val-wind').innerText = sbState.wind;
            document.getElementById('sb-val-bounce').innerText = sbState.bounce;
        }

        function fireSandboxBall() {
            const angle = parseFloat(document.getElementById('sb-input-angle').value) || 45;
            const vel = parseFloat(document.getElementById('sb-input-vel').value) || 60;

            const rad = angle * Math.PI / 180;
            const vx = vel * Math.cos(rad);
            const vy = -vel * Math.sin(rad);

            sbState.balls.push({
                x: 50,
                y: sbCanvas.height - 40,
                vx: vx,
                vy: vy,
                trail: [],
                color: '#00f0ff'
            });

            // Update telemetry UI estimates
            document.getElementById('sb-tele-vx').innerText = vx.toFixed(1);
            document.getElementById('sb-tele-vy').innerText = Math.abs(vy).toFixed(1);
            
            const hmax = (vy * vy) / (2 * sbState.g);
            document.getElementById('sb-tele-hmax').innerText = isNaN(hmax) ? "0.0" : Math.abs(hmax).toFixed(1);

            const estRange = (vel * vel * Math.sin(2 * rad)) / sbState.g;
            document.getElementById('sb-tele-range').innerText = isNaN(estRange) ? "0.0" : Math.abs(estRange).toFixed(1);

            playSound('fire');
        }

        function clearSandboxCanvas() {
            sbState.balls = [];
        }

        function sandboxLoop() {
            if (!sbCtx) return;

            sbCtx.fillStyle = '#0a0e17';
            sbCtx.fillRect(0, 0, sbCanvas.width, sbCanvas.height);

            // Ground
            sbCtx.fillStyle = '#1e293b';
            sbCtx.fillRect(0, sbCanvas.height - 30, sbCanvas.width, 30);

            const dt = 0.15;

            sbState.balls.forEach(b => {
                b.trail.push({ x: b.x, y: b.y });

                b.vx += sbState.wind * 0.05 * dt;
                b.vy += sbState.g * dt;

                b.x += b.vx * dt;
                b.y += b.vy * dt;

                // Bounce ground
                if (b.y >= sbCanvas.height - 35) {
                    b.y = sbCanvas.height - 35;
                    b.vy = -b.vy * sbState.bounce;
                    b.vx *= sbState.bounce;
                }

                // Draw Trail
                sbCtx.strokeStyle = 'rgba(0, 240, 255, 0.4)';
                sbCtx.lineWidth = 2;
                sbCtx.beginPath();
                b.trail.forEach((pt, idx) => {
                    if (idx === 0) sbCtx.moveTo(pt.x, pt.y);
                    else sbCtx.lineTo(pt.x, pt.y);
                });
                sbCtx.stroke();

                // Draw Ball
                sbCtx.fillStyle = b.color;
                sbCtx.beginPath();
                sbCtx.arc(b.x, b.y, 6, 0, Math.PI * 2);
                sbCtx.fill();
            });

            requestAnimationFrame(sandboxLoop);
        }

        // INITIALIZATION
        window.onload = function() {
            loadPlayerProfile();
        };
    </script>
</body>
</html>
