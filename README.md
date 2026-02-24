# Naijaflip-
Domain sales
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>NaijaFlip | Premium Domain Marketplace</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&display=swap" rel="stylesheet">
    <!-- Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: { sans: ['Inter', 'sans-serif'] },
                    colors: {
                        brand: { 500: '#0ea5e9', 600: '#0284c7' },
                        dark: { 900: '#0f172a', 800: '#1e293b', 700: '#334155' }
                    }
                }
            }
        }
    </script>
    <style>
        body { background-color: #0f172a; color: #f8fafc; -webkit-tap-highlight-color: transparent; }
        .glass-panel { background: rgba(30, 41, 59, 0.7); backdrop-filter: blur(10px); border: 1px solid rgba(255, 255, 255, 0.1); }
        .view-section { display: none; animation: fadeIn 0.3s ease-in-out; }
        .view-section.active { display: block; }
        @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }
        /* Hide Scrollbar for clean look */
        .no-scrollbar::-webkit-scrollbar { display: none; }
        .no-scrollbar { -ms-overflow-style: none; scrollbar-width: none; }
    </style>
</head>
<body class="antialiased min-h-screen flex flex-col">

    <!-- Navbar -->
    <nav class="glass-panel sticky top-0 z-50 border-b border-gray-700">
        <div class="max-w-7xl mx-auto px-4 h-16 flex items-center justify-between">
            <div class="flex items-center gap-2 cursor-pointer" onclick="switchTab('home')">
                <div class="w-8 h-8 bg-brand-500 rounded-lg flex items-center justify-center">
                    <i class="fa-solid fa-layer-group text-white text-sm"></i>
                </div>
                <span class="font-bold text-xl tracking-tight text-white">Naija<span class="text-brand-500">Flip</span></span>
            </div>
            <!-- Desktop Menu -->
            <div class="hidden md:flex space-x-6">                <button onclick="switchTab('home')" class="text-gray-300 hover:text-white font-medium">Marketplace</button>
                <button onclick="switchTab('sell')" class="text-gray-300 hover:text-white font-medium">Sell Domain</button>
                <button onclick="switchTab('contact')" class="text-gray-300 hover:text-white font-medium">Contact</button>
            </div>
        </div>
    </nav>

    <!-- MAIN CONTENT AREA -->
    <main class="flex-grow">

        <!-- ================= VIEW: HOME (MARKETPLACE) ================= -->
        <div id="home-view" class="view-section active">
            <!-- Hero -->
            <div class="px-4 py-12 text-center">
                <h1 class="text-3xl md:text-5xl font-bold text-white mb-4">Secure Your <span class="text-brand-500">Digital Identity</span></h1>
                <p class="text-gray-400 mb-8">Premium .ng domains for Nigerian Startups.</p>
                
                <!-- Search -->
                <div class="max-w-md mx-auto relative">
                    <i class="fa-solid fa-search absolute left-4 top-3.5 text-gray-500"></i>
                    <input type="text" id="searchInput" class="w-full bg-dark-800 border border-gray-700 text-white pl-12 pr-4 py-3 rounded-xl focus:outline-none focus:border-brand-500" placeholder="Search domains...">
                </div>
            </div>

            <!-- Filters -->
            <div class="px-4 mb-6 overflow-x-auto no-scrollbar">
                <div class="flex space-x-2 min-w-max" id="filterContainer">
                    <button onclick="filterDomains('all')" class="filter-btn bg-brand-600 text-white px-4 py-1.5 rounded-full text-sm font-medium">All</button>
                    <button onclick="filterDomains('AI')" class="filter-btn bg-dark-800 text-gray-400 border border-gray-700 px-4 py-1.5 rounded-full text-sm">AI & Tech</button>
                    <button onclick="filterDomains('Fintech')" class="filter-btn bg-dark-800 text-gray-400 border border-gray-700 px-4 py-1.5 rounded-full text-sm">Fintech</button>
                    <button onclick="filterDomains('E-commerce')" class="filter-btn bg-dark-800 text-gray-400 border border-gray-700 px-4 py-1.5 rounded-full text-sm">E-commerce</button>
                </div>
            </div>

            <!-- Grid -->
            <div class="max-w-7xl mx-auto px-4 pb-24">
                <div id="domainGrid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
                    <!-- Items injected via JS -->
                </div>
                <div id="emptyState" class="hidden text-center py-12 text-gray-500">No domains found.</div>
            </div>
        </div>

        <!-- ================= VIEW: CHECKOUT ================= -->
        <div id="checkout-view" class="view-section">
            <div class="max-w-md mx-auto px-4 py-8">
                <!-- Back Button -->
                <button onclick="switchTab('home')" class="flex items-center text-gray-400 hover:text-white mb-6">
                    <i class="fa-solid fa-arrow-left mr-2"></i> Back to Marketplace
                </button>
                <div class="glass-panel rounded-2xl p-6 border border-gray-700">
                    <h2 class="text-2xl font-bold text-white mb-1">Checkout</h2>
                    <p class="text-gray-400 text-sm mb-6">Complete your purchase securely.</p>

                    <!-- Order Summary -->
                    <div class="bg-dark-900 rounded-xl p-4 mb-6 border border-gray-800">
                        <div class="flex justify-between items-center mb-2">
                            <span class="text-gray-400">Domain Name</span>
                            <span id="checkout-domain" class="text-white font-bold text-right">...</span>
                        </div>
                        <div class="flex justify-between items-center mb-2">
                            <span class="text-gray-400">Transfer Fee</span>
                            <span class="text-white">₦0.00</span>
                        </div>
                        <div class="border-t border-gray-700 my-3"></div>
                        <div class="flex justify-between items-center">
                            <span class="text-gray-300 font-medium">Total</span>
                            <span id="checkout-total" class="text-brand-500 font-bold text-xl">₦0.00</span>
                        </div>
                    </div>

                    <!-- Payment Instructions -->
                    <div class="mb-6">
                        <h3 class="text-sm font-semibold text-gray-300 uppercase mb-3">Payment Method</h3>
                        <div class="bg-blue-900/20 border border-blue-800 rounded-lg p-4">
                            <div class="flex items-start gap-3">
                                <i class="fa-solid fa-building-columns text-blue-400 mt-1"></i>
                                <div>
                                    <p class="text-sm text-blue-100 font-bold">Bank Transfer</p>
                                    <p class="text-xs text-blue-200 mt-1">Opay / Moniepoint</p>
                                    <p class="text-lg text-white font-mono mt-1">9012345678</p>
                                    <p class="text-xs text-blue-200">NaijaFlip Ventures</p>
                                </div>
                            </div>
                        </div>
                        <p class="text-xs text-gray-500 mt-2 text-center">After transfer, click "Confirm Payment" to send proof via WhatsApp.</p>
                    </div>

                    <!-- Action Button -->
                    <button onclick="confirmPayment()" class="w-full bg-green-600 hover:bg-green-500 text-white font-bold py-4 rounded-xl shadow-lg shadow-green-900/20 transition transform active:scale-95">
                        <i class="fa-brands fa-whatsapp mr-2"></i> Confirm Payment
                    </button>
                </div>
            </div>
        </div>

        <!-- ================= VIEW: SELL DOMAIN ================= -->
        <div id="sell-view" class="view-section">
            <div class="max-w-md mx-auto px-4 py-8">                <button onclick="switchTab('home')" class="flex items-center text-gray-400 hover:text-white mb-6">
                    <i class="fa-solid fa-arrow-left mr-2"></i> Back
                </button>
                
                <h2 class="text-2xl font-bold text-white mb-2">Sell Your Domain</h2>
                <p class="text-gray-400 text-sm mb-6">Have a premium .ng domain? List it with us.</p>

                <form onsubmit="handleSellSubmit(event)" class="glass-panel p-6 rounded-2xl space-y-4">
                    <div>
                        <label class="block text-sm text-gray-400 mb-1">Domain Name</label>
                        <input type="text" required placeholder="e.g. LagosTech.com.ng" class="w-full bg-dark-900 border border-gray-700 rounded-lg p-3 text-white focus:border-brand-500 focus:outline-none">
                    </div>
                    <div>
                        <label class="block text-sm text-gray-400 mb-1">Asking Price (₦)</label>
                        <input type="number" required placeholder="e.g. 50000" class="w-full bg-dark-900 border border-gray-700 rounded-lg p-3 text-white focus:border-brand-500 focus:outline-none">
                    </div>
                    <div>
                        <label class="block text-sm text-gray-400 mb-1">Your WhatsApp Number</label>
                        <input type="tel" required placeholder="080..." class="w-full bg-dark-900 border border-gray-700 rounded-lg p-3 text-white focus:border-brand-500 focus:outline-none">
                    </div>
                    <button type="submit" class="w-full bg-brand-600 hover:bg-brand-500 text-white font-bold py-3 rounded-lg mt-4">Submit Listing</button>
                </form>
            </div>
        </div>

        <!-- ================= VIEW: CONTACT ================= -->
        <div id="contact-view" class="view-section">
            <div class="max-w-md mx-auto px-4 py-12 text-center">
                <div class="w-20 h-20 bg-dark-800 rounded-full flex items-center justify-center mx-auto mb-6">
                    <i class="fa-solid fa-headset text-3xl text-brand-500"></i>
                </div>
                <h2 class="text-2xl font-bold text-white mb-2">Need Help?</h2>
                <p class="text-gray-400 mb-8">Our support team is available 24/7 to assist with transfers and payments.</p>
                
                <div class="space-y-4">
                    <a href="https://wa.me/2348000000000" class="block w-full bg-green-600/10 border border-green-600/30 text-green-400 py-3 rounded-lg font-medium hover:bg-green-600/20 transition">
                        <i class="fa-brands fa-whatsapp mr-2"></i> Chat on WhatsApp
                    </a>
                    <a href="mailto:support@naijaflip.ng" class="block w-full bg-dark-800 border border-gray-700 text-gray-300 py-3 rounded-lg font-medium hover:bg-gray-700 transition">
                        <i class="fa-solid fa-envelope mr-2"></i> Email Support
                    </a>
                </div>
            </div>
        </div>

    </main>

    <!-- Mobile Bottom Navigation -->
    <div class="md:hidden fixed bottom-0 w-full glass-panel border-t border-gray-700 flex justify-around py-3 z-50 pb-safe">
        <button onclick="switchTab('home')" class="nav-btn active flex flex-col items-center text-brand-500">            <i class="fa-solid fa-store text-xl mb-1"></i>
            <span class="text-xs">Buy</span>
        </button>
        <button onclick="switchTab('sell')" class="nav-btn flex flex-col items-center text-gray-500 hover:text-gray-300">
            <i class="fa-solid fa-plus-circle text-xl mb-1"></i>
            <span class="text-xs">Sell</span>
        </button>
        <button onclick="switchTab('contact')" class="nav-btn flex flex-col items-center text-gray-500 hover:text-gray-300">
            <i class="fa-solid fa-user text-xl mb-1"></i>
            <span class="text-xs">Profile</span>
        </button>
    </div>

    <!-- JavaScript Logic -->
    <script>
        // --- DATA ---
        const domains = [
            { id: 1, name: "LagosAI.com.ng", category: "AI", price: 25000, tag: "Hot" },
            { id: 2, name: "PaySwift.ng", category: "Fintech", price: 45000, tag: "Premium" },
            { id: 3, name: "NaijaShop.com.ng", category: "E-commerce", price: 15000, tag: null },
            { id: 4, name: "AbujaTech.com.ng", category: "AI", price: 18000, tag: null },
            { id: 5, name: "Zenvo.ng", category: "Brandable", price: 35000, tag: "Short" },
            { id: 6, name: "CryptoNg.com.ng", category: "Fintech", price: 22000, tag: null },
            { id: 7, name: "FarmConnect.ng", category: "E-commerce", price: 20000, tag: "Agro" },
            { id: 8, name: "DataFlow.com.ng", category: "AI", price: 15000, tag: null }
        ];

        let currentCart = null;
        const MY_PHONE = "2348000000000"; // REPLACE WITH YOUR NUMBER

        // --- NAVIGATION ---
        function switchTab(tabId) {
            // Hide all views
            document.querySelectorAll('.view-section').forEach(el => el.classList.remove('active'));
            // Show target view
            document.getElementById(tabId + '-view').classList.add('active');
            
            // Update Mobile Nav Icons
            document.querySelectorAll('.nav-btn').forEach(btn => {
                btn.classList.remove('text-brand-500');
                btn.classList.add('text-gray-500');
            });
            
            // Highlight active nav (simple logic based on order)
            if(tabId === 'home') document.querySelectorAll('.nav-btn')[0].classList.replace('text-gray-500', 'text-brand-500');
            if(tabId === 'sell') document.querySelectorAll('.nav-btn')[1].classList.replace('text-gray-500', 'text-brand-500');
            if(tabId === 'contact') document.querySelectorAll('.nav-btn')[2].classList.replace('text-gray-500', 'text-brand-500');

            window.scrollTo(0,0);
        }
        // --- RENDER DOMAINS ---
        function renderDomains(data) {
            const grid = document.getElementById('domainGrid');
            grid.innerHTML = '';
            
            if(data.length === 0) {
                document.getElementById('emptyState').classList.remove('hidden');
                return;
            }
            document.getElementById('emptyState').classList.add('hidden');

            data.forEach(d => {
                const tagHtml = d.tag ? `<span class="absolute top-3 right-3 bg-brand-600 text-white text-[10px] font-bold px-2 py-1 rounded uppercase">${d.tag}</span>` : '';
                grid.innerHTML += `
                    <div class="glass-panel rounded-xl p-5 relative border border-gray-700 flex flex-col justify-between">
                        ${tagHtml}
                        <div>
                            <p class="text-xs text-brand-400 font-semibold mb-1">${d.category}</p>
                            <h3 class="text-lg font-bold text-white mb-1">${d.name}</h3>
                        </div>
                        <div class="mt-4 flex items-center justify-between">
                            <span class="text-emerald-400 font-bold">₦${d.price.toLocaleString()}</span>
                            <button onclick="initiateCheckout(${d.id})" class="bg-white text-dark-900 px-3 py-1.5 rounded-lg text-xs font-bold hover:bg-gray-200">Buy</button>
                        </div>
                    </div>
                `;
            });
        }

        // --- FILTER & SEARCH ---
        function filterDomains(cat) {
            // Visual update for buttons
            document.querySelectorAll('.filter-btn').forEach(b => {
                b.classList.remove('bg-brand-600', 'text-white');
                b.classList.add('bg-dark-800', 'text-gray-400');
                if((cat === 'all' && b.innerText === 'All') || b.innerText.includes(cat)) {
                    b.classList.remove('bg-dark-800', 'text-gray-400');
                    b.classList.add('bg-brand-600', 'text-white');
                }
            });

            if(cat === 'all') renderDomains(domains);
            else renderDomains(domains.filter(d => d.category === cat));
        }

        document.getElementById('searchInput').addEventListener('input', (e) => {
            const term = e.target.value.toLowerCase();
            renderDomains(domains.filter(d => d.name.toLowerCase().includes(term)));
        });
        // --- CHECKOUT LOGIC ---
        function initiateCheckout(id) {
            const domain = domains.find(d => d.id === id);
            currentCart = domain;
            
            // Populate Checkout View
            document.getElementById('checkout-domain').innerText = domain.name;
            document.getElementById('checkout-total').innerText = '₦' + domain.price.toLocaleString();
            
            switchTab('checkout');
        }

        function confirmPayment() {
            if(!currentCart) return;
            const msg = `Hello NaijaFlip, I just made a transfer for *${currentCart.name}* (₦${currentCart.price}). Please confirm and initiate transfer.`;
            window.open(`https://wa.me/${MY_PHONE}?text=${encodeURIComponent(msg)}`, '_blank');
        }

        // --- SELL FORM LOGIC ---
        function handleSellSubmit(e) {
            e.preventDefault();
            const inputs = e.target.querySelectorAll('input');
            const domainName = inputs[0].value;
            const price = inputs[1].value;
            
            const msg = `Hi, I want to sell my domain *${domainName}* for ₦${price}. Here are my details.`;
            window.open(`https://wa.me/${MY_PHONE}?text=${encodeURIComponent(msg)}`, '_blank');
        }

        // Initialize
        renderDomains(domains);
    </script>
</body>
</html>
