<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>निर्भया केस (2012) - एक सिंहावलोकन</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+Devanagari:wght@400;500;700&display=swap" rel="stylesheet">
    <!-- Chosen Palette: Warm Neutrals with a Muted Maroon Accent -->
    <!-- Application Structure Plan: एक सिंगल-पेज, स्क्रॉलिंग एप्लिकेशन जिसमें एक स्टिकी नेविगेशन बार है जो उपयोगकर्ताओं को विभिन्न अनुभागों पर जाने की अनुमति देता है: घटना, जांच, एक इंटरैक्टिव न्यायिक प्रक्रिया समयरेखा, दोषी और मामले के स्थायी प्रभाव। यह संरचना उपयोगकर्ता को एक जटिल और संवेदनशील विषय के माध्यम से तार्किक रूप से मार्गदर्शन करने के लिए चुनी गई थी, जो कालानुक्रमिक प्रवाह और विषयगत समूहीकरण का संयोजन करती है। इंटरैक्टिव समयरेखा विशेष रूप से लंबी कानूनी लड़ाई को सुलभ बनाने के लिए डिज़ाइन की गई है। -->
    <!-- Visualization & Content Choices: 
        1. न्यायिक प्रक्रिया: लक्ष्य - एक लंबी और जटिल कानूनी प्रक्रिया को सरल बनाना। विज़/प्रेजेंटेशन - एक क्लिक करने योग्य HTML/CSS समयरेखा। इंटरेक्शन - समयरेखा पर एक बिंदु पर क्लिक करने से नीचे एक विस्तृत सूचना पैनल अपडेट होता है। औचित्य - यह एक बहु-वर्षीय कानूनी मामले को आसानी से खोजे जाने योग्य प्रारूप में तोड़ देता है। लाइब्रेरी/विधि - वेनिला जावास्क्रिप्ट।
        2. प्रभाव और सुधार: लक्ष्य - मामले के सामाजिक-कानूनी परिणामों को दिखाना। विज़/प्रेजेंटेशन - Chart.js बार चार्ट जो 2012 के आसपास के वर्षों में भारत में दर्ज बलात्कार के मामलों को दिखाता है। इंटरेक्शन - प्रत्येक बार पर होवर करने पर सटीक संख्या दिखाने वाले टूलटिप्स। औचित्य - यह बढ़ी हुई रिपोर्टिंग और जागरूकता के माध्यम से मामले के मूर्त प्रभावों में से एक को प्रभावी ढंग से मापता है। लाइब्रेरी/विधि - Chart.js।
        3. दोषी: लक्ष्य - इसमें शामिल व्यक्तियों के बारे में जानकारी व्यवस्थित करना। विज़/प्रेजेंटेशन - प्रत्येक दोषी के लिए जानकारी के साथ HTML/Tailwind कार्ड का एक ग्रिड। इंटरेक्शन - कोई नहीं, केवल स्पष्ट प्रस्तुति। औचित्य - प्रत्येक व्यक्ति से संबंधित जानकारी को स्पष्ट रूप से अलग और प्रस्तुत करता है। लाइब्रेरी/विधि - HTML/CSS। -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <style>
        body {
            font-family: 'Noto Sans Devanagari', sans-serif;
            background-color: #FDFBF8;
            color: #3f3c3a;
        }
        .nav-link {
            transition: all 0.3s ease;
            border-bottom: 2px solid transparent;
        }
        .nav-link.active, .nav-link:hover {
            border-bottom-color: #8c2d2d;
            color: #8c2d2d;
        }
        .timeline-item {
            cursor: pointer;
            transition: all 0.3s ease;
        }
        .timeline-item.active .timeline-dot {
            background-color: #8c2d2d;
            transform: scale(1.25);
        }
        .timeline-item.active .timeline-content {
            color: #8c2d2d;
            font-weight: 700;
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 800px;
            margin-left: auto;
            margin-right: auto;
            height: 400px;
            max-height: 50vh;
        }
        .content-section {
            display: none;
        }
        .content-section.active {
            display: block;
        }
    </style>
