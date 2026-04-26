<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Material Rates 2025 - Chattogram</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
            overflow: hidden;
        }

        .header {
            background: linear-gradient(135deg, #ff6b6b, #feca57);
            color: white;
            padding: 30px;
            text-align: center;
        }

        .header h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        .header p {
            font-size: 1.2em;
            opacity: 0.9;
        }

        .location-info {
            background: #4ecdc4;
            padding: 20px;
            text-align: center;
            color: white;
        }

        .location-info h2 {
            font-size: 1.8em;
            margin-bottom: 10px;
        }

        .materials-grid {
            padding: 40px;
        }

        .material-card {
            background: #f8f9fa;
            border-radius: 15px;
            padding: 25px;
            margin-bottom: 25px;
            border-left: 5px solid #ff6b6b;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0,0,0,0.08);
        }

        .material-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(0,0,0,0.15);
        }

        .material-name {
            font-size: 1.4em;
            font-weight: bold;
            color: #2c3e50;
            margin-bottom: 10px;
        }

        .rate-info {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 15px;
        }

        .price {
            font-size: 1.8em;
            font-weight: bold;
            color: #27ae60;
        }

        .unit {
            color: #7f8c8d;
            font-size: 1.1em;
        }

        .update-info {
            background: #3498db;
            color: white;
            padding: 8px 15px;
            border-radius: 20px;
            font-size: 0.9em;
            margin-top: 15px;
        }

        .search-box {
            padding: 20px 40px;
            background: #ecf0f1;
            text-align: center;
        }

        .search-input {
            width: 100%;
            max-width: 500px;
            padding: 15px 25px;
            border: 2px solid #bdc3c7;
            border-radius: 50px;
            font-size: 1.1em;
            outline: none;
            transition: all 0.3s ease;
        }

        .search-input:focus {
            border-color: #3498db;
            box-shadow: 0 0 20px rgba(52, 152, 219, 0.3);
        }

        @media (max-width: 768px) {
            .materials-grid {
                padding: 20px;
            }
            
            .material-card {
                padding: 20px;
            }
            
            .rate-info {
                flex-direction: column;
                text-align: center;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>🏗️ Material Rates 2025</h1>
            <p>চট্টগ্রাম বিভাগ - সর্বশেষ রেট লিস্ট</p>
        </div>

        <div class="location-info">
            <h2>📍 Chattogram Division</h2>
            <p>Updated: January 2025 | All prices in BDT</p>
        </div>

        <div class="search-box">
            <input type="text" class="search-input" placeholder="🔍 Search materials (e.g., Cement, Rod, Brick)..." onkeyup="searchMaterials(this.value)">
        </div>

        <div class="materials-grid" id="materialsContainer">
            <!-- 24 Materials will be populated by JavaScript -->
        </div>
    </div>

    <script>
        const materials = [
            { name: "Portland Cement (50kg)", price: 580, unit: "/bag", category: "cement" },
            { name: "OPC Cement (50kg)", price: 560, unit: "/bag", category: "cement" },
            { name: "Sand (Fine)", price: 1850, unit: "/CFT", category: "sand" },
            { name: "Sand (Medium)", price: 1750, unit: "/CFT", category: "sand" },
            { name: "Sand (Brick)", price: 1650, unit: "/CFT", category: "sand" },
            { name: "60 Grade Rod (12mm)", price: 7800, unit: "/ton", category: "rod" },
            { name: "60 Grade Rod (16mm)", price: 7850, unit: "/ton", category: "rod" },
            { name: "60 Grade Rod (20mm)", price: 7900, unit: "/ton", category: "rod" },
            { name: "Red Brick", price: 7.5, unit: "/piece", category: "brick" },
            { name: "English Brick", price: 12, unit: "/piece", category: "brick" },
            { name: "Crushed Stone (1\")", price: 2200, unit: "/CFT", category: "stone" },
            { name: "Crushed Stone (1.5\")", price: 2150, unit: "/CFT", category: "stone" },
            { name: "Crushed Stone Dust", price: 1450, unit: "/CFT", category: "stone" },
            { name: "Stone Chips (20mm)", price: 2350, unit: "/CFT", category: "chips" },
            { name: "Stone Chips (10mm)", price: 2400, unit: "/CFT", category: "chips" },
            { name: "PVC Pipe (1\")", price: 145, unit: "/piece (6ft)", category: "pipe" },
            { name: "PVC Pipe (2\")", price: 285, unit: "/piece (6ft)", category: "pipe" },
            { name: "M.S. Angle (3x3\")", price: 125000, unit: "/ton", category: "steel" },
            { name: "M.S. Flat Bar (40x5mm)", price: 115000, unit: "/ton", category: "steel" },
            { name: "Binding Wire", price: 125, unit: "/kg", category: "wire" },
            { name: "C.I. Manhole Cover (18\")", price: 2850, unit: "/piece", category: "cover" },
            { name: "Plywood (4x8ft, 12mm)", price: 4200, unit: "/sheet", category: "plywood" },
            { name: "G.I. Pipe (1\")", price: 245, unit: "/piece (12ft)", category: "pipe" },
            { name: "Electrical Wire (2.5mm)", price: 145, unit: "/100m", category: "electrical" }
        ];

        function createMaterialCard(material) {
            return `
                <div class="material-card" data-category="${material.category}">
                    <div class="material-name">${material.name}</div>
                    <div class="rate-info">
                        <div class="price">৳ ${material.price.toLocaleString()}</div>
                        <div class="unit">${material.unit}</div>
                    </div>
                    <div class="update-info">
                        ✅ Chattogram Rate 2025 | Valid till March 2025
                    </div>
                </div>
            `;
        }

        function renderMaterials(materialsToShow = materials) {
            const container = document.getElementById('materialsContainer');
            container.innerHTML = materialsToShow.map(createMaterialCard).join('');
        }

        function searchMaterials(query) {
            const filtered = materials.filter(material => 
                material.name.toLowerCase().includes(query.toLowerCase()) ||
                material.category.includes(query.toLowerCase())
            );
            renderMaterials(filtered);
        }

        // Initialize
        renderMaterials();

        // Add some interactive features
        document.addEventListener('DOMContentLoaded', function() {
            // Add click animation
            document.querySelectorAll('.material-card').forEach(card => {
                card.addEventListener('click', function() {
                    this.style.transform = 'scale(0.98)';
                    setTimeout(() => {
                        this.style.transform = '';
                    }, 150);
                });
            });
        });
    </script>
</body>
</html>
