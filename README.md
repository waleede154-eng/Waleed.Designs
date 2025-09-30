<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Waleed Designs - مُحاكي تصميم غرف النوم</title>
    <!-- Load Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Load Cairo Font for Arabic -->
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700;900&display=swap" rel="stylesheet">
    <style>
        /* Custom styles to ensure proper Arabic typography and flow */
        body {
            font-family: 'Cairo', sans-serif;
            background-color: #f8fafc; /* Tailwind's slate-50 */
        }
        /* Custom scrollbar for a cleaner look */
        ::-webkit-scrollbar { width: 8px; }
        ::-webkit-scrollbar-track { background: #f1f5f9; }
        ::-webkit-scrollbar-thumb { background: #cbd5e1; border-radius: 10px; }
        ::-webkit-scrollbar-thumb:hover { background: #94a3b8; }

        /* Style for primary buttons for a more modern feel */
        .primary-btn {
            background-color: #25D366; /* WhatsApp Green */
            color: white;
            padding: 0.75rem 1.5rem;
            border-radius: 0.75rem;
            font-weight: bold;
            transition: background-color 0.2s, transform 0.1s, box-shadow 0.2s;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
            box-shadow: 0 4px 14px 0 rgba(37, 211, 102, 0.39);
        }
        .primary-btn:hover {
            background-color: #1DA851; 
            transform: translateY(-2px);
            box-shadow: 0 6px 20px 0 rgba(37, 211, 102, 0.23);
        }
        .primary-btn:disabled {
            background-color: #9ca3af;
            cursor: not-allowed;
            transform: none;
            box-shadow: none;
        }

        /* Custom Modal Styles */
        .modal-backdrop {
            transition: opacity 0.3s ease;
        }
        .modal-content {
            transition: transform 0.3s ease, opacity 0.3s ease;
        }

        /* Custom Checkbox Styles */
        .custom-checkbox:checked {
            background-color: #4f46e5;
            border-color: #4f46e5;
        }
    </style>
</head>
<body class="bg-slate-50">

    <div class="max-w-4xl mx-auto p-4 sm:p-6 pb-40"> <!-- Added padding-bottom for sticky footer -->
        
        <!-- HEADER -->
        <header class="text-center mb-8 border-b-2 border-indigo-200 pb-6">
            <h1 class="text-4xl sm:text-5xl font-black text-indigo-800">Waleed Designs</h1>
            <p class="text-lg text-slate-600 mt-2">محاكي الأسعار التفاعلي لغرف النوم</p>
            <p class="text-xs text-slate-400 mt-4">معرف المستخدم: <span id="user-id-display" class="font-mono bg-slate-200 text-slate-600 px-2 py-1 rounded">يتم التحميل...</span></p>
        </header>
        
        <!-- CONFIGURATOR FORM -->
        <form id="configurator-form" class="space-y-8">
            
            <!-- Room Size Card -->
            <div class="bg-indigo-100 p-6 rounded-2xl border-2 border-indigo-300 shadow-lg">
                <h3 class="text-2xl font-bold mb-4 text-indigo-800 flex items-center gap-3">
                    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m21 21-6-6m6 6v-4.5m0 4.5h-4.5"/><path d="M3 3h7v7H3z"/><path d="M14 3h7v7h-7z"/><path d="M3 14h7v7H3z"/></svg>
                    <span>أبعاد الغرفة الرئيسية</span>
                </h3>
                <div>
                    <label for="room-size" class="block text-base font-medium text-slate-700 mb-2">اختر حجم الغرفة المبدئي:</label>
                    <select id="room-size" class="w-full p-3 bg-white rounded-lg border border-slate-300 focus:ring-2 focus:ring-indigo-500 focus:border-indigo-500 transition">
                        <option value="small">صغيرة (Small)</option>
                        <option value="medium" selected>متوسطة (Medium)</option>
                        <option value="large">كبيرة (Large)</option>
                    </select>
                    <p class="text-sm text-slate-500 mt-2">هذا الاختيار يحدد الأبعاد الافتراضية لجميع قطع الأثاث.</p>
                </div>
            </div>

            <!-- Main Furniture Grid -->
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
                
                <!-- 1. Closet (دولاب) Card -->
                <div class="bg-white p-6 rounded-2xl shadow-md border space-y-4">
                    <div class="flex justify-between items-center border-b pb-3">
                        <h3 class="text-xl font-bold text-slate-800">1. الدولاب</h3>
                        <div class="flex items-center gap-2">
                            <label for="include-closet" class="text-sm font-medium text-slate-600">إضافة للسعر</label>
                            <input type="checkbox" id="include-closet" class="h-5 w-5 text-indigo-600 rounded border-gray-300 custom-checkbox" checked>
                        </div>
                    </div>
                    <div>
                        <label for="closet-wood-type" class="text-sm font-medium text-slate-600">نوع الخشب</label>
                        <select id="closet-wood-type" class="w-full mt-1 p-2 rounded-md border border-slate-300">
                            <option value="counter">كونتر</option>
                            <option value="sandwich_hpl">سندوتش HPL</option>
                            <option value="hpl_separate">HPL</option>
                        </select>
                    </div>
                    <div id="closet-paint-option-container" class="hidden">
                        <label for="closet-paint-type" class="text-sm font-medium text-slate-600">نوع الدهان</label>
                        <select id="closet-paint-type" class="w-full mt-1 p-2 rounded-md border border-slate-300">
                            <option value="none" selected>بدون دهان</option>
                            <option value="ester">استر (Stain/Varnish)</option>
                            <option value="duco">دوكو (Lacquer/Duco)</option>
                        </select>
                    </div>
                    <div class="grid grid-cols-3 gap-2">
                        <div><label class="text-xs text-slate-500">العرض (سم)</label><input type="number" id="closet-width" value="200" min="100" class="w-full mt-1 p-2 rounded-md border border-slate-300"></div>
                        <div><label class="text-xs text-slate-500">الارتفاع (سم)</label><input type="number" id="closet-height" value="240" min="200" class="w-full mt-1 p-2 rounded-md border border-slate-300"></div>
                        <div><label class="text-xs text-slate-500">العمق (سم)</label><input type="number" id="closet-depth" value="60" min="50" class="w-full mt-1 p-2 rounded-md border border-slate-300"></div>
                    </div>
                    <div class="grid grid-cols-3 gap-2">
                         <div><label class="text-xs text-slate-500">عدد الضُلف</label><input type="number" id="closet-doors" value="3" min="1" class="w-full mt-1 p-2 rounded-md border border-slate-300"></div>
                         <div><label class="text-xs text-slate-500">ضلف زجاج</label><input type="number" id="closet-glass-doors" value="0" min="0" class="w-full mt-1 p-2 rounded-md border border-slate-300"></div>
                         <div><label class="text-xs text-slate-500">أدراج داخلية</label><input type="number" id="closet-internal-drawers" value="2" min="0" class="w-full mt-1 p-2 rounded-md border border-slate-300"></div>
                    </div>
                     <div class="grid grid-cols-2 gap-2">
                        <div><label class="text-sm font-medium text-slate-600">آلية الضُلف</label><select id="door-mechanism" class="w-full mt-1 p-2 rounded-md border border-slate-300"><option value="hinged">مفصلي</option><option value="sliding">جرار</option></select></div>
                        <div><label class="text-sm font-medium text-slate-600">رفوف داخلية</label><input type="number" id="closet-shelves" value="4" min="1" class="w-full mt-1 p-2 rounded-md border border-slate-300"></div>
                    </div>
                    <div class="flex items-center pt-2"><input type="checkbox" id="closet-led" class="h-4 w-4 text-indigo-600 rounded"><label for="closet-led" class="mr-2 text-sm text-slate-700">إضافة إضاءة ليد داخلية</label></div>
                </div>

                <!-- 2. Bed & Nightstands Card -->
                <div class="bg-white p-6 rounded-2xl shadow-md border space-y-4">
                     <div class="flex justify-between items-center border-b pb-3">
                        <h3 class="text-xl font-bold text-slate-800">2. السرير والكمود</h3>
                        <div class="flex items-center gap-2">
                            <label for="include-bed" class="text-sm font-medium text-slate-600">إضافة للسعر</label>
                            <input type="checkbox" id="include-bed" class="h-5 w-5 text-indigo-600 rounded border-gray-300 custom-checkbox" checked>
                        </div>
                    </div>
                    <div class="grid grid-cols-2 gap-2">
                        <div><label class="text-sm font-medium text-slate-600">عدد السراير</label><input type="number" id="bed-count" value="1" min="1" class="w-full mt-1 p-2 rounded-md border border-slate-300"></div>
                        <div><label class="text-sm font-medium text-slate-600">مقاس السرير</label><select id="bed-size" class="w-full mt-1 p-2 rounded-md border border-slate-300"><option value="100">100 سم</option><option value="120">120 سم</option><option value="140">140 سم</option><option value="160" selected>160 سم</option><option value="180">180 سم</option><option value="200">200 سم</option></select></div>
                    </div>
                    <div>
                        <label class="text-sm font-medium text-slate-600">خامة السرير</label>
                        <select id="bed-material" class="w-full mt-1 p-2 rounded-md border border-slate-300">
                            <option value="wood">خشب فقط</option>
                            <option value="upholstered_back">تنجيد الظهر فقط</option>
                            <option value="upholstered_full">تنجيد كامل</option>
                        </select>
                    </div>
                     <div id="bed-paint-option-container" class="hidden">
                        <label for="bed-paint-type" class="text-sm font-medium text-slate-600">نوع دهان السرير</label>
                        <select id="bed-paint-type" class="w-full mt-1 p-2 rounded-md border border-slate-300">
                            <option value="none" selected>بدون دهان</option>
                            <option value="ester">استر</option>
                            <option value="duco">دوكو</option>
                        </select>
                    </div>
                    <div class="grid grid-cols-2 gap-2 pt-2">
                         <div class="flex items-center"><input type="checkbox" id="lifting-mechanism" class="h-4 w-4 text-indigo-600 rounded"><label for="lifting-mechanism" class="mr-2 text-sm text-slate-700">ميكانيزم رفع</label></div>
                         <div class="flex items-center"><input type="checkbox" id="bed-led" class="h-4 w-4 text-indigo-600 rounded"><label for="bed-led" class="mr-2 text-sm text-slate-700">إضاءة ليد للسرير</label></div>
                    </div>
                    <div class="grid grid-cols-2 gap-2 pt-2 border-t mt-4">
                        <div><label class="text-sm font-medium text-slate-600">عدد الكمود</label><input type="number" id="komod-count" value="2" min="0" class="w-full mt-1 p-2 rounded-md border border-slate-300"></div>
                        <div><label class="text-sm font-medium text-slate-600">أدراج الكمود</label><input type="number" id="komod-drawers" value="2" min="0" class="w-full mt-1 p-2 rounded-md border border-slate-300"></div>
                    </div>
                </div>

                <!-- 3. Dresser Card -->
                <div class="bg-white p-6 rounded-2xl shadow-md border space-y-4 lg:col-span-2">
                    <div class="flex justify-between items-center border-b pb-3">
                        <h3 class="text-xl font-bold text-slate-800">3. التسريحة والمرايا</h3>
                         <div class="flex items-center gap-2">
                            <label for="include-dresser" class="text-sm font-medium text-slate-600">إضافة للسعر</label>
                            <input type="checkbox" id="include-dresser" class="h-5 w-5 text-indigo-600 rounded border-gray-300 custom-checkbox" checked>
                        </div>
                    </div>
                    <div class="grid grid-cols-2 lg:grid-cols-4 gap-2">
                        <div><label class="text-sm font-medium text-slate-600">طريقة التركيب</label><select id="dresser-type" class="w-full mt-1 p-2 rounded-md border border-slate-300"><option value="hanging">معلقة</option><option value="floor" selected>على الأرض</option></select></div>
                        <div><label class="text-sm font-medium text-slate-600">عدد الأدراج</label><input type="number" id="dresser-drawers" value="3" min="0" class="w-full mt-1 p-2 rounded-md border border-slate-300"></div>
                        <div><label class="text-xs text-slate-500">العرض (سم)</label><input type="number" id="dresser-width" value="120" min="60" class="w-full mt-1 p-2 rounded-md border border-slate-300"></div>
                        <div><label class="text-xs text-slate-500">العمق (سم)</label><input type="number" id="dresser-depth" value="45" min="30" class="w-full mt-1 p-2 rounded-md border border-slate-300"></div>
                    </div>
                    <div class="grid grid-cols-2 lg:grid-cols-4 gap-2 pt-4 border-t mt-4">
                        <div>
                           <label for="mirror-shape" class="text-sm font-medium text-slate-600">شكل المرايا</label>
                           <select id="mirror-shape" class="w-full mt-1 p-2 rounded-md border border-slate-300">
                               <option value="rectangle">مستطيل</option>
                               <option value="square">مربع</option>
                               <option value="circle">دائري</option>
                           </select>
                        </div>
                        <div><label id="mirror-width-label" class="text-xs text-slate-500">عرض المرايا (سم)</label><input type="number" id="mirror-width" value="70" min="40" class="w-full mt-1 p-2 rounded-md border border-slate-300"></div>
                        <div id="mirror-height-container"><label id="mirror-height-label" class="text-xs text-slate-500">ارتفاع المرايا (سم)</label><input type="number" id="mirror-height" value="100" min="60" class="w-full mt-1 p-2 rounded-md border border-slate-300"></div>
                        <div class="flex items-end pb-1"><div class="flex items-center"><input type="checkbox" id="mirror-led" class="h-4 w-4 text-indigo-600 rounded"><label for="mirror-led" class="mr-2 text-sm text-slate-700">إضاءة ليد للمرايا</label></div></div>
                    </div>
                </div>

            </div> <!-- End Grid -->

            <!-- Additional Furniture Section -->
            <div class="bg-white p-6 rounded-2xl shadow-md border space-y-6">
                <h3 class="text-xl font-bold text-slate-800 border-b pb-3">4. قطع أثاث إضافية</h3>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    
                    <!-- TV Table -->
                    <div class="space-y-3 p-4 border rounded-lg bg-slate-50">
                        <div class="flex justify-between items-center">
                            <h4 class="font-bold text-slate-700">ترابيزة تليفزيون (TV Unit)</h4>
                            <div class="flex items-center gap-2">
                                <label for="include-tv-table" class="text-sm font-medium text-slate-600">إضافة للسعر</label>
                                <input type="checkbox" id="include-tv-table" class="h-5 w-5 text-indigo-600 rounded border-gray-300 custom-checkbox">
                            </div>
                        </div>
                        <div class="grid grid-cols-3 gap-2">
                            <div><label class="text-xs text-slate-500">العرض (سم)</label><input type="number" id="tv-table-width" value="160" min="80" class="w-full mt-1 p-2 rounded-md border border-slate-300"></div>
                            <div><label class="text-xs text-slate-500">الارتفاع (سم)</label><input type="number" id="tv-table-height" value="50" min="30" class="w-full mt-1 p-2 rounded-md border border-slate-300"></div>
                            <div><label class="text-xs text-slate-500">العمق (سم)</label><input type="number" id="tv-table-depth" value="40" min="30" class="w-full mt-1 p-2 rounded-md border border-slate-300"></div>
                        </div>
                         <div>
                            <label class="text-xs text-slate-500">عدد الأدراج</label>
                            <input type="number" id="tv-table-drawers" value="0" min="0" class="w-full mt-1 p-2 rounded-md border border-slate-300">
                        </div>
                    </div>

                    <!-- Coffee Table -->
                    <div class="space-y-3 p-4 border rounded-lg bg-slate-50">
                        <div class="flex justify-between items-center">
                            <h4 class="font-bold text-slate-700">ترابيزة وسط (Coffee Table)</h4>
                            <div class="flex items-center gap-2">
                                <label for="include-coffee-table" class="text-sm font-medium text-slate-600">إضافة للسعر</label>
                                <input type="checkbox" id="include-coffee-table" class="h-5 w-5 text-indigo-600 rounded border-gray-300 custom-checkbox">
                            </div>
                        </div>
                        <div class="grid grid-cols-3 gap-2">
                           <div><label class="text-xs text-slate-500">العرض (سم)</label><input type="number" id="coffee-table-width" value="100" min="50" class="w-full mt-1 p-2 rounded-md border border-slate-300"></div>
                           <div><label class="text-xs text-slate-500">الارتفاع (سم)</label><input type="number" id="coffee-table-height" value="45" min="30" class="w-full mt-1 p-2 rounded-md border border-slate-300"></div>
                           <div><label class="text-xs text-slate-500">العمق (سم)</label><input type="number" id="coffee-table-depth" value="60" min="40" class="w-full mt-1 p-2 rounded-md border border-slate-300"></div>
                        </div>
                    </div>

                </div>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 gap-4 text-center pt-8">
                 <button type="button" id="generate-image-btn" class="primary-btn bg-slate-700 hover:bg-slate-800 shadow-slate-300 hover:shadow-slate-400 w-full py-3 text-lg">
                    توليد صورة للمقترح
                    <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-image"><rect width="18" height="18" x="3" y="3" rx="2" ry="2"/><circle cx="9" cy="9" r="2"/><path d="m21 15-3.086-3.086a2 2 0 0 0-2.828 0L6 21"/></svg>
                </button>
                <button type="button" id="show-quote-btn" class="primary-btn bg-indigo-600 hover:bg-indigo-700 shadow-indigo-300 hover:shadow-indigo-400 w-full py-3 text-lg">
                    عرض السعر وطلب التواصل
                </button>
            </div>

        </form>
    </div>

    <!-- STICKY FOOTER FOR PRICE & SUBMISSION -->
    <footer class="fixed bottom-0 left-0 right-0 bg-white/80 backdrop-blur-sm border-t border-slate-200 shadow-t-xl z-50 hidden">
        <div class="max-w-4xl mx-auto p-4 flex flex-col sm:flex-row justify-between items-center gap-4">
            <!-- Price Display -->
            <div class="text-center sm:text-right">
                <p class="text-sm font-medium text-slate-500">السعر التقديري المحدد</p>
                <p id="total-price" class="text-3xl font-black text-indigo-700">0 ج.م</p>
                <p id="price-error-message" class="text-xs text-red-600 h-4"></p>
            </div>
            <!-- Contact Info & Submit -->
            <div class="flex-grow w-full sm:w-auto flex flex-col sm:flex-row items-center gap-3">
                 <input type="text" id="customer-name" placeholder="الاسم بالكامل *" class="w-full sm:w-40 p-2 text-sm rounded-md border border-slate-300" required>
                 <input type="tel" id="customer-phone" placeholder="رقم التليفون *" class="w-full sm:w-40 p-2 text-sm rounded-md border border-slate-300" required>
                 <button type="button" id="request-quote-btn" class="primary-btn w-full sm:w-auto" disabled>
                     إرسال الطلب
                     <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m22 2-7 20-4-9-9-4Z"/><path d="M22 2 11 13"/></svg>
                 </button>
            </div>
        </div>
    </footer>

    <!-- MODAL for alerts -->
    <div id="alert-modal" class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center p-4 z-[60] opacity-0 pointer-events-none modal-backdrop">
        <div class="bg-white rounded-lg shadow-xl p-6 w-full max-w-sm text-center transform scale-95 opacity-0 modal-content">
            <h3 id="modal-title" class="text-lg font-bold text-slate-800">تنبيه</h3>
            <p id="modal-message" class="text-slate-600 mt-2 mb-6">محتوى الرسالة هنا.</p>
            <button id="modal-close-btn" class="bg-indigo-600 text-white font-bold py-2 px-6 rounded-lg hover:bg-indigo-700 transition">حسنًا</button>
        </div>
    </div>

    <!-- IMAGE MODAL -->
    <div id="image-modal" class="fixed inset-0 bg-black bg-opacity-70 flex items-center justify-center p-4 z-[70] opacity-0 pointer-events-none modal-backdrop">
        <div class="bg-white rounded-lg shadow-xl w-full max-w-2xl text-center transform scale-95 opacity-0 modal-content relative p-4">
            <button id="image-modal-close-btn" class="absolute -top-4 -right-4 bg-white text-slate-800 rounded-full h-10 w-10 flex items-center justify-center font-bold text-2xl shadow-lg border">&times;</button>
            <div id="image-loading-spinner" class="h-96 flex flex-col items-center justify-center text-slate-600">
                 <div class="animate-spin rounded-full h-16 w-16 border-b-4 border-indigo-600 mb-4"></div>
                 <p>جاري توليد الصورة، قد يستغرق الأمر لحظات...</p>
            </div>
            <img id="generated-image" src="" alt="صورة التصميم المقترح" class="rounded-lg hidden w-full h-auto max-h-[80vh]">
        </div>
    </div>

    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInAnonymously, signInWithCustomToken, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        
        // --- GLOBAL APP STATE & CONFIG ---
        const App = {
            auth: null,
            currentUserId: null,
            elements: {},
            config: {
                WHATSAPP_NUMBER: "201110846333",
                COSTS: {
                    WOOD_BASE: { 'counter': 2800, 'sandwich_hpl': 2320, 'hpl_separate': 2720 },
                    PAINT: { 'ester': 200, 'duco': 400, 'none': 0 },
                    CLOSET: { 'sliding': 200, 'glass_door': 1500, 'wood_door_deduction': 1000, 'internal_drawer': 400, 'led': 1200, 'shelves': 80 },
                    BED: { 'base_price_unit_160': 4800, 'lifting_mechanism': 3600, 'upholstered_back': 1600, 'upholstered_full': 3200, 'led': 640 },
                    KOMOD: { 'base_price': 1440, 'drawer_cost': 480 },
                    DRESSER: { 'hanging_premium': 400, 'drawer_cost': 560 },
                    MIRROR: { 'base_area_cost_per_sqm': 800, 'led': 960 },
                    TABLES: { 'base_cost_per_sqm': 2400, 'drawer_cost': 500 },
                },
                DIMENSIONS: {
                    'small': { closet: { w: 160, h: 220 }, bed_size: '140', dresser: { w: 100, d: 40, drawers: 2 }, mirror: { w: 60, h: 90 } },
                    'medium': { closet: { w: 200, h: 240 }, bed_size: '160', dresser: { w: 120, d: 45, drawers: 3 }, mirror: { w: 70, h: 100 } },
                    'large': { closet: { w: 250, h: 250 }, bed_size: '180', dresser: { w: 140, d: 50, drawers: 4 }, mirror: { w: 80, h: 120 } }
                },
                AR_TRANSLATIONS: {
                    roomSize: { 'small': 'صغيرة', 'medium': 'متوسطة', 'large': 'كبيرة' },
                    woodType: { 'counter': 'كونتر', 'sandwich_hpl': 'سندوتش HPL', 'hpl_separate': 'HPL' },
                    paintType: { 'ester': 'استر', 'duco': 'دوكو', 'none': 'بدون' },
                    mechanism: { 'hinged': 'مفصلي', 'sliding': 'جرار' },
                    bedMaterial: { 'wood': 'خشب فقط', 'upholstered_back': 'تنجيد الظهر', 'upholstered_full': 'تنجيد كامل' },
                    dresserType: { 'hanging': 'معلقة', 'floor': 'على الأرض' },
                    mirrorShape: { 'rectangle': 'مستطيل', 'square': 'مربع', 'circle': 'دائري' },
                    boolean: { true: 'نعم', false: 'لا' }
                }
            }
        };

        // --- UTILITY FUNCTIONS ---
        const $ = (selector) => document.querySelector(selector);
        const $$ = (selector) => document.querySelectorAll(selector);

        function showAlert(message, title = "تنبيه") {
            App.elements.modalTitle.textContent = title;
            App.elements.modalMessage.textContent = message;
            App.elements.alertModal.classList.remove('opacity-0', 'pointer-events-none');
            App.elements.modalContent.classList.remove('scale-95', 'opacity-0');
        }

        function hideAlert() {
            App.elements.modalContent.classList.add('scale-95', 'opacity-0');
            App.elements.alertModal.classList.add('opacity-0');
            setTimeout(() => App.elements.alertModal.classList.add('pointer-events-none'), 300);
        }
        
        // --- UI MANIPULATION ---
        function updateUI() {
            const closetWoodType = App.elements.closetWoodType.value;
            $('#closet-paint-option-container').style.display = (closetWoodType === 'counter') ? 'block' : 'none';
            
            const bedMaterial = App.elements.bedMaterial.value;
            $('#bed-paint-option-container').style.display = (bedMaterial === 'wood') ? 'block' : 'none';

            const mirrorShape = App.elements.mirrorShape.value;
            const widthLabel = $('#mirror-width-label');
            const heightContainer = $('#mirror-height-container');
            if (mirrorShape === 'circle') {
                widthLabel.textContent = 'قطر المرايا (سم)';
                heightContainer.style.display = 'none';
            } else if (mirrorShape === 'square') {
                widthLabel.textContent = 'طول ضلع المرايا (سم)';
                heightContainer.style.display = 'none';
            } else {
                widthLabel.textContent = 'عرض المرايا (سم)';
                heightContainer.style.display = 'block';
            }

            // Enable/disable submit button based on contact info
            const name = App.elements.customerName.value.trim();
            const phone = App.elements.customerPhone.value.trim();
            App.elements.requestQuoteBtn.disabled = !(name && phone);
        }
        
        function updateDimensionsBasedOnSize() {
            const size = App.elements.roomSize.value;
            const dims = App.config.DIMENSIONS[size];
            if (!dims) return;

            App.elements.closetWidth.value = dims.closet.w;
            App.elements.closetHeight.value = dims.closet.h;
            App.elements.closetDepth.value = 60;
            App.elements.bedSize.value = dims.bed_size;
            App.elements.dresserWidth.value = dims.dresser.w;
            App.elements.dresserDepth.value = dims.dresser.d;
            App.elements.dresserDrawers.value = dims.dresser.drawers;
            App.elements.mirrorWidth.value = dims.mirror.w;
            App.elements.mirrorHeight.value = dims.mirror.h;
            
        }

        function showQuoteFooter() {
            recalculate(); // Ensure price is updated before showing
            App.elements.footer.classList.remove('hidden');
            App.elements.showQuoteBtn.parentElement.classList.add('hidden'); 
            setTimeout(() => { 
                 App.elements.footer.scrollIntoView({ behavior: 'smooth', block: 'end' });
            }, 100);
        }
        
        // --- CORE PRICING LOGIC ---
        function calculateSurfaceArea(w, h, d) {
            const [widthM, heightM, depthM] = [w / 100, h / 100, d / 100];
            return (widthM * heightM * 2) + (widthM * depthM) + (heightM * depthM * 2);
        }

        function calculateTotal() {
            const formConfig = getFullConfiguration(); // Use a more detailed config for calculation
            const C = App.config.COSTS;
            let total = 0;
            let error = null;

            if (formConfig.includeCloset) {
                const cl = formConfig.closet;
                if (cl.width > 0 && cl.height > 0) {
                    const area = calculateSurfaceArea(cl.width, cl.height, cl.depth);
                    total += area * (C.WOOD_BASE[cl.woodType] + C.PAINT[cl.paintType]);
                    total += cl.internalDrawers * C.CLOSET.internal_drawer;
                    total += cl.shelves * C.CLOSET.shelves;
                    if (cl.mechanism === 'sliding') total += cl.doors * C.CLOSET.sliding;
                    if (cl.hasLed) total += C.CLOSET.led;
                    if (cl.glassDoors > cl.doors) error = "عدد الضلف الزجاج لا يمكن أن يكون أكبر من العدد الكلي.";
                    total += cl.glassDoors * (C.CLOSET.glass_door - C.CLOSET.wood_door_deduction);
                }
            }

            if (formConfig.includeBed) {
                const be = formConfig.bed;
                if (be.count > 0 && be.size > 0) {
                    let bedPrice = C.BED.base_price_unit_160 * (be.size / 160);
                    if (be.material === 'upholstered_back') bedPrice += C.BED.upholstered_back;
                    if (be.material === 'upholstered_full') bedPrice += C.BED.upholstered_full;
                    if (be.hasLiftingMechanism) bedPrice += C.BED.lifting_mechanism;
                    if (be.hasLed) bedPrice += C.BED.led;
                    if (be.material === 'wood') bedPrice += (be.size / 100 * 2) * C.PAINT[be.paintType];
                    total += bedPrice * be.count;
                }
                const ko = formConfig.komod;
                if (ko.count > 0) {
                    total += ko.count * (C.KOMOD.base_price + (ko.drawers * C.KOMOD.drawer_cost));
                }
            }

            if (formConfig.includeDresser) {
                const dr = formConfig.dresser;
                if (dr.width > 0) {
                    const area = calculateSurfaceArea(dr.width, 90, dr.depth);
                    total += area * C.WOOD_BASE.counter;
                    total += dr.drawers * C.DRESSER.drawer_cost;
                    if (dr.type === 'hanging') total += C.DRESSER.hanging_premium;

                    let mirrorArea = 0;
                    if (dr.mirrorShape === 'circle') mirrorArea = Math.PI * Math.pow(dr.mirrorWidth / 200, 2);
                    else if (dr.mirrorShape === 'square') mirrorArea = Math.pow(dr.mirrorWidth / 100, 2);
                    else mirrorArea = (dr.mirrorWidth / 100) * (dr.mirrorHeight / 100);
                    total += mirrorArea * C.MIRROR.base_area_cost_per_sqm;
                    if (dr.hasMirrorLed) total += C.MIRROR.led;
                }
            }
            
            if(formConfig.includeTvTable){
                const tv = formConfig.tvTable;
                if(tv.width > 0 && tv.height > 0){
                    const area = calculateSurfaceArea(tv.width, tv.height, tv.depth);
                    total += area * C.TABLES.base_cost_per_sqm;
                    total += tv.drawers * C.TABLES.drawer_cost;
                }
            }

            if(formConfig.includeCoffeeTable){
                const coffee = formConfig.coffeeTable;
                if(coffee.width > 0 && coffee.height > 0){
                    const area = calculateSurfaceArea(coffee.width, coffee.height, coffee.depth);
                    total += area * C.TABLES.base_cost_per_sqm;
                }
            }
            
            return { total: error ? -1 : total, error };
        }

        function recalculate() {
            const result = calculateTotal();
            App.elements.totalPrice.textContent = `${Math.round(result.total).toLocaleString('ar-EG')} ج.م`;
            App.elements.priceErrorMessage.textContent = result.error || '';
        }

        // --- EVENT HANDLING & SUBMISSION ---
        function submitQuote() {
            const name = App.elements.customerName.value.trim();
            const phone = App.elements.customerPhone.value.trim();
            
            if (!name || !phone) {
                showAlert('الرجاء إدخال الاسم ورقم التليفون لإرسال الطلب.');
                return;
            }
            
            const { total, error } = calculateTotal();
            if (error) {
                showAlert(`لا يمكن إرسال الطلب. ${error}`);
                return;
            }

            const fullConfig = getFullConfiguration();
            const T = App.config.AR_TRANSLATIONS;
            
            let summary = `*طلب عرض سعر جديد من تطبيق Waleed Designs*
---------------------------------------------
*الاسم:* ${name}
*التليفون:* ${phone}
*معرف المستخدم:* ${App.currentUserId}
*حجم الغرفة المبدئي:* ${T.roomSize[fullConfig.roomSize]}`;

            if(fullConfig.includeCloset){
                summary += `
---------------------------------------------
*-- مواصفات الدولاب --*
- نوع الخشب: ${T.woodType[fullConfig.closet.woodType]} | دهان: ${T.paintType[fullConfig.closet.paintType]}
- الأبعاد (ع×ا×ع): ${fullConfig.closet.width}×${fullConfig.closet.height}×${fullConfig.closet.depth} سم
- آلية الضلف: ${T.mechanism[fullConfig.closet.mechanism]} (${fullConfig.closet.doors} ضلفة)
- ضلف زجاج: ${fullConfig.closet.glassDoors} | أدراج: ${fullConfig.closet.internalDrawers} | رفوف: ${fullConfig.closet.shelves}
- إضاءة ليد: ${T.boolean[fullConfig.closet.hasLed]}`;
            }

            if(fullConfig.includeBed){
                 summary += `
---------------------------------------------
*-- مواصفات السرير والكمود --*
- عدد السراير: ${fullConfig.bed.count} | مقاس: ${fullConfig.bed.size} سم
- الخامة: ${T.bedMaterial[fullConfig.bed.material]} | دهان: ${T.paintType[fullConfig.bed.paintType]}
- ميكانيزم رفع: ${T.boolean[fullConfig.bed.hasLiftingMechanism]} | إضاءة ليد: ${T.boolean[fullConfig.bed.hasLed]}
- الكمود: ${fullConfig.komod.count} | أدراج الكمود: ${fullConfig.komod.drawers}`;
            }

            if(fullConfig.includeDresser){
                 summary += `
---------------------------------------------
*-- مواصفات التسريحة --*
- التركيب: ${T.dresserType[fullConfig.dresser.type]} | أدراج: ${fullConfig.dresser.drawers}
- الأبعاد (ع×ع): ${fullConfig.dresser.width}×${fullConfig.dresser.depth} سم
- المرايا: ${T.mirrorShape[fullConfig.dresser.mirrorShape]} | إضاءة ليد: ${T.boolean[fullConfig.dresser.hasMirrorLed]}`;
            }

            if(fullConfig.includeTvTable){
                summary += `
---------------------------------------------
*-- مواصفات ترابيزة التليفزيون (TV Unit) --*
- الأبعاد (ع×ا×ع): ${fullConfig.tvTable.width}×${fullConfig.tvTable.height}×${fullConfig.tvTable.depth} سم
- عدد الأدراج: ${fullConfig.tvTable.drawers}`;
            }

             if(fullConfig.includeCoffeeTable){
                summary += `
---------------------------------------------
*-- مواصفات ترابيزة الوسط (Coffee Table) --*
- الأبعاد (ع×ا×ع): ${fullConfig.coffeeTable.width}×${fullConfig.coffeeTable.height}×${fullConfig.coffeeTable.depth} سم`;
            }

            summary += `
---------------------------------------------
*السعر التقديري الإجمالي المحدد: ${Math.round(total).toLocaleString('ar-EG')} ج.م*`;

            const whatsappUrl = `https://wa.me/${App.config.WHATSAPP_NUMBER}?text=${encodeURIComponent(summary.trim())}`;
            window.open(whatsappUrl, '_blank');
            showAlert('تم تجهيز طلبك بنجاح! سيتم الآن فتح واتساب لإتمام الإرسال.', 'تم بنجاح');
        }

        // --- IMAGE GENERATION ---
        function showImageModal() {
            App.elements.imageModal.classList.remove('opacity-0', 'pointer-events-none');
            App.elements.imageModalContent.classList.remove('scale-95', 'opacity-0');
        }

        function hideImageModal() {
            App.elements.imageModalContent.classList.add('scale-95', 'opacity-0');
            App.elements.imageModal.classList.add('opacity-0');
            setTimeout(() => App.elements.imageModal.classList.add('pointer-events-none'), 300);
        }

        function generateImagePrompt() {
            const config = getFullConfiguration();

            let includedItems = [];
            if (config.includeCloset) includedItems.push('closet');
            if (config.includeBed) includedItems.push('bed');
            if (config.includeDresser) includedItems.push('dresser');
            if (config.includeTvTable) includedItems.push('tv_table');
            if (config.includeCoffeeTable) includedItems.push('coffee_table');

            if (includedItems.length === 0) {
                return null;
            }

            let parts = [];
            const productBasePrompt = "A photorealistic, professional product photograph of a piece of modern, luxurious furniture, studio lighting, on a plain light grey background.";
            const roomBasePrompt = "A photorealistic, professional interior design photograph of a modern, luxurious room.";
            
            if (includedItems.length === 1) {
                parts.push(productBasePrompt);
                const item = includedItems[0];
                
                if (item === 'closet') {
                    const woodMap = { counter: 'light oak veneer', sandwich_hpl: 'modern HPL panels', hpl_separate: 'high-pressure laminate with a wood grain texture' };
                    let desc = `The subject is a custom-built wardrobe, ${config.closet.width}cm wide, made of rich ${woodMap[config.closet.woodType]}.`;
                    if (config.closet.mechanism) desc += ` The doors are ${config.closet.mechanism}.`;
                    if (config.closet.glassDoors > 0) desc += ` with ${config.closet.glassDoors} elegant glass panel doors.`;
                    if (config.closet.hasLed) desc += " Subtle integrated LED lighting illuminates the interior.";
                    parts.push(desc);
                }
                if (item === 'bed') {
                    const materialMap = { wood: 'with a solid wood frame.', upholstered_back: 'with a plush, upholstered headboard in a neutral fabric.', upholstered_full: 'fully upholstered in a luxurious, soft-touch fabric.' };
                    const bedCount = config.bed.count;
                    let desc = '';
                    if (bedCount === 1) {
                        desc = `The subject is a single large (${config.bed.size}cm) bed ${materialMap[config.bed.material]}.`;
                    } else if (bedCount === 2) {
                        desc = `The subject is two twin beds, each (${config.bed.size}cm), ${materialMap[config.bed.material]} placed neatly in the room.`;
                    } else {
                         desc = `The subject is a room with ${bedCount} beds, each (${config.bed.size}cm), ${materialMap[config.bed.material]}.`;
                    }
                    if (config.bed.hasLed) desc += " A soft LED glow emanates from under the bed frame(s).";
                    parts.push(desc);
                    if (config.komod.count > 0) {
                        parts.push(`The scene includes ${config.komod.count} matching nightstands (komod).`);
                    }
                }
                if (item === 'dresser') {
                    let desc = `The subject is a modern dresser, ${config.dresser.width}cm wide.`;
                    let mirrorDesc = `Above it hangs a ${config.dresser.mirrorShape} mirror`;
                    if(config.dresser.hasMirrorLed) mirrorDesc += " backlit with warm LED light.";
                    parts.push(desc, mirrorDesc);
                }
                if (item === 'tv_table') {
                    parts.push(`The subject is a sleek, low-profile TV unit, ${config.tvTable.width}cm wide, with ${config.tvTable.drawers} drawers.`);
                }
                if (item === 'coffee_table') {
                    parts.push(`The subject is a modern coffee table, ${config.coffeeTable.width}cm wide and ${config.coffeeTable.depth}cm deep.`);
                }
            } else { // Multiple items
                parts.push(roomBasePrompt);
                const roomSizeMap = { small: "The room is a cozy and well-organized master bedroom.", medium: "The room is a spacious and airy master bedroom.", large: "The room is an expansive and grand master bedroom." };
                parts.push(roomSizeMap[config.roomSize] || '');

                if (config.includeCloset) {
                    const woodMap = { counter: 'light oak veneer', sandwich_hpl: 'modern HPL panels', hpl_separate: 'high-pressure laminate with a wood grain texture' };
                    let desc = `The room features a custom-built wardrobe, ${config.closet.width}cm wide, made of rich ${woodMap[config.closet.woodType]}.`;
                    if (config.closet.mechanism) desc += ` The doors are ${config.closet.mechanism}.`;
                    if (config.closet.glassDoors > 0) desc += ` with ${config.closet.glassDoors} elegant glass panel doors.`;
                    if (config.closet.hasLed) desc += " Subtle integrated LED lighting illuminates the interior.";
                    parts.push(desc);
                }
                if (config.includeBed) {
                     const materialMap = { wood: 'with a solid wood frame.', upholstered_back: 'with a plush, upholstered headboard in a neutral fabric.', upholstered_full: 'fully upholstered in a luxurious, soft-touch fabric.' };
                     const bedCount = config.bed.count;
                     let desc = '';
                     if (bedCount === 1) {
                        desc = `The centerpiece is a single large (${config.bed.size}cm) bed ${materialMap[config.bed.material]}.`;
                     } else if (bedCount === 2) {
                        desc = `The room contains two twin beds, each (${config.bed.size}cm), ${materialMap[config.bed.material]} placed neatly side-by-side.`;
                     } else {
                        desc = `The room is arranged to accommodate ${bedCount} beds, each (${config.bed.size}cm), ${materialMap[config.bed.material]}.`;
                     }
                     if (config.bed.hasLed) desc += " A soft LED glow emanates from under the bed frame(s).";
                     parts.push(desc);
                     if (config.komod.count > 0) {
                        parts.push(`The beds are flanked by ${config.komod.count} matching nightstands (komod).`);
                     }
                }
                 if (config.includeDresser) {
                    let desc = `There is a matching dresser, ${config.dresser.width}cm wide.`;
                    let mirrorDesc = `Above it hangs a ${config.dresser.mirrorShape} mirror`;
                    if(config.dresser.hasMirrorLed) mirrorDesc += " backlit with warm LED light.";
                    parts.push(desc, mirrorDesc);
                }
                if (config.includeTvTable) {
                    parts.push(`The room also contains a sleek, low-profile TV unit, ${config.tvTable.width}cm wide, with ${config.tvTable.drawers} drawers.`);
                }
                if (config.includeCoffeeTable) {
                     parts.push(`The room has a modern coffee table, ${config.coffeeTable.width}cm wide and ${config.coffeeTable.depth}cm deep.`);
                }
            }
            
            parts.push("The styling is minimalist yet sophisticated, with high-end finishes, soft textiles, and a neutral color palette of beige, grey, and cream.", "The lighting is warm and inviting, creating a relaxing ambiance.", "Shot with a 35mm lens, f/1.8, cinematic lighting.");
            
            return parts.filter(p => p).join(' ');
        }

        async function generateImage() {
            const userPrompt = generateImagePrompt();
            if (!userPrompt) {
                showAlert("الرجاء اختيار قطعة أثاث واحدة على الأقل لتوليد صورة لها.");
                return;
            }
            
            showImageModal();
            App.elements.imageLoadingSpinner.classList.remove('hidden');
            App.elements.generatedImage.classList.add('hidden');

            const apiKey = ""; 
            const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/imagen-3.0-generate-002:predict?key=${apiKey}`;
            const payload = { instances: [{ prompt: userPrompt }], parameters: { "sampleCount": 1 } };

            try {
                const response = await fetch(apiUrl, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify(payload)
                });
                if (!response.ok) throw new Error(`HTTP error! status: ${response.status}`);
                
                const result = await response.json();
                if (result.predictions && result.predictions.length > 0 && result.predictions[0].bytesBase64Encoded) {
                    const imageUrl = `data:image/png;base64,${result.predictions[0].bytesBase64Encoded}`;
                    App.elements.generatedImage.src = imageUrl;
                    App.elements.imageLoadingSpinner.classList.add('hidden');
                    App.elements.generatedImage.classList.remove('hidden');
                } else {
                    throw new Error("No image data in API response.");
                }
            } catch (error) {
                console.error("Image generation failed:", error);
                hideImageModal();
                showAlert("عذراً، حدث خطأ أثناء توليد الصورة. الرجاء المحاولة مرة أخرى.");
            }
        }
        
        // --- INITIALIZATION ---
        function initialize() {
            App.elements = {
                userIdDisplay: $('#user-id-display'), footer: $('footer'), totalPrice: $('#total-price'), priceErrorMessage: $('#price-error-message'),
                requestQuoteBtn: $('#request-quote-btn'), showQuoteBtn: $('#show-quote-btn'), generateImageBtn: $('#generate-image-btn'),
                customerName: $('#customer-name'), customerPhone: $('#customer-phone'), roomSize: $('#room-size'),
                includeCloset: $('#include-closet'), includeBed: $('#include-bed'), includeDresser: $('#include-dresser'),
                closetWoodType: $('#closet-wood-type'), closetWidth: $('#closet-width'), closetHeight: $('#closet-height'), closetDepth: $('#closet-depth'), closetDoors: $('#closet-doors'), closetGlassDoors: $('#closet-glass-doors'), closetInternalDrawers: $('#closet-internal-drawers'), doorMechanism: $('#door-mechanism'), closetShelves: $('#closet-shelves'), closetLed: $('#closet-led'),
                bedCount: $('#bed-count'), bedSize: $('#bed-size'), bedMaterial: $('#bed-material'), liftingMechanism: $('#lifting-mechanism'), bedLed: $('#bed-led'),
                komodCount: $('#komod-count'), komodDrawers: $('#komod-drawers'),
                dresserType: $('#dresser-type'), dresserDrawers: $('#dresser-drawers'), dresserWidth: $('#dresser-width'), dresserDepth: $('#dresser-depth'),
                mirrorShape: $('#mirror-shape'), mirrorWidth: $('#mirror-width'), mirrorHeight: $('#mirror-height'), mirrorLed: $('#mirror-led'),
                includeTvTable: $('#include-tv-table'), tvTableWidth: $('#tv-table-width'), tvTableHeight: $('#tv-table-height'), tvTableDepth: $('#tv-table-depth'), tvTableDrawers: $('#tv-table-drawers'),
                includeCoffeeTable: $('#include-coffee-table'), coffeeTableWidth: $('#coffee-table-width'), coffeeTableHeight: $('#coffee-table-height'), coffeeTableDepth: $('#coffee-table-depth'),
                alertModal: $('#alert-modal'), modalContent: $('#alert-modal .modal-content'), modalTitle: $('#modal-title'), modalMessage: $('#modal-message'), modalCloseBtn: $('#modal-close-btn'),
                imageModal: $('#image-modal'), imageModalContent: $('#image-modal .modal-content'), imageModalCloseBtn: $('#image-modal-close-btn'), imageLoadingSpinner: $('#image-loading-spinner'), generatedImage: $('#generated-image')
            };

            // Event listeners
            $$('#configurator-form input, #configurator-form select').forEach(el => el.addEventListener('change', updateUI));
            App.elements.roomSize.addEventListener('change', updateDimensionsBasedOnSize);
            App.elements.showQuoteBtn.addEventListener('click', showQuoteFooter);
            App.elements.requestQuoteBtn.addEventListener('click', submitQuote);
            App.elements.generateImageBtn.addEventListener('click', generateImage);
            $$('#customer-name, #customer-phone').forEach(el => el.addEventListener('input', updateUI));
            App.elements.modalCloseBtn.addEventListener('click', hideAlert);
            App.elements.alertModal.addEventListener('click', e => { if (e.target === App.elements.alertModal) hideAlert(); });
            App.elements.imageModalCloseBtn.addEventListener('click', hideImageModal);
            App.elements.imageModal.addEventListener('click', e => { if (e.target === App.elements.imageModal) hideImageModal(); });

            // Firebase Init
            const firebaseConfig = typeof __firebase_config !== 'undefined' && __firebase_config ? JSON.parse(__firebase_config) : null;
            if (firebaseConfig && Object.keys(firebaseConfig).length > 0) {
                try {
                    const app = initializeApp(firebaseConfig);
                    App.auth = getAuth(app);
                    onAuthStateChanged(App.auth, async (user) => {
                        if (user) { App.currentUserId = user.uid; } 
                        else {
                            const initialAuthToken = typeof __initial_auth_token !== 'undefined' ? __initial_auth_token : null;
                            const signedInUser = initialAuthToken ? await signInWithCustomToken(App.auth, initialAuthToken) : await signInAnonymously(App.auth);
                            App.currentUserId = signedInUser.user.uid;
                        }
                        App.elements.userIdDisplay.textContent = App.currentUserId || 'غير معروف';
                    });
                } catch (e) {
                    console.error("Firebase initialization failed:", e);
                    App.elements.userIdDisplay.textContent = "فشل الاتصال";
                }
            } else { App.elements.userIdDisplay.textContent = "الإعدادات غير متوفرة"; }

            updateUI();
            updateDimensionsBasedOnSize();
        }

        // Helper to get all form values for calculation/submission
        function getFullConfiguration() {
            const elements = App.elements;
            return {
                includeCloset: elements.includeCloset.checked, includeBed: elements.includeBed.checked, includeDresser: elements.includeDresser.checked, includeTvTable: elements.includeTvTable.checked, includeCoffeeTable: elements.includeCoffeeTable.checked, roomSize: elements.roomSize.value,
                closet: { woodType: elements.closetWoodType.value, paintType: $('#closet-paint-type').value || 'none', width: parseFloat(elements.closetWidth.value) || 0, height: parseFloat(elements.closetHeight.value) || 0, depth: parseFloat(elements.closetDepth.value) || 0, doors: parseInt(elements.closetDoors.value) || 0, glassDoors: parseInt(elements.closetGlassDoors.value) || 0, internalDrawers: parseInt(elements.closetInternalDrawers.value) || 0, mechanism: elements.doorMechanism.value, shelves: parseInt(elements.closetShelves.value) || 0, hasLed: elements.closetLed.checked },
                bed: { count: parseInt(elements.bedCount.value) || 0, size: parseInt(elements.bedSize.value) || 0, material: elements.bedMaterial.value, paintType: $('#bed-paint-type').value || 'none', hasLiftingMechanism: elements.liftingMechanism.checked, hasLed: elements.bedLed.checked },
                komod: { count: parseInt(elements.komodCount.value) || 0, drawers: parseInt(elements.komodDrawers.value) || 0 },
                dresser: { type: elements.dresserType.value, drawers: parseInt(elements.dresserDrawers.value) || 0, width: parseFloat(elements.dresserWidth.value) || 0, depth: parseFloat(elements.dresserDepth.value) || 0, mirrorWidth: parseFloat(elements.mirrorWidth.value) || 0, mirrorHeight: parseFloat(elements.mirrorHeight.value) || 0, mirrorShape: elements.mirrorShape.value, hasMirrorLed: elements.mirrorLed.checked },
                tvTable: { width: parseFloat(elements.tvTableWidth.value) || 0, height: parseFloat(elements.tvTableHeight.value) || 0, depth: parseFloat(elements.tvTableDepth.value) || 0, drawers: parseInt(elements.tvTableDrawers.value) || 0 },
                coffeeTable: { width: parseFloat(elements.coffeeTableWidth.value) || 0, height: parseFloat(elements.coffeeTableHeight.value) || 0, depth: parseFloat(elements.coffeeTableDepth.value) || 0 }
            };
        }
        
        document.addEventListener('DOMContentLoaded', initialize);
    </script>
</body>
</html>


