<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>煙火攝影焦距與風向助手</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
    <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
    <style>
        #map { height: 500px; width: 100%; border-radius: 12px; }
        .glass-morphism {
            background: rgba(255, 255, 255, 0.9);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }
    </style>
</head>
<body class="bg-slate-900 text-slate-800 min-h-screen p-4 md:p-8 relative">

    <div class="max-w-7xl mx-auto grid grid-cols-1 lg:grid-cols-3 gap-8">
        
        <!-- 左側控制面板 -->
        <div class="lg:col-span-1 space-y-6">
            <div class="glass-morphism p-6 rounded-2xl shadow-xl">
                <h1 class="text-2xl font-bold mb-4 flex items-center gap-2">
                    <span class="text-orange-500">🎆</span> 煙火攝影計算機
                </h1>
                
                <div class="space-y-4">
                    <div class="grid grid-cols-2 gap-4">
                        <div>
                            <label class="block text-sm font-medium text-slate-600">最大吋數</label>
                            <input type="number" id="fwInch" value="12" class="w-full p-2 border rounded-lg focus:ring-2 focus:ring-orange-500 outline-none">
                        </div>
                        <div>
                            <label class="block text-sm font-medium text-slate-600">發射點數量</label>
                            <input type="number" id="fwPoints" value="3" min="1" class="w-full p-2 border rounded-lg focus:ring-2 focus:ring-orange-500 outline-none">
                        </div>
                    </div>

                    <div class="grid grid-cols-2 gap-4">
                        <div>
                            <label class="block text-sm font-medium text-slate-600">砲陣地總寬度 (m)</label>
                            <input type="number" id="fwWidth" value="100" class="w-full p-2 border rounded-lg focus:ring-2 focus:ring-orange-500 outline-none">
                        </div>
                        <div>
                            <label class="block text-sm font-medium text-slate-600">拍攝點高低差 (m)</label>
                            <input type="number" id="elevationDiff" value="0" class="w-full p-2 border rounded-lg focus:ring-2 focus:ring-orange-500 outline-none" title="正數表示您在高處，負數表示您在低處">
                            <p class="text-[10px] text-slate-400 mt-1 leading-tight">正數:山上往下 / 負數:谷底往上</p>
                        </div>
                    </div>

                    <div>
                        <label class="block text-sm font-medium text-slate-600">安全預留邊界 (%)</label>
                        <input type="range" id="safetyMargin" min="0" max="50" value="20" class="w-full h-2 bg-slate-200 rounded-lg appearance-none cursor-pointer">
                        <div class="flex justify-between text-xs text-slate-500">
                            <span>0% (極限)</span>
                            <span id="marginVal">20%</span>
                        </div>
                    </div>

                    <div>
                        <label class="block text-sm font-medium text-slate-600">預留地景佔比 (%)</label>
                        <input type="range" id="landscapeMargin" min="0" max="50" value="25" class="w-full h-2 bg-slate-200 rounded-lg appearance-none cursor-pointer">
                        <div class="flex justify-between text-xs text-slate-500">
                            <span>0% (純天空)</span>
                            <span id="landscapeVal">25% (1/4 畫面)</span>
                        </div>
                    </div>

                    <div class="pt-4 border-t border-slate-200">
                        <div class="flex justify-between items-center mb-2">
                            <span class="text-sm font-bold text-slate-700">計算結果 (全片幅)</span>
                            <span class="px-2 py-1 bg-orange-100 text-orange-600 rounded text-xs">建議焦距</span>
                        </div>
                        <div class="grid grid-cols-2 gap-4 text-center">
                            <div class="p-3 bg-slate-50 rounded-xl">
                                <span class="block text-xs text-slate-500">橫幅建議</span>
                                <span id="focalHorizontal" class="text-2xl font-black text-orange-600">-- mm</span>
                            </div>
                            <div class="p-3 bg-slate-50 rounded-xl">
                                <span class="block text-xs text-slate-500">直幅建議</span>
                                <span id="focalVertical" class="text-2xl font-black text-orange-600">-- mm</span>
                            </div>
                        </div>
                        <button onclick="openAR()" class="mt-4 w-full bg-emerald-500 hover:bg-emerald-600 text-white font-bold py-3 rounded-xl transition shadow-lg flex items-center justify-center gap-2">
                            📷 開啟相機取景模擬
                        </button>
                    </div>
                </div>
            </div>

            <!-- 自動存檔與手動備份 -->
            <div class="glass-morphism p-6 rounded-2xl shadow-xl">
                <h2 class="text-xl font-bold mb-4 flex items-center gap-2">
                    <span class="text-emerald-500">💾</span> 設定存檔與備份
                </h2>
                <div class="space-y-3">
                    <!-- 自動存檔提示 -->
                    <div class="p-3 bg-emerald-50 border border-emerald-200 rounded-lg text-sm text-emerald-800 flex items-start gap-2">
                        <span class="text-lg">✨</span>
                        <p>系統會<strong>自動儲存</strong>您的設定與地圖機位。下次打開此網頁時將自動讀取，無需手動載入！</p>
                    </div>

                    <div class="flex flex-col gap-2 pt-3 border-t border-slate-200">
                        <span class="text-xs font-bold text-slate-500">手動備份 / 分享機位給朋友 (JSON)</span>
                        <input type="text" id="configName" placeholder="輸入專案名稱 (例: 101跨年)" class="w-full p-2 border rounded-lg focus:ring-2 focus:ring-emerald-500 outline-none text-sm text-slate-800">
                        <div class="flex gap-2">
                            <button onclick="window.exportConfig()" class="flex-1 bg-slate-600 hover:bg-slate-700 text-white px-4 py-2 rounded-lg text-sm font-bold shadow transition flex items-center justify-center gap-1">
                                <span>📥</span> 匯出
                            </button>
                            <label class="flex-1 bg-blue-500 hover:bg-blue-600 text-white px-4 py-2 rounded-lg text-sm font-bold shadow transition cursor-pointer flex items-center justify-center gap-1">
                                <span>📤</span> 匯入
                                <input type="file" id="importFile" accept=".json" class="hidden" onchange="window.importConfig(event)">
                            </label>
                        </div>
                        <span id="saveMsg" class="text-xs h-4 font-bold text-center block mt-1"></span>
                    </div>
                </div>
            </div>

            <!-- 風向資訊 -->
            <div class="glass-morphism p-6 rounded-2xl shadow-xl">
                <h2 class="text-xl font-bold mb-4 flex items-center gap-2">
                    <span class="text-blue-500">🌬️</span> 風向與氣象預測
                </h2>
                <div id="weatherStatus" class="text-sm text-slate-500 mb-4 italic">請在地圖上點擊以獲取氣象資料...</div>
                <div id="windForecast" class="space-y-3">
                    <!-- 風向清單 -->
                </div>
            </div>
        </div>

        <!-- 右側地圖區域 -->
        <div class="lg:col-span-2 space-y-4">
            <div class="glass-morphism p-4 rounded-2xl shadow-xl">
                <div class="flex flex-wrap gap-4 mb-3 items-center justify-between">
                    <div class="flex gap-2 text-sm">
                        <span class="flex items-center gap-1"><span class="w-3 h-3 bg-red-500 rounded-full"></span> 砲陣地</span>
                        <span class="flex items-center gap-1"><span class="w-3 h-3 bg-blue-500 rounded-full"></span> 拍攝點</span>
                    </div>
                    <div class="flex items-center gap-4">
                        <div id="distanceDisplay" class="font-bold text-lg text-blue-600">距離: -- 公尺</div>
                        <div id="angleDisplay" class="font-bold text-lg text-emerald-600 hidden">夾角: --°</div>
                    </div>
                    <button onclick="resetMap()" class="text-sm bg-slate-200 hover:bg-slate-300 px-3 py-1 rounded-md transition">重設位置</button>
                </div>
                
                <div class="relative">
                    <div id="map"></div>
                    
                    <!-- 地圖浮動控制：旋轉觀賞面 -->
                    <div id="angleControlBox" class="hidden absolute bottom-6 left-1/2 transform -translate-x-1/2 z-[1000] w-11/12 max-w-sm bg-white/95 backdrop-blur px-5 py-3 rounded-2xl shadow-[0_4px_20px_rgba(0,0,0,0.2)] border border-slate-200 transition-all">
                        <label class="block text-sm font-bold text-slate-700 mb-2 text-center flex items-center justify-center gap-2">
                            <span>🔄 旋轉觀賞面</span>
                            <span id="siteAngleVal" class="text-orange-600 text-lg">90°</span>
                        </label>
                        <input type="range" id="siteAngle" min="0" max="180" value="90" class="w-full h-2 bg-slate-200 rounded-lg appearance-none cursor-pointer focus:outline-none focus:ring-2 focus:ring-orange-500">
                        <div class="flex justify-between text-xs text-slate-500 mt-2 font-medium">
                            <span>0° (南北)</span>
                            <span>180°</span>
                        </div>
                    </div>
                </div>

                <div class="mt-4 grid grid-cols-1 md:grid-cols-3 gap-4">
                    <div class="bg-white/50 p-3 rounded-lg border">
                        <span class="block text-xs text-slate-500">爆炸直徑預估</span>
                        <span id="estDia" class="font-bold text-slate-700">-- m</span>
                    </div>
                    <div class="bg-white/50 p-3 rounded-lg border">
                        <span class="block text-xs text-slate-500">升空高度預估</span>
                        <span id="estAlt" class="font-bold text-slate-700">-- m</span>
                    </div>
                    <div class="bg-white/50 p-3 rounded-lg border">
                        <span class="block text-xs text-slate-500">建議取景高度</span>
                        <span id="estSceneHeight" class="font-bold text-slate-700">-- m</span>
                    </div>
                </div>
            </div>
        </div>

    </div>

    <!-- AR 相機取景模擬 Modal -->
    <div id="arModal" class="hidden fixed inset-0 z-[2000] bg-black">
        <video id="arVideo" autoplay playsinline class="absolute inset-0 w-full h-full object-cover"></video>
        <canvas id="arCanvas" class="absolute inset-0 w-full h-full z-10"></canvas>
        
        <!-- AR 控制面板 (改為雙層結構，加入參數調整) -->
        <div class="absolute top-0 left-0 right-0 p-3 flex flex-col gap-2 z-20 bg-gradient-to-b from-black/80 via-black/50 to-transparent pb-10 pointer-events-none">
            <!-- 頂部按鈕與標題 -->
            <div class="flex justify-between items-start text-white pointer-events-auto">
                <span class="font-bold text-sm md:text-base drop-shadow-md">📷 比例草圖模擬</span>
                <div class="flex gap-2">
                    <button onclick="toggleFullscreen()" class="bg-blue-500 hover:bg-blue-600 px-3 py-1 rounded font-bold text-sm shadow-lg transition">⛶ 全螢幕</button>
                    <button onclick="closeAR()" class="bg-red-500 hover:bg-red-600 px-3 py-1 rounded font-bold text-sm shadow-lg transition">關閉 X</button>
                </div>
            </div>
            
            <!-- 參數微調列 -->
            <div class="flex flex-wrap items-center gap-2 pointer-events-auto">
                <select id="arOrientation" onchange="drawARSketch()" class="p-1 text-black rounded text-xs outline-none shadow-md">
                    <option value="auto">自動方向</option>
                    <option value="portrait">強制直幅</option>
                    <option value="landscape">強制橫幅</option>
                </select>
                
                <div class="bg-black/60 px-2 py-1 rounded backdrop-blur border border-white/20 flex items-center gap-1 shadow-md">
                    <label class="text-white text-[10px] whitespace-nowrap">焦距:</label>
                    <input type="number" id="arFocalLength" value="23" oninput="drawARSketch()" class="w-10 p-0.5 text-black text-center rounded text-xs outline-none" title="相機等效焦距">
                    <span class="text-white text-[10px]">mm</span>
                </div>

                <div class="bg-emerald-900/60 px-2 py-1 rounded backdrop-blur border border-emerald-500/50 flex items-center gap-1 shadow-md">
                    <label class="text-emerald-100 text-[10px] whitespace-nowrap">最大吋數:</label>
                    <input type="number" id="arFwInch" oninput="syncFromAR()" class="w-10 p-0.5 text-black text-center rounded text-xs outline-none">
                </div>

                <div class="bg-emerald-900/60 px-2 py-1 rounded backdrop-blur border border-emerald-500/50 flex items-center gap-1 shadow-md">
                    <label class="text-emerald-100 text-[10px] whitespace-nowrap">陣地寬:</label>
                    <input type="number" id="arFwWidth" oninput="syncFromAR()" class="w-12 p-0.5 text-black text-center rounded text-xs outline-none">
                    <span class="text-emerald-100 text-[10px]">m</span>
                </div>

                <div class="bg-emerald-900/60 px-2 py-1 rounded backdrop-blur border border-emerald-500/50 flex items-center gap-1 shadow-md">
                    <label class="text-emerald-100 text-[10px] whitespace-nowrap">發射點:</label>
                    <input type="number" id="arFwPoints" oninput="syncFromAR()" class="w-10 p-0.5 text-black text-center rounded text-xs outline-none">
                </div>
            </div>
        </div>

        <div id="arWarning" class="absolute inset-0 flex items-center justify-center pointer-events-none hidden z-30">
            <div class="text-white/90 text-sm bg-black/80 p-5 rounded-xl text-center max-w-xs backdrop-blur-sm border border-white/20 pointer-events-auto shadow-2xl">
                <p class="font-bold text-red-400 mb-2 text-lg">⚠️ 無法存取相機</p>
                <p>如果您不小心拒絕了權限，請手動<span class="text-emerald-400 font-bold">允許相機權限</span>後，重新整理網頁。</p>
                <p class="mt-2 text-white/50 text-xs">目前僅能顯示黑色背景的模擬草圖。</p>
            </div>
        </div>
    </div>

    <script>
        var map;
        var fireworkPos = null;
        var cameraPos = null;
        var markers = [];
        var polyline = null;
        var windArrow = null;
        var siteLineGroup = null;
        var isAutoLoading = false; // 防止讀取時觸發自動儲存

        // 初始化地圖與自動讀取
        window.onload = function() {
            map = L.map('map').setView([25.0339, 121.5644], 15);
            
            const googleStreets = L.tileLayer('https://mt1.google.com/vt/lyrs=m&x={x}&y={y}&z={z}', {
                maxZoom: 20,
                attribution: '&copy; Google'
            });

            const googleHybrid = L.tileLayer('https://mt1.google.com/vt/lyrs=y&x={x}&y={y}&z={z}', {
                maxZoom: 20,
                attribution: '&copy; Google'
            });

            googleStreets.addTo(map);

            L.control.layers({
                "Google 一般地圖": googleStreets,
                "Google 衛星地圖": googleHybrid
            }).addTo(map);

            map.on('click', onMapClick);

            // 監聽所有主選單輸入並觸發計算與自動儲存
            document.querySelectorAll('input:not([id^="ar"]').forEach(input => {
                input.addEventListener('input', calculate);
            });

            // 啟動時自動讀取本地存檔
            autoLoadLocal();
        };

        function onMapClick(e) {
            if (!fireworkPos) {
                fireworkPos = e.latlng;
                addMarker(fireworkPos, 'firework', '砲陣地');
                document.getElementById('angleControlBox').classList.remove('hidden');
                calculate();
            } else if (!cameraPos) {
                cameraPos = e.latlng;
                addMarker(cameraPos, 'camera', '拍攝點');
                updateDistance();
                fetchWeather(fireworkPos.lat, fireworkPos.lng);
            }
        }

        function addMarker(latlng, type, label) {
            const color = type === 'firework' ? '#ef4444' : '#3b82f6';
            const marker = L.circleMarker(latlng, {
                radius: 10,
                fillColor: color,
                color: '#fff',
                weight: 2,
                fillOpacity: 1
            }).addTo(map).bindPopup(label).openPopup();
            markers.push(marker);
        }

        function updateDistance() {
            if (fireworkPos && cameraPos) {
                const dist = fireworkPos.distanceTo(cameraPos);
                document.getElementById('distanceDisplay').innerText = `距離: ${Math.round(dist)} 公尺`;
                
                if (polyline) map.removeLayer(polyline);
                polyline = L.polyline([fireworkPos, cameraPos], {color: 'blue', dashArray: '5, 10'}).addTo(map);
                
                calculate();
            }
        }

        function resetMap() {
            markers.forEach(m => map.removeLayer(m));
            if (polyline) map.removeLayer(polyline);
            if (windArrow) map.removeLayer(windArrow);
            if (siteLineGroup) map.removeLayer(siteLineGroup);
            markers = [];
            polyline = null;
            fireworkPos = null;
            cameraPos = null;
            document.getElementById('distanceDisplay').innerText = `距離: -- 公尺`;
            document.getElementById('angleDisplay').classList.add('hidden');
            document.getElementById('focalHorizontal').innerText = `-- mm`;
            document.getElementById('focalVertical').innerText = `-- mm`;
            document.getElementById('windForecast').innerHTML = '';
            document.getElementById('weatherStatus').innerText = '請在地圖上點擊以獲取氣象資料...';
            document.getElementById('angleControlBox').classList.add('hidden');
            
            // 重置後自動儲存空狀態
            autoSaveLocal();
        }

        function calculate() {
            const inch = parseFloat(document.getElementById('fwInch').value) || 0;
            const arrayWidth = parseFloat(document.getElementById('fwWidth').value) || 0;
            const siteAngle = parseFloat(document.getElementById('siteAngle').value) || 0;
            const elevationDiff = parseFloat(document.getElementById('elevationDiff').value) || 0;
            
            document.getElementById('siteAngleVal').innerText = `${siteAngle}°`;

            const safety = 1 + (parseFloat(document.getElementById('safetyMargin').value) / 100);
            document.getElementById('marginVal').innerText = `${Math.round((safety-1)*100)}%`;
            
            const landscapePct = parseFloat(document.getElementById('landscapeMargin').value) || 0;
            document.getElementById('landscapeVal').innerText = `${landscapePct}%`;

            const burstDia = inch * 28;
            const altitude = inch * 32;
            const totalHeight = altitude + (burstDia / 2);
            const totalWidth = arrayWidth + burstDia;

            const landscapeRatio = landscapePct / 100;
            const virtualTotalHeight = totalHeight / (1 - landscapeRatio);

            document.getElementById('estDia').innerText = `${Math.round(burstDia)} m`;
            document.getElementById('estAlt').innerText = `${Math.round(altitude)} m`;
            document.getElementById('estSceneHeight').innerText = `${Math.round(totalHeight)} m`;

            if (fireworkPos && cameraPos) {
                const distance = fireworkPos.distanceTo(cameraPos);
                const slantDistance = Math.sqrt(distance * distance + elevationDiff * elevationDiff);
                
                const fH_w = (36 * slantDistance) / (totalWidth * safety);
                const fH_h = (24 * slantDistance) / (virtualTotalHeight * safety);
                const suggestH = Math.min(fH_w, fH_h);

                const fV_w = (24 * slantDistance) / (totalWidth * safety);
                const fV_h = (36 * slantDistance) / (virtualTotalHeight * safety);
                const suggestV = Math.min(fV_w, fV_h);

                document.getElementById('focalHorizontal').innerText = `${Math.floor(suggestH)} mm`;
                document.getElementById('focalVertical').innerText = `${Math.floor(suggestV)} mm`;

                const bearing = getBearing(fireworkPos, cameraPos);
                let diff = Math.abs(bearing - siteAngle) % 180;
                if (diff > 90) diff = 180 - diff;
                const viewAngle = Math.round(diff);
                
                let angleHint = "";
                if(viewAngle >= 75) angleHint = "(正面)";
                else if(viewAngle <= 15) angleHint = "(側面)";
                else angleHint = "(斜角)";
                
                const angleEl = document.getElementById('angleDisplay');
                angleEl.innerText = `夾角: ${viewAngle}° ${angleHint}`;
                angleEl.classList.remove('hidden');
            }

            updateLaunchSiteLine();
            
            // 同步變數到 AR 輸入框
            syncToAR();

            if(!document.getElementById('arModal').classList.contains('hidden')) {
                drawARSketch();
            }

            // 每次計算(數值變更)後都觸發自動儲存
            if (!isAutoLoading) {
                autoSaveLocal();
            }
        }

        // ====== AR 內部數值同步邏輯 ======
        function syncToAR() {
            const arInch = document.getElementById('arFwInch');
            const arWidth = document.getElementById('arFwWidth');
            const arPoints = document.getElementById('arFwPoints');
            if(arInch) arInch.value = document.getElementById('fwInch').value;
            if(arWidth) arWidth.value = document.getElementById('fwWidth').value;
            if(arPoints) arPoints.value = document.getElementById('fwPoints').value;
        }

        function syncFromAR() {
            // 從 AR 介面修改後，同步回主設定並重新計算
            document.getElementById('fwInch').value = document.getElementById('arFwInch').value;
            document.getElementById('fwWidth').value = document.getElementById('arFwWidth').value;
            document.getElementById('fwPoints').value = document.getElementById('arFwPoints').value;
            calculate();
        }

        // ==============================

        function getBearing(latlng1, latlng2) {
            const lat1 = latlng1.lat * Math.PI / 180;
            const lng1 = latlng1.lng * Math.PI / 180;
            const lat2 = latlng2.lat * Math.PI / 180;
            const lng2 = latlng2.lng * Math.PI / 180;
            const dLng = lng2 - lng1;
            const y = Math.sin(dLng) * Math.cos(lat2);
            const x = Math.cos(lat1) * Math.sin(lat2) - Math.sin(lat1) * Math.cos(lat2) * Math.cos(dLng);
            let brng = Math.atan2(y, x) * 180 / Math.PI;
            return (brng + 360) % 360;
        }

        function getOffsetLatLng(latlng, distanceMeters, angleDeg) {
            const lat = latlng.lat !== undefined ? latlng.lat : latlng[0];
            const lng = latlng.lng !== undefined ? latlng.lng : latlng[1];
            const latOffset = (distanceMeters * Math.cos(angleDeg * Math.PI / 180)) / 111320;
            const lngOffset = (distanceMeters * Math.sin(angleDeg * Math.PI / 180)) / (111320 * Math.cos(lat * Math.PI / 180));
            return [lat + latOffset, lng + lngOffset];
        }

        function updateLaunchSiteLine() {
            if (siteLineGroup) map.removeLayer(siteLineGroup);
            if (!fireworkPos) return;

            const W = parseFloat(document.getElementById('fwWidth').value) || 0;
            const angle = parseFloat(document.getElementById('siteAngle').value) || 0;
            const ptsCount = parseInt(document.getElementById('fwPoints').value) || 1;
            const inch = parseFloat(document.getElementById('fwInch').value) || 0;
            const burstDia = inch * 28;

            siteLineGroup = L.layerGroup().addTo(map);

            const pt1 = getOffsetLatLng(fireworkPos, W/2, angle);
            const pt2 = getOffsetLatLng(fireworkPos, W/2, angle + 180);

            L.polyline([pt1, pt2], { color: '#f97316', weight: 6, opacity: 0.9 }).addTo(siteLineGroup);

            for (let i = 0; i < ptsCount; i++) {
                let fraction = ptsCount === 1 ? 0.5 : i / (ptsCount - 1);
                let distFromCenter = (fraction - 0.5) * W; 
                let ptLatLng = getOffsetLatLng(fireworkPos, Math.abs(distFromCenter), distFromCenter > 0 ? angle : angle + 180);

                L.circle(ptLatLng, { radius: burstDia / 2, color: '#ef4444', weight: 1, fillOpacity: 0.05, dashArray: '5,5' }).addTo(siteLineGroup);
                L.circleMarker(ptLatLng, { radius: 3, fillColor: '#fff', color: '#000', weight: 1, fillOpacity: 1 }).addTo(siteLineGroup);
            }

            if (W < 1000) {
                const ptDash1 = getOffsetLatLng(fireworkPos, 500, angle);
                const ptDash2 = getOffsetLatLng(fireworkPos, 500, angle + 180);
                L.polyline([pt1, ptDash1], { color: '#f97316', weight: 4, dashArray: '8, 8', opacity: 0.6 }).addTo(siteLineGroup);
                L.polyline([pt2, ptDash2], { color: '#f97316', weight: 4, dashArray: '8, 8', opacity: 0.6 }).addTo(siteLineGroup);
            }
        }

        // ================= AR 相關函式 =================
        let arStream = null;
        let arAnimationId = null;

        async function openAR() {
            document.getElementById('arModal').classList.remove('hidden');
            const video = document.getElementById('arVideo');
            
            try {
                arStream = await navigator.mediaDevices.getUserMedia({ 
                    video: { facingMode: "environment" } 
                });
                video.srcObject = arStream;
                document.getElementById('arWarning').classList.add('hidden');
            } catch (err) {
                document.getElementById('arWarning').classList.remove('hidden');
            }

            resizeCanvas();
            window.addEventListener('resize', resizeCanvas);
            drawARSketch();
        }

        function closeAR() {
            document.getElementById('arModal').classList.add('hidden');
            if (arStream) {
                arStream.getTracks().forEach(track => track.stop());
                arStream = null;
            }
            window.removeEventListener('resize', resizeCanvas);
            if(arAnimationId) cancelAnimationFrame(arAnimationId);

            if (document.fullscreenElement || document.webkitFullscreenElement) {
                if (document.exitFullscreen) {
                    document.exitFullscreen();
                } else if (document.webkitExitFullscreen) {
                    document.webkitExitFullscreen();
                }
            }
        }

        function toggleFullscreen() {
            const elem = document.getElementById('arModal');
            if (!document.fullscreenElement && !document.webkitFullscreenElement) {
                if (elem.requestFullscreen) {
                    elem.requestFullscreen();
                } else if (elem.webkitRequestFullscreen) {
                    elem.webkitRequestFullscreen();
                }
            } else {
                if (document.exitFullscreen) {
                    document.exitFullscreen();
                } else if (document.webkitExitFullscreen) {
                    document.webkitExitFullscreen();
                }
            }
            setTimeout(resizeCanvas, 300);
        }

        function resizeCanvas() {
            const canvas = document.getElementById('arCanvas');
            canvas.width = canvas.clientWidth;
            canvas.height = canvas.clientHeight;
            drawARSketch();
        }

        function drawARSketch() {
            const canvas = document.getElementById('arCanvas');
            if (!canvas.getContext) return;
            const ctx = canvas.getContext('2d');
            const cw = canvas.width;
            const ch = canvas.height;

            ctx.clearRect(0, 0, cw, ch);

            const inch = parseFloat(document.getElementById('fwInch').value) || 0;
            const W = parseFloat(document.getElementById('fwWidth').value) || 0;
            const ptsCount = parseInt(document.getElementById('fwPoints').value) || 1;
            const landscapePct = parseFloat(document.getElementById('landscapeMargin').value) || 0;
            const elevationDiff = parseFloat(document.getElementById('elevationDiff').value) || 0;

            const burstDia = inch * 28;
            const altitude = inch * 32;
            const totalHeight = altitude + (burstDia / 2);
            const totalWidth = W + burstDia;

            // groundY 在這代表相機水平向前的視線 (eye-level horizon)
            const groundY = ch * (1 - (landscapePct / 100));

            let distance = 0;
            let slantDistance = 500;
            let viewAngle = 90;
            let isDefaultDistance = false;

            if (fireworkPos && cameraPos) {
                distance = fireworkPos.distanceTo(cameraPos);
                slantDistance = Math.sqrt(distance * distance + elevationDiff * elevationDiff);
                const siteAngle = parseFloat(document.getElementById('siteAngle').value) || 0;
                const bearing = getBearing(fireworkPos, cameraPos);
                let diff = Math.abs(bearing - siteAngle) % 180;
                if (diff > 90) diff = 180 - diff;
                viewAngle = Math.round(diff);
            } else {
                slantDistance = 500;
                viewAngle = 90;
                isDefaultDistance = true;
            }

            let scale = 1;
            let scaleHint = "";

            const orientationMode = document.getElementById('arOrientation').value;
            let isPortrait;
            if (orientationMode === 'portrait') {
                isPortrait = true;
            } else if (orientationMode === 'landscape') {
                isPortrait = false;
            } else {
                isPortrait = ch > cw; 
            }
            
            const orientationText = isPortrait ? "直幅" : "橫幅";
            const userFocalLength = parseFloat(document.getElementById('arFocalLength').value) || 23;
            const sensorWidth = isPortrait ? 24 : 36;
            const fovH_rad = 2 * Math.atan(sensorWidth / (2 * userFocalLength));
            const fovDeg = Math.round(fovH_rad * 180 / Math.PI);
            const focalLengthPx = (cw / 2) / Math.tan(fovH_rad / 2);
            
            // 使用斜邊距離計算真實縮放比例
            scale = focalLengthPx / slantDistance; 
            
            // ========== 核心升級：高低差透視計算 ==========
            let launchBaseY = groundY + (elevationDiff * scale);

            if (isDefaultDistance) {
                scaleHint = `⚠️ 預設 500m 模擬 | ${orientationText} (FOV: ${fovDeg}°)`;
            } else {
                scaleHint = `${Math.round(slantDistance)}m (含高低差斜距) | 視角 ${viewAngle}°`;
            }

            const apparentW = W * Math.max(Math.sin(viewAngle * Math.PI / 180), 0.05);
            const cx = cw / 2;

            // 畫相機平視水平線
            ctx.strokeStyle = 'rgba(255, 255, 255, 0.4)';
            ctx.lineWidth = 1;
            ctx.setLineDash([5, 5]);
            ctx.beginPath();
            ctx.moveTo(0, groundY);
            ctx.lineTo(cw, groundY);
            ctx.stroke();
            ctx.fillStyle = 'rgba(255, 255, 255, 0.6)';
            ctx.font = '12px sans-serif';
            ctx.textAlign = 'left';
            ctx.fillText(`相機水平視線 (0m)`, 10, groundY - 5);
            ctx.setLineDash([]);

            // 畫陣地實際所在基準面 (高低差線)
            if (elevationDiff !== 0) {
                ctx.strokeStyle = 'rgba(249, 115, 22, 0.5)';
                ctx.lineWidth = 1;
                ctx.setLineDash([2, 2]);
                ctx.beginPath();
                ctx.moveTo(0, launchBaseY);
                ctx.lineTo(cw, launchBaseY);
                ctx.stroke();
                ctx.fillStyle = 'rgba(249, 115, 22, 0.8)';
                ctx.fillText(`陣地基準面 (${-elevationDiff}m)`, 10, launchBaseY - 5);
                ctx.setLineDash([]);
            }

            for (let i = 0; i < ptsCount; i++) {
                let fraction = ptsCount === 1 ? 0.5 : i / (ptsCount - 1);
                
                let distFromCenter = (fraction - 0.5) * apparentW; 
                let pointX = cx + (distFromCenter * scale);
                
                // 煙火是從陣地基準面往上升空
                let explodeY = launchBaseY - (altitude * scale);
                let radiusPx = (burstDia / 2) * scale;

                ctx.strokeStyle = 'rgba(255, 255, 255, 0.5)';
                ctx.lineWidth = 2;
                ctx.beginPath();
                ctx.moveTo(pointX, launchBaseY);
                ctx.lineTo(pointX, explodeY);
                ctx.stroke();

                ctx.strokeStyle = 'rgba(239, 68, 68, 0.8)';
                ctx.lineWidth = 2;
                ctx.beginPath();
                ctx.arc(pointX, explodeY, Math.max(radiusPx, 2), 0, Math.PI * 2);
                ctx.stroke();
                
                ctx.fillStyle = 'rgba(249, 115, 22, 0.5)';
                ctx.beginPath();
                ctx.arc(pointX, explodeY, Math.max(radiusPx * 0.2, 2), 0, Math.PI * 2);
                ctx.fill();
            }

            ctx.fillStyle = 'rgba(255, 255, 255, 0.9)';
            ctx.font = 'bold 14px sans-serif';
            ctx.textAlign = 'center';
            ctx.shadowColor = "rgba(0,0,0,0.8)";
            ctx.shadowBlur = 4;
            
            ctx.fillText(`現場模擬草圖 (發射點: ${ptsCount} / 真實寬度: ${W}m)`, cx, 100);
            ctx.fillStyle = 'rgba(252, 211, 77, 1)'; 
            ctx.fillText(`狀態：${scaleHint}`, cx, 120);
            
            ctx.shadowBlur = 0;
        }

        // ================= 瀏覽器本地快取自動存檔 (Auto-Save) =================
        function autoSaveLocal() {
            if (isAutoLoading || !map) return;
            const data = {
                fwInch: document.getElementById('fwInch').value,
                fwPoints: document.getElementById('fwPoints').value,
                fwWidth: document.getElementById('fwWidth').value,
                elevationDiff: document.getElementById('elevationDiff').value,
                safetyMargin: document.getElementById('safetyMargin').value,
                landscapeMargin: document.getElementById('landscapeMargin').value,
                siteAngle: document.getElementById('siteAngle').value,
                fireworkPos: window.fireworkPos ? { lat: window.fireworkPos.lat, lng: window.fireworkPos.lng } : null,
                cameraPos: window.cameraPos ? { lat: window.cameraPos.lat, lng: window.cameraPos.lng } : null
            };
            localStorage.setItem('fireworks_autosave', JSON.stringify(data));
        }

        function autoLoadLocal() {
            isAutoLoading = true; // 鎖定自動儲存，防止讀取過程中覆蓋資料
            const saved = localStorage.getItem('fireworks_autosave');
            if (saved) {
                try {
                    const data = JSON.parse(saved);
                    document.getElementById('fwInch').value = data.fwInch || 12;
                    document.getElementById('fwPoints').value = data.fwPoints || 1;
                    document.getElementById('fwWidth').value = data.fwWidth || 100;
                    document.getElementById('elevationDiff').value = data.elevationDiff || 0;
                    document.getElementById('safetyMargin').value = data.safetyMargin || 20;
                    document.getElementById('landscapeMargin').value = data.landscapeMargin || 25;
                    document.getElementById('siteAngle').value = data.siteAngle || 90;
                    
                    if (data.fireworkPos) {
                        window.fireworkPos = L.latLng(data.fireworkPos.lat, data.fireworkPos.lng);
                        addMarker(window.fireworkPos, 'firework', '砲陣地');
                        document.getElementById('angleControlBox').classList.remove('hidden');
                    }
                    
                    if (data.cameraPos) {
                        window.cameraPos = L.latLng(data.cameraPos.lat, data.cameraPos.lng);
                        addMarker(window.cameraPos, 'camera', '拍攝點');
                    }
                    
                    if (window.fireworkPos && window.cameraPos) {
                        updateDistance(); 
                        fetchWeather(window.fireworkPos.lat, window.fireworkPos.lng);
                        map.fitBounds(L.latLngBounds([window.fireworkPos, window.cameraPos]), { padding: [50, 50] });
                    } else if (window.fireworkPos) {
                        map.setView(window.fireworkPos, 15);
                        calculate();
                    } else {
                        calculate();
                    }
                    showSaveMsg("🔄 已自動讀取上次設定與機位");
                } catch (err) {
                    console.error("Auto load error:", err);
                    calculate();
                }
            } else {
                calculate();
            }
            isAutoLoading = false; // 解除鎖定
        }

        // ================= JSON 檔案手動匯出 / 匯入 (備份用途) =================
        window.exportConfig = function() {
            const name = document.getElementById('configName').value.trim() || 'fireworks_config';
            const data = {
                name: name,
                fwInch: document.getElementById('fwInch').value,
                fwPoints: document.getElementById('fwPoints').value,
                fwWidth: document.getElementById('fwWidth').value,
                elevationDiff: document.getElementById('elevationDiff').value,
                safetyMargin: document.getElementById('safetyMargin').value,
                landscapeMargin: document.getElementById('landscapeMargin').value,
                siteAngle: document.getElementById('siteAngle').value,
                fireworkPos: window.fireworkPos ? { lat: window.fireworkPos.lat, lng: window.fireworkPos.lng } : null,
                cameraPos: window.cameraPos ? { lat: window.cameraPos.lat, lng: window.cameraPos.lng } : null
            };

            const blob = new Blob([JSON.stringify(data, null, 2)], { type: 'application/json' });
            const url = URL.createObjectURL(blob);
            
            const a = document.createElement('a');
            a.href = url;
            a.download = `${name}.json`;
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
            URL.revokeObjectURL(url);
            
            showSaveMsg("✅ 已成功匯出設定檔");
        };

        window.importConfig = function(event) {
            const file = event.target.files[0];
            if (!file) return;

            const reader = new FileReader();
            reader.onload = function(e) {
                try {
                    const data = JSON.parse(e.target.result);
                    
                    document.getElementById('configName').value = data.name || '';
                    document.getElementById('fwInch').value = data.fwInch || 12;
                    document.getElementById('fwPoints').value = data.fwPoints || 1;
                    document.getElementById('fwWidth').value = data.fwWidth || 100;
                    document.getElementById('elevationDiff').value = data.elevationDiff || 0;
                    document.getElementById('safetyMargin').value = data.safetyMargin || 20;
                    document.getElementById('landscapeMargin').value = data.landscapeMargin || 25;
                    document.getElementById('siteAngle').value = data.siteAngle || 90;
                    
                    resetMap();
                    
                    if (data.fireworkPos) {
                        window.fireworkPos = L.latLng(data.fireworkPos.lat, data.fireworkPos.lng);
                        addMarker(window.fireworkPos, 'firework', '砲陣地');
                        document.getElementById('angleControlBox').classList.remove('hidden');
                    }
                    
                    if (data.cameraPos) {
                        window.cameraPos = L.latLng(data.cameraPos.lat, data.cameraPos.lng);
                        addMarker(window.cameraPos, 'camera', '拍攝點');
                    }
                    
                    if (window.fireworkPos && window.cameraPos) {
                        updateDistance(); 
                        fetchWeather(window.fireworkPos.lat, window.fireworkPos.lng);
                        map.fitBounds(L.latLngBounds([window.fireworkPos, window.cameraPos]), { padding: [50, 50] });
                    } else if (window.fireworkPos) {
                        map.setView(window.fireworkPos, 15);
                        calculate();
                    } else {
                        calculate();
                    }
                    showSaveMsg(`✅ 已成功載入「${data.name || '設定檔'}」`);
                } catch (err) {
                    showSaveMsg("❌ 匯入失敗，檔案格式不正確", true);
                }
                event.target.value = '';
            };
            reader.readAsText(file);
        };

        function showSaveMsg(msg, isError = false) {
            const el = document.getElementById('saveMsg');
            if(!el) return;
            el.textContent = msg;
            el.className = `text-xs h-4 font-bold text-center block mt-1 ${isError ? 'text-red-500' : 'text-emerald-500'}`;
            setTimeout(() => el.textContent = '', 3000);
        }

        // ==========================================

        async function fetchWeather(lat, lng) {
            document.getElementById('weatherStatus').innerText = '正在讀取氣象預報...';
            try {
                const url = `https://api.open-meteo.com/v1/forecast?latitude=${lat}&longitude=${lng}&hourly=windspeed_10m,winddirection_10m&current_weather=true&timezone=auto`;
                const response = await fetch(url);
                const data = await response.json();
                displayWeather(data);
            } catch (error) {
                document.getElementById('weatherStatus').innerText = '無法獲取氣象資料。';
            }
        }

        function displayWeather(data) {
            const current = data.current_weather;
            const hourly = data.hourly;
            const forecastDiv = document.getElementById('windForecast');
            forecastDiv.innerHTML = '';
            
            document.getElementById('weatherStatus').innerHTML = `目前位置氣溫: ${current.temperature}°C <br><span class="text-xs text-orange-500 font-bold mt-1 inline-block">💡 點擊下方時段，可於地圖預覽該時間風向</span>`;

            let startIndex = hourly.time.findIndex(t => t === current.time);
            if (startIndex === -1) startIndex = new Date().getHours();

            let activeItem = null;

            for (let i = 0; i <= 6; i++) {
                const dataIndex = startIndex + i;
                if (dataIndex >= hourly.time.length) break;

                const timeObj = new Date(hourly.time[dataIndex]);
                const hour = timeObj.getHours().toString().padStart(2, '0');
                
                const windDir = i === 0 ? current.winddirection : hourly.winddirection_10m[dataIndex];
                const windSpd = i === 0 ? current.windspeed : hourly.windspeed_10m[dataIndex];
                const label = i === 0 ? "現在" : `+${i}hr (${hour}:00)`;

                const item = document.createElement('div');
                item.className = "flex items-center justify-between bg-white p-2 rounded-lg text-sm shadow-sm cursor-pointer border-2 border-transparent hover:border-blue-300 transition-all";
                item.innerHTML = `
                    <span class="font-bold text-slate-500">${label}</span>
                    <span class="flex items-center gap-2">
                        <span style="display:inline-block; transform: rotate(${windDir}deg)">⬆️</span>
                        ${getWindDirection(windDir)}
                    </span>
                    <span class="text-blue-600 font-medium">${windSpd} km/h</span>
                `;

                if (i === 0) {
                    item.classList.add('border-blue-500', 'bg-blue-50');
                    activeItem = item;
                    updateWindArrow(windDir, label);
                }

                item.onclick = () => {
                    if (activeItem) activeItem.classList.remove('border-blue-500', 'bg-blue-50');
                    item.classList.add('border-blue-500', 'bg-blue-50');
                    activeItem = item;
                    updateWindArrow(windDir, label);
                };

                forecastDiv.appendChild(item);
            }
        }

        function updateWindArrow(degree, timeLabel = "現在") {
            if (windArrow) map.removeLayer(windArrow);
            if (!fireworkPos || isNaN(degree)) return;
            
            const blowingToAngle = (degree + 180) % 360;
            const endPoint = getOffsetLatLng(fireworkPos, 300, blowingToAngle);
            
            const leftPt = getOffsetLatLng(endPoint, 40, blowingToAngle + 150);
            const rightPt = getOffsetLatLng(endPoint, 40, blowingToAngle - 150);

            const line = L.polyline([fireworkPos, endPoint], {
                color: '#a855f7',
                weight: 5,
                opacity: 0.6
            }).bindTooltip(`煙霧飄向 (${timeLabel})`, {permanent: true, direction: 'top'});

            const tip = L.polygon([endPoint, leftPt, rightPt], {
                color: '#a855f7',
                fillColor: '#a855f7',
                fillOpacity: 0.8
            });

            windArrow = L.layerGroup([line, tip]).addTo(map);
        }

        function getWindDirection(deg) {
            const directions = ['北', '北北東', '東北', '東北東', '東', '東南東', '東南', '南南東', '南', '南南西', '西南', '西南西', '西', '西北西', '西北', '北北西'];
            const index = Math.round(deg / 22.5) % 16;
            return directions[index];
        }
    </script>
</body>
</html>