</head>
<body class="bg-stone-50 text-stone-800">

    <div class="container mx-auto p-4 md:p-8">
        <header class="text-center mb-8">
            <h1 class="text-4xl md:text-5xl font-bold text-stone-900">निर्भया केस (दिल्ली, 2012)</h1>
            <p class="mt-2 text-lg text-stone-600">एक घटना जिसने भारत को झकझोर दिया और न्याय के लिए एक लंबी लड़ाई शुरू की।</p>
        </header>

        <nav class="sticky top-0 bg-stone-50/80 backdrop-blur-sm z-10 shadow-md rounded-lg mb-8">
            <div class="max-w-5xl mx-auto px-4">
                <div class="flex justify-center items-center space-x-2 md:space-x-8 h-16">
                    <a href="#incident" class="nav-link px-3 py-2 text-sm md:text-base font-medium">घटना</a>
                    <a href="#investigation" class="nav-link px-3 py-2 text-sm md:text-base font-medium">जांच और गिरफ्तारी</a>
                    <a href="#judicial" class="nav-link px-3 py-2 text-sm md:text-base font-medium">न्यायिक प्रक्रिया</a>
                    <a href="#convicts" class="nav-link px-3 py-2 text-sm md:text-base font-medium">दोषी</a>
                    <a href="#impact" class="nav-link px-3 py-2 text-sm md:text-base font-medium">प्रभाव और सुधार</a>
                </div>
            </div>
        </nav>

        <main class="max-w-5xl mx-auto">
            <section id="incident" class="content-section p-6 bg-white rounded-lg shadow-sm">
                <h2 class="text-2xl font-bold mb-4 text-[#8c2d2d]">वह भयावह रात: 16 दिसंबर 2012</h2>
                <p class="text-stone-700 leading-relaxed">
                    16 दिसंबर 2012 की रात, 23 वर्षीय फिजियोथेरेपी इंटर्न, जिसे बाद में 'निर्भया' (निडर) नाम दिया गया, और उनके पुरुष मित्र दक्षिण दिल्ली के मुनिरका में एक निजी बस में चढ़े। बस में ड्राइवर सहित छह लोग पहले से मौजूद थे। उन्होंने जल्द ही युवती के साथ क्रूरतापूर्वक सामूहिक बलात्कार और मारपीट की, और उसके दोस्त पर भी बेरहमी से हमला किया। लगभग एक घंटे की इस भयावहता के बाद, उन्होंने दोनों को चलती बस से महिपालपुर के पास फेंक दिया। इस क्रूर घटना ने पूरे देश में आक्रोश और सदमे की लहर दौड़ा दी, जिससे बड़े पैमाने पर विरोध प्रदर्शन हुए और महिला सुरक्षा पर एक राष्ट्रीय बहस छिड़ गई।
                </p>
            </section>

            <section id="investigation" class="content-section p-6 bg-white rounded-lg shadow-sm">
                <h2 class="text-2xl font-bold mb-4 text-[#8c2d2d]">जांच और गिरफ्तारी</h2>
                <p class="text-stone-700 leading-relaxed mb-4">
                    दिल्ली पुलिस ने मामले की जांच के लिए तुरंत कई टीमें गठित कीं। पीड़ित के मित्र के बयान और बस के आंशिक विवरण के आधार पर, पुलिस ने 300 से अधिक बसों की जांच की। आखिरकार, उन्हें वह बस मिल गई और कुछ ही घंटों में बस के ड्राइवर राम सिंह को गिरफ्तार कर लिया गया।
                </p>
                <ul class="list-disc list-inside space-y-2 text-stone-700">
                    <li><strong>राम सिंह (ड्राइवर):</strong> सबसे पहले गिरफ्तार किया गया।</li>
                    <li><strong>मुकेश सिंह (राम सिंह का भाई):</strong> राजस्थान से गिरफ्तार।</li>
                    <li><strong>विनय शर्मा और पवन गुप्ता:</strong> दिल्ली के झुग्गी-झोपड़ी वाले इलाकों से पकड़े गए।</li>
                    <li><strong>अक्षय कुमार सिंह:</strong> बिहार के औरंगाबाद से गिरफ्तार।</li>
                    <li><strong>एक नाबालिग:</strong> दिल्ली से ही पकड़ा गया, जिसकी उम्र 18 साल से कुछ महीने कम थी।</li>
                </ul>
                <p class="mt-4 text-stone-700 leading-relaxed">
                    पुलिस ने तेजी से काम करते हुए घटना के कुछ ही दिनों के भीतर सभी छह आरोपियों को गिरफ्तार कर लिया, जिससे मामले की न्यायिक प्रक्रिया का रास्ता साफ हो गया।
                </p>
            </section>

            <section id="judicial" class="content-section p-6 bg-white rounded-lg shadow-sm">
                <h2 class="text-2xl font-bold mb-4 text-[#8c2d2d]">न्याय की लंबी राह: एक इंटरैक्टिव समयरेखा</h2>
                 <p class="text-stone-600 mb-6 leading-relaxed">यह खंड सात साल से अधिक चली जटिल न्यायिक प्रक्रिया का अवलोकन प्रदान करता है। न्याय की इस लंबी और कठिन यात्रा के प्रमुख मील के पत्थर देखने के लिए समयरेखा पर किसी भी घटना पर क्लिक करें। प्रत्येक चरण, फास्ट-ट्रैक अदालतों से लेकर अंतिम फैसले तक, भारत की कानूनी प्रणाली के लिए एक महत्वपूर्ण क्षण था।</p>
                <div class="relative wrap overflow-hidden p-4 h-auto">
                    <div class="border-2-2 absolute border-opacity-20 border-stone-700 h-full border" style="left: 50%"></div>
                    <div id="timeline-container" class="flex flex-col space-y-8">
                    </div>
                </div>
                <div id="timeline-details" class="mt-8 p-6 bg-stone-100 rounded-lg min-h-[150px] transition-all duration-300">
                    <h3 id="details-title" class="text-xl font-bold text-stone-800">विवरण देखने के लिए किसी घटना पर क्लिक करें</h3>
                    <p id="details-content" class="mt-2 text-stone-700"></p>
                </div>
            </section>

            <section id="convicts" class="content-section p-6 bg-white rounded-lg shadow-sm">
                <h2 class="text-2xl font-bold mb-4 text-[#8c2d2d]">शामिल दोषी</h2>
                 <p class="text-stone-600 mb-6 leading-relaxed">इस मामले में कुल छह व्यक्ति शामिल थे। प्रत्येक की पहचान की गई और उन पर मुकदमा चलाया गया, लेकिन उनके मामले अलग-अलग तरीकों से समाप्त हुए। यह खंड प्रत्येक दोषी और उनके अंतिम परिणाम का संक्षिप्त विवरण प्रदान करता है, जिसमें कानूनी प्रक्रियाओं और अप्रत्याशित घटनाओं पर प्रकाश डाला गया है, जिन्होंने उनके भाग्य को आकार दिया।</p>
                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                    <div class="bg-stone-100 p-4 rounded-lg shadow">
                        <h3 class="font-bold text-lg text-stone-800">राम सिंह</h3>
                        <p class="text-stone-600">बस का ड्राइवर और मुख्य आरोपी। मार्च 2013 में मुकदमे के दौरान तिहाड़ जेल में मृत पाया गया। अधिकारियों ने इसे आत्महत्या बताया।</p>
                    </div>
                    <div class="bg-stone-100 p-4 rounded-lg shadow">
                        <h3 class="font-bold text-lg text-stone-800">मुकेश सिंह</h3>
                        <p class="text-stone-600">राम सिंह का भाई। अपराध के समय बस चला रहा था। सभी अपीलों और दया याचिकाओं के खारिज होने के बाद, उसे 20 मार्च 2020 को फांसी दे दी गई।</p>
                    </div>
                    <div class="bg-stone-100 p-4 rounded-lg shadow">
                        <h3 class="font-bold text-lg text-stone-800">विनय शर्मा</h3>
                        <p class="text-stone-600">एक जिम प्रशिक्षक। उसे भी मौत की सजा सुनाई गई और 20 मार्च 2020 को फांसी पर लटका दिया गया।</p>
                    </div>
                    <div class="bg-stone-100 p-4 rounded-lg shadow">
                        <h3 class="font-bold text-lg text-stone-800">पवन गुप्ता</h3>
                        <p class="text-stone-600">एक फल विक्रेता। उसे भी मौत की सजा दी गई और 20 मार्च 2020 को फांसी दे दी गई।</p>
                    </div>
                    <div class="bg-stone-100 p-4 rounded-lg shadow">
                        <h3 class="font-bold text-lg text-stone-800">अक्षय कुमार सिंह</h3>
                        <p class="text-stone-600">बस का सहायक। उसकी दया याचिका राष्ट्रपति द्वारा खारिज कर दी गई और उसे 20 मार्च 2020 को फांसी दी गई।</p>
                    </div>
                    <div class="bg-stone-100 p-4 rounded-lg shadow">
                        <h3 class="font-bold text-lg text-stone-800">नाबालिग दोषी</h3>
                        <p class="text-stone-600">अपराध के समय 17 साल का था। उस पर किशोर न्याय अधिनियम के तहत मुकदमा चला और उसे तीन साल के लिए सुधार गृह भेजा गया, जो कि अधिकतम सजा थी। उसे 2015 में रिहा कर दिया गया।</p>
                    </div>
                </div>
            </section>

            <section id="impact" class="content-section p-6 bg-white rounded-lg shadow-sm">
                <h2 class="text-2xl font-bold mb-4 text-[#8c2d2d]">राष्ट्रव्यापी प्रभाव और कानूनी सुधार</h2>
                 <p class="text-stone-600 mb-6 leading-relaxed">निर्भया मामले ने पूरे भारत में अभूतपूर्व विरोध प्रदर्शनों को जन्म दिया और महिला सुरक्षा और यौन हिंसा पर कानूनों की गहन समीक्षा के लिए मजबूर किया। इस खंड में मामले के सामाजिक और कानूनी परिणामों का पता लगाया गया है, जिसमें नए कानून का निर्माण और यौन उत्पीड़न के प्रति दृष्टिकोण में बदलाव शामिल है, जिसे नीचे दिए गए चार्ट में दर्ज मामलों में वृद्धि से देखा जा सकता है।</p>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-8 items-center">
                    <div>
                        <h3 class="font-semibold text-xl mb-2">जनता का आक्रोश और नए कानून</h3>
                        <p class="text-stone-700 leading-relaxed">
                            इस घटना के बाद, हजारों लोग सड़कों पर उतर आए, विशेषकर दिल्ली में इंडिया गेट और रायसीना हिल पर, और महिलाओं के लिए बेहतर सुरक्षा और बलात्कार के खिलाफ सख्त कानूनों की मांग की। सरकार ने न्यायमूर्ति जे.एस. वर्मा समिति का गठन किया, जिसकी सिफारिशों के आधार पर <strong>आपराधिक कानून (संशोधन) अधिनियम, 2013</strong> पारित किया गया। इस कानून ने बलात्कार, यौन उत्पीड़न और एसिड हमलों से संबंधित कानूनों को काफी सख्त बना दिया और इसमें नई श्रेणियां जैसे पीछा करना (स्टॉकिंग) और ताक-झांक (वॉयरिज्म) को भी अपराध माना गया।
                        </p>
                    </div>
                    <div>
                        <div class="chart-container">
                            <canvas id="rapeCasesChart"></canvas>
                        </div>
                        <p class="text-center text-sm text-stone-500 mt-2">स्रोत: राष्ट्रीय अपराध रिकॉर्ड ब्यूरो (NCRB), भारत</p>
                    </div>
                </div>
            </section>
        </main>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const navLinks = document.querySelectorAll('.nav-link');
            const contentSections = document.querySelectorAll('.content-section');

            const timelineData = [
                {
                    year: 'दिसंबर 2012',
                    title: 'घटना और गिरफ्तारी',
                    content: '16 दिसंबर को दिल्ली में चलती बस में 23 वर्षीय महिला के साथ सामूहिक बलात्कार और हमला। 29 दिसंबर को सिंगापुर के एक अस्पताल में पीड़िता की मृत्यु हो गई। पुलिस ने सभी छह आरोपियों को गिरफ्तार कर लिया।'
                },
                {
                    year: 'सितंबर 2013',
                    title: 'फास्ट-ट्रैक कोर्ट का फैसला',
                    content: 'दिल्ली की एक फास्ट-ट्रैक अदालत ने चार वयस्क दोषियों - मुकेश सिंह, विनय शर्मा, अक्षय कुमार सिंह और पवन गुप्ता को हत्या, सामूहिक बलात्कार और अन्य आरोपों में दोषी ठहराया और उन्हें मौत की सजा सुनाई।'
                },
                {
                    year: 'मार्च 2014',
                    title: 'दिल्ली उच्च न्यायालय का फैसला',
                    content: 'दिल्ली उच्च न्यायालय ने चारों दोषियों की अपील खारिज कर दी और फास्ट-ट्रैक कोर्ट द्वारा दी गई मौत की सजा की पुष्टि की। न्यायालय ने कहा कि यह मामला "दुर्लभ से दुर्लभतम" (rarest of rare) श्रेणी में आता है।'
                },
                {
                    year: 'मई 2017',
                    title: 'सर्वोच्च न्यायालय का फैसला',
                    content: 'भारत के सर्वोच्च न्यायालय ने दोषियों की अपील को खारिज करते हुए मौत की सजा को बरकरार रखा। अदालत ने अपराध को "क्रूरता की सुनामी" कहा जिसने समाज की अंतरात्मा को झकझोर दिया।'
                },
                {
                    year: '2018-2019',
                    title: 'पुनर्विचार याचिकाएं',
                    content: 'दोषियों ने सर्वोच्च न्यायालय में पुनर्विचार याचिकाएं दायर कीं। 2018 और 2019 में, सर्वोच्च न्यायालय ने इन सभी याचिकाओं को खारिज कर दिया, यह कहते हुए कि फैसले पर पुनर्विचार करने का कोई आधार नहीं है।'
                },
                {
                    year: 'जनवरी-मार्च 2020',
                    title: 'उपचारात्मक और दया याचिकाएं',
                    content: 'दोषियों ने एक के बाद एक उपचारात्मक (curative) याचिकाएं और भारत के राष्ट्रपति के समक्ष दया याचिकाएं दायर कीं, जिससे फांसी में देरी हुई। सभी याचिकाएं अंततः खारिज कर दी गईं।'
                },
                {
                    year: '20 मार्च 2020',
                    title: 'फांसी',
                    content: 'घटना के सात साल, तीन महीने और चार दिन बाद, चारों दोषियों - मुकेश सिंह, पवन गुप्ता, विनय शर्मा और अक्षय कुमार सिंह को तिहाड़ जेल में सुबह 5:30 बजे फांसी दे दी गई।'
                }
            ];

            const timelineContainer = document.getElementById('timeline-container');
            const detailsTitle = document.getElementById('details-title');
            const detailsContent = document.getElementById('details-content');

            timelineData.forEach((item, index) => {
                const timelineElement = document.createElement('div');
                timelineElement.classList.add('timeline-item', 'mb-8', 'flex', 'justify-between', 'items-center', 'w-full');
                if (index % 2 === 0) {
                    timelineElement.classList.add('flex-row-reverse');
                }
                timelineElement.innerHTML = `
                    <div class="order-1 w-5/12"></div>
                    <div class="z-20 flex items-center order-1 bg-stone-800 shadow-xl w-12 h-12 rounded-full timeline-dot">
                        <h1 class="mx-auto font-semibold text-lg text-white">${index + 1}</h1>
                    </div>
                    <div class="order-1 bg-stone-200 rounded-lg shadow-xl w-5/12 px-6 py-4 timeline-content">
                        <h3 class="font-bold text-stone-800 text-lg">${item.year}</h3>
                        <p class="text-sm leading-snug tracking-wide text-stone-600">${item.title}</p>
                    </div>
                `;
                timelineElement.addEventListener('click', () => {
                    document.querySelectorAll('.timeline-item').forEach(el => el.classList.remove('active'));
                    timelineElement.classList.add('active');
                    detailsTitle.textContent = `${item.year}: ${item.title}`;
                    detailsContent.textContent = item.content;
                });
                timelineContainer.appendChild(timelineElement);
            });

            const activateSection = (hash) => {
                const targetHash = hash || '#incident';
                navLinks.forEach(link => {
                    link.classList.toggle('active', link.hash === targetHash);
                });
                contentSections.forEach(section => {
                    section.classList.toggle('active', `#${section.id}` === targetHash);
                });
            };
            
            navLinks.forEach(link => {
                link.addEventListener('click', (e) => {
                    e.preventDefault();
                    history.pushState(null, null, e.currentTarget.hash);
                    activateSection(e.currentTarget.hash);
                });
            });

            window.addEventListener('popstate', () => {
                 activateSection(window.location.hash);
            });
            
            activateSection(window.location.hash);

            const ctx = document.getElementById('rapeCasesChart').getContext('2d');
            const rapeCasesChart = new Chart(ctx, {
                type: 'bar',
                data: {
                    labels: ['2010', '2011', '2012', '2013', '2014', '2015', '2016'],
                    datasets: [{
                        label: 'भारत में दर्ज बलात्कार के मामले',
                        data: [22172, 24206, 24923, 33707, 36735, 34651, 38947],
                        backgroundColor: 'rgba(140, 45, 45, 0.6)',
                        borderColor: 'rgba(140, 45, 45, 1)',
                        borderWidth: 1
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        title: {
                            display: true,
                            text: 'बलात्कार के मामलों की रिपोर्टिंग में वृद्धि (2012 के बाद)',
                            font: { size: 16 }
                        },
                        tooltip: {
                            callbacks: {
                                label: function(context) {
                                    let label = context.dataset.label || '';
                                    if (label) {
                                        label += ': ';
                                    }
                                    if (context.parsed.y !== null) {
                                        label += new Intl.NumberFormat('en-IN').format(context.parsed.y);
                                    }
                                    return label;
                                }
                            }
                        }
                    },
                    scales: {
                        y: {
                            beginAtZero: true,
                            title: {
                                display: true,
                                text: 'मामलों की संख्या'
                            }
                        }
                    }
                }
            });

            if(document.querySelector('.timeline-item')) {
                 document.querySelector('.timeline-item').click();
            }
        });
    </script>
</body>
</html>

