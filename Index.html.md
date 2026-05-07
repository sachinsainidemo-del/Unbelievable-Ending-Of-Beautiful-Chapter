Index.html  
  
  
```html  
<!DOCTYPE html>  
<html lang="en">  
<head>  
    <meta charset="UTF-8">  
    <meta name="viewport" content="width=device-width, initial-scale=1.0">  
    <title>Gift Letter to Sonam</title>  
    <script src="https://cdn.tailwindcss.com"></script>  
    <style>  
        @import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Lora:ital,wght@0,400;0,700;1,400&family=Courier+Prime&family=Montserrat:wght@300;400;600;700;800&family=Inter:wght@400;600&family=Birthstone&display=swap');  
  
        :root {  
            --pink-highlight: #ff2d75;  
            --hot-pink: #ff1493;  
            --pink-soft: #fff0f5;  
            --dark-base: #1a1a1a;  
            --spoiler-bg: #333333;  
        }  
  
        body {  
            background: #f8fafc;   
            font-family: 'Lora', serif;  
            color: #2d3436;  
            line-height: 1.8;  
            overflow-x: hidden;  
            margin: 0;  
            padding: 0;  
            position: relative;  
        }  
  
        /* --- VIGNETTE EFFECT --- */  
        body::after {  
            content: "";  
            position: fixed;  
            top: 0;  
            left: 0;  
            width: 100%;  
            height: 100%;  
            box-shadow: inset 0 0 150px rgba(0,0,0,0.07);  
            pointer-events: none;  
            z-index: 100;  
        }  
  
        /* --- GRAIN/DUST TEXTURE --- */  
        .grain-overlay {  
            position: fixed;  
            top: 0;  
            left: 0;  
            width: 100%;  
            height: 100%;  
            background-image: url("https://www.transparenttextures.com/patterns/stardust.png");  
            opacity: 0.04;  
            pointer-events: none;  
            z-index: 99;  
        }  
  
        /* --- PETALS ANIMATION --- */  
        .petal {  
            position: fixed;  
            background: #ffd1dc;  
            border-radius: 150% 0 150% 0;  
            opacity: 0.3;  
            pointer-events: none;  
            z-index: 5;  
            animation: fall 10s linear infinite;  
        }  
  
        @keyframes fall {  
            0% { transform: translateY(-10vh) rotate(0deg); left: var(--left); }  
            100% { transform: translateY(110vh) rotate(360deg); left: calc(var(--left) + 20px); }  
        }  
  
        /* --- STAMP EFFECT --- */  
        .vintage-stamp {  
            position: absolute;  
            top: 40px;  
            right: 40px;  
            width: 100px;  
            height: 100px;  
            border: 3px double #e2e8f0;  
            border-radius: 50%;  
            display: flex;  
            align-items: center;  
            justify-content: center;  
            text-align: center;  
            font-family: 'Montserrat', sans-serif;  
            font-weight: 800;  
            font-size: 0.6rem;  
            color: #cbd5e0;  
            text-transform: uppercase;  
            transform: rotate(15deg);  
            padding: 5px;  
            user-select: none;  
            pointer-events: none;  
        }  
  
        /* --- Digital Envelope Styles --- */  
        #envelope-overlay {  
            position: fixed;  
            top: 0;  
            left: 0;  
            width: 100%;  
            height: 100%;  
            background: #f1f5f9;  
            z-index: 9999;  
            display: flex;  
            align-items: center;  
            justify-content: center;  
            transition: transform 0.8s cubic-bezier(0.87, 0, 0.13, 1);  
        }  
  
        .envelope {  
            width: 320px;  
            height: 220px;  
            background: #ffffff;  
            position: relative;  
            box-shadow: 0 20px 40px rgba(0,0,0,0.15);  
            border-radius: 4px;  
            display: flex;  
            flex-direction: column;  
            align-items: center;  
            justify-content: center;  
            border: 1px solid #e2e8f0;  
        }  
  
        .envelope::before {  
            content: "";  
            position: absolute;  
            top: 0;  
            width: 0;  
            height: 0;  
            border-left: 160px solid transparent;  
            border-right: 160px solid transparent;  
            border-top: 110px solid #f1f5f9;  
            z-index: 2;  
        }  
  
        .open-btn {  
            z-index: 10;  
            background: var(--hot-pink);  
            color: white;  
            padding: 12px 30px;  
            border-radius: 50px;  
            font-family: 'Montserrat', sans-serif;  
            font-weight: 700;  
            cursor: pointer;  
            border: none;  
            box-shadow: 0 4px 20px rgba(255, 20, 147, 0.4);  
            transition: 0.3s ease;  
            text-transform: uppercase;  
            letter-spacing: 2px;  
            font-size: 0.9rem;  
            animation: pulse 2s infinite;  
        }  
  
        @keyframes pulse {  
            0% { transform: scale(1); }  
            50% { transform: scale(1.05); }  
            100% { transform: scale(1); }  
        }  
  
        .envelope-stamp {  
            position: absolute;  
            bottom: 20px;  
            right: 20px;  
            font-family: 'Birthstone', cursive;  
            font-size: 1.5rem;  
            color: #cbd5e0;  
        }  
  
        /* --- Main Content Transition --- */  
        .content-hidden {  
            opacity: 0;  
            transform: translateY(20px);  
            transition: all 1s ease 0.5s;  
        }  
  
        .content-visible {  
            opacity: 1;  
            transform: translateY(0);  
        }  
  
        /* --- Typewriter Effect Styles --- */  
        .typewriter {  
            overflow: hidden;  
            border-right: .15em solid var(--hot-pink);  
            white-space: nowrap;  
            margin: 0 auto;  
            letter-spacing: .15em;  
            width: 0;   
        }  
  
        @keyframes typing {  
            from { width: 0 }  
            to { width: 100% }  
        }  
  
        @keyframes blink-caret {  
            from, to { border-color: transparent }  
            50% { border-color: var(--hot-pink); }  
        }  
  
        .animate-type {  
            animation:   
                typing 3s steps(40, end) forwards,  
                blink-caret .75s step-end infinite;  
        }  
  
        /* Letter Container & Content Styles */  
        .letter-container {  
            max-width: 800px;  
            margin: 40px auto;  
            background: #ffffff;   
            color: #2d3436;  
            padding: 60px 50px;  
            position: relative;  
            box-shadow: 0 25px 60px rgba(0, 0, 0, 0.08);  
            border-radius: 8px;  
            border: 1px solid #edf2f7;  
            z-index: 10;  
        }  
  
        .greeting-card {  
            background: #ffffff;  
            border: 2px solid var(--hot-pink);  
            padding: 8px 20px;  
            display: inline-block;  
            border-radius: 10px;  
            margin-bottom: 30px;  
            box-shadow: 0 4px 15px rgba(255, 20, 147, 0.1);  
        }  
  
        .hot-pink-text-handwritten {  
            color: var(--hot-pink) !important;  
            font-family: 'Dancing Script', cursive;  
            font-size: 2.5rem;  
            line-height: 1.2;  
        }  
  
        .header-bold-line {  
            font-family: 'Montserrat', sans-serif;  
            font-weight: 800 !important;   
            letter-spacing: 0.25em;  
            color: #4b5563;  
            text-transform: uppercase;  
            font-size: 11px;  
            border-top: 1px solid #e2e8f0;  
            border-bottom: 1px solid #e2e8f0;  
            padding: 6px 0;  
            display: inline-block;  
            width: 100%;  
        }  
  
        h1 {  
            font-family: 'Montserrat', sans-serif;  
            font-weight: 800;  
            text-transform: uppercase;  
            letter-spacing: 4px;  
            color: var(--dark-base);  
            margin-bottom: 15px;  
            font-size: 2.2rem;  
        }  
  
        .sub-heading {  
            font-family: 'Dancing Script', cursive;  
            font-size: 2.2rem;   
            color: #4b5563;   
            margin-bottom: 45px;  
            display: block;  
            text-shadow: 1px 1px 2px rgba(0,0,0,0.05);  
            transition: all 0.3s ease;  
            opacity: 0.85;   
        }  
  
        .hl-pink { background: var(--pink-soft); color: #d63384; padding: 0 4px; border-radius: 2px; font-weight: 600; }  
        .hl-black { background: #f1f2f6; color: #2f3542; padding: 0 4px; border-radius: 2px; font-weight: 600; }  
        .underline-black { border-bottom: 2px solid #1a1a1a; font-weight: 600; }  
          
        .main-highlight {  
            color: #000;  
            font-weight: 800;  
            background-color: #fff9c4;  
            padding: 0 2px;  
        }  
  
        .suspense-spoiler {  
            background-color: var(--spoiler-bg);  
            color: transparent;  
            cursor: pointer;  
            transition: all 0.4s ease;  
            border-radius: 4px;  
            padding: 0 6px;  
            user-select: none;  
        }  
        .suspense-spoiler:hover {  
            background-color: #fdf2f8;  
            color: var(--hot-pink);  
            box-shadow: 0 0 10px rgba(255, 20, 147, 0.2);  
        }  
  
        .quote-block {  
            font-style: italic;  
            text-align: center;  
            color: #4a5568;  
            margin: 40px 0;  
            padding: 30px;  
            border-top: 1px solid #f1f5f9;  
            border-bottom: 1px solid #f1f5f9;  
            font-size: 1.1rem;  
            position: relative;  
        }  
  
        .quote-block::before {  
            content: "“";  
            position: absolute;  
            top: 10px;  
            left: 50%;  
            transform: translateX(-50%);  
            font-size: 3rem;  
            color: #cbd5e0;  
            font-family: serif;  
        }  
  
        /* Floating Minimal Quote Style */  
        .minimal-quote {  
            text-align: center;  
            margin: 45px 0;  
            padding: 20px;  
            border: 1px dashed #cbd5e0;  
            border-radius: 4px;  
            font-family: 'Lora', serif;  
            font-style: italic;  
            color: #64748b;  
            font-size: 1rem;  
        }  
  
        /* --- POLAROID PHOTO STYLES --- */  
        .photo-memories {  
            display: flex;  
            justify-content: center;  
            margin: 50px 0;  
        }  
  
        .polaroid {  
            background: white;  
            padding: 15px 15px 40px 15px;  
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);  
            transform: rotate(-3deg);  
            border: 1px solid #eee;  
            max-width: 320px;  
            transition: transform 0.3s ease;  
        }  
  
        .polaroid:hover {  
            transform: rotate(0deg) scale(1.05);  
            z-index: 20;  
        }  
  
        .polaroid img {  
            width: 100%;  
            height: auto;  
            border-radius: 2px;  
            display: block;  
        }  
  
        .polaroid .caption {  
            font-family: 'Dancing Script', cursive;  
            text-align: center;  
            font-size: 1.4rem;  
            margin-top: 15px;  
            color: #444;  
        }  
  
        /* --- TIMELINE STYLES --- */  
        .timeline {  
            margin: 60px 0;  
            padding-left: 20px;  
            border-left: 2px solid #edf2f7;  
        }  
        .timeline-item {  
            position: relative;  
            margin-bottom: 40px;  
            padding-left: 30px;  
        }  
        .timeline-item::before {  
            content: "";  
            position: absolute;  
            left: -31px;  
            top: 5px;  
            width: 20px;  
            height: 20px;  
            background: white;  
            border: 2px solid var(--hot-pink);  
            border-radius: 50%;  
        }  
        .timeline-date {  
            font-weight: 800;  
            color: #1a1a1a;  
            font-size: 0.9rem;  
            text-transform: uppercase;  
            letter-spacing: 1px;  
            margin-bottom: 5px;  
            display: block;  
        }  
        .timeline-desc {  
            font-size: 0.95rem;  
            color: #4a5568;  
            font-style: italic;  
        }  
  
        .final-note-box {  
            margin-top: 60px;  
            border: 2px solid #1a1a1a;  
            padding: 30px;  
            background: #ffffff;  
            position: relative;  
            text-align: center;  
        }  
  
        .final-note-title {  
            position: absolute;  
            top: -14px;  
            left: 50%;  
            transform: translateX(-50%);  
            background: #1a1a1a;  
            color: white;  
            padding: 4px 20px;  
            font-family: 'Montserrat', sans-serif;  
            font-weight: 800;  
            font-size: 0.8rem;  
            letter-spacing: 2px;  
        }  
  
        /* --- NEW DARK MESSAGE STYLE --- */  
        .dark-message-box {  
            background-color: #000;  
            padding: 40px 20px;  
            border-radius: 4px;  
            margin-top: 40px;  
            text-align: center;  
            box-shadow: 0 0 30px rgba(255, 20, 147, 0.4);  
            border: 1px solid var(--hot-pink);  
            position: relative;  
            overflow: hidden;  
        }  
  
        .dark-message-box::before {  
            content: "";  
            position: absolute;  
            top: 0; left: 0; right: 0; bottom: 0;  
            background: radial-gradient(circle at center, rgba(255, 20, 147, 0.15) 0%, transparent 70%);  
            pointer-events: none;  
        }  
  
        .dark-message-text {  
            color: #fff;  
            font-family: 'Montserrat', sans-serif;  
            font-weight: 900;  
            text-transform: uppercase;  
            font-size: 1.5rem;  
            letter-spacing: 0.1em;  
            margin: 0;  
            position: relative;  
            z-index: 2;  
        }  
  
        .page-break {  
            margin: 50px 0;  
            text-align: center;  
            color: #cbd5e0;  
            font-size: 1.5rem;  
            letter-spacing: 1rem;  
        }  
  
        /* Heart Divider */  
        .heart-divider {  
            display: flex;  
            align-items: center;  
            justify-content: center;  
            gap: 15px;  
            margin: 40px 0;  
            opacity: 0.4;  
        }  
        .heart-divider .line {  
            height: 1px;  
            width: 60px;  
            background: #cbd5e0;  
        }  
        .tiny-heart {  
            font-size: 0.8rem;  
            color: #a0aec0;  
        }  
  
        .corner {  
            position: absolute;  
            width: 40px;  
            height: 40px;  
            border: 2px solid var(--hot-pink);  
            opacity: 0.3;  
        }  
        .top-left { top: 30px; left: 30px; border-right: none; border-bottom: none; }  
        .bottom-right { bottom: 30px; right: 30px; border-left: none; border-top: none; }  
  
        .footer-end-text {  
            font-family: 'Montserrat', sans-serif;  
            font-weight: 400;  
            font-size: 0.7rem;  
            letter-spacing: 0.15em;  
            color: #94a3b8;  
            text-transform: uppercase;  
        }  
  
        .sig-box-white {  
            background-color: #fff;  
            color: #1a1a1a;  
            padding: 20px 0;  
            display: inline-block;  
            margin-top: 10px;  
            min-width: 250px;  
        }  
  
        .signature-font-dark {  
            font-family: 'Birthstone', cursive;  
            font-size: 4rem;  
            color: #1a1a1a;  
            line-height: 0.8;  
            margin-bottom: 15px;  
        }  
  
        .always-font-dark {  
            font-family: 'Lora', serif;  
            font-style: italic;  
            font-size: 0.9rem;  
            letter-spacing: 0.05em;  
            color: #4a5568;  
            border-top: 1px solid #e2e8f0;  
            padding-top: 10px;  
            margin-top: 5px;  
            display: inline-block;  
        }  
  
        .stop-now-line {  
            font-family: 'Inter', sans-serif;  
            font-size: 0.95rem;  
            color: #4b5563;  
            margin-top: 20px;  
            display: block;  
        }  
  
        /* --- HIDDEN MESSAGE STYLES --- */  
        #secret-trigger {  
            cursor: pointer;  
            color: #f1f5f9;   
            font-size: 0.8rem;  
            transition: color 0.5s ease;  
            margin-top: 10px;  
            display: inline-block;  
            user-select: none;  
        }  
        #secret-trigger:hover {  
            color: #cbd5e0;  
        }  
  
        #secret-message {  
            display: none;  
            position: fixed;  
            top: 50%;  
            left: 50%;  
            transform: translate(-50%, -50%);  
            background: white;  
            padding: 40px;  
            border-radius: 12px;  
            box-shadow: 0 30px 100px rgba(0,0,0,0.2);  
            z-index: 10000;  
            width: 90%;  
            max-width: 500px;  
            border: 1px solid var(--pink-soft);  
            text-align: center;  
        }  
  
        .overlay-dark {  
            display: none;  
            position: fixed;  
            top: 0;  
            left: 0;  
            width: 100%;  
            height: 100%;  
            background: rgba(0,0,0,0.4);  
            backdrop-filter: blur(5px);  
            z-index: 9999;  
        }  
  
        .secret-content {  
            font-family: 'Dancing Script', cursive;  
            font-size: 1.8rem;  
            color: #1a1a1a;  
            line-height: 1.4;  
        }  
  
        .close-secret {  
            margin-top: 25px;  
            font-family: 'Montserrat', sans-serif;  
            font-size: 0.7rem;  
            text-transform: uppercase;  
            letter-spacing: 2px;  
            color: #94a3b8;  
            cursor: pointer;  
            border: 1px solid #e2e8f0;  
            padding: 8px 15px;  
            border-radius: 4px;  
            display: inline-block;  
        }  
  
        @media (max-width: 640px) {  
            .letter-container { padding: 40px 20px; margin: 10px; }  
            .typewriter { font-size: 0.8rem; white-space: normal; width: auto !important; border: none; animation: none; }  
            .sub-heading { font-size: 1.6rem; }  
            h1 { font-size: 1.5rem; }  
            .vintage-stamp { top: 15px; right: 15px; width: 70px; height: 70px; font-size: 0.45rem; }  
            .dark-message-text { font-size: 1.1rem; }  
        }  
    </style>  
</head>  
<body class="py-10">  
  
    <div class="grain-overlay"></div>  
    <div id="petals-container"></div>  
  
    <!-- Envelope Overlay -->  
    <div id="envelope-overlay">  
        <div class="envelope">  
            <div class="text-center mb-6">  
                <p class="text-xs uppercase tracking-widest text-gray-400 mb-1">Incoming Message</p>  
                <p class="font-bold text-gray-700">A special letter for you</p>  
            </div>  
            <button class="open-btn" onclick="openLetter()">Open Letter</button>  
            <div class="envelope-stamp">For Sonam</div>  
        </div>  
    </div>  
  
    <!-- Secret Message Popup -->  
    <div id="overlay-dark" class="overlay-dark" onclick="closeSecret()"></div>  
    <div id="secret-message">  
        <div class="secret-content">  
            "Jis din se maine tumhe jean kurti aur punjabi jutti m dekha ha i loose my control aur bhut khush tha ush din se lekin abbbb idk but Thanks us video k lie 💫🤌🏻🐣🌸"  
        </div>  
        <div class="close-secret" onclick="closeSecret()">Close</div>  
    </div>  
  
    <!-- Letter Content -->  
    <div id="main-content" class="letter-container content-hidden">  
        <div class="vintage-stamp">  
            SEALED &<br>FINAL<br>#SAM1803  
        </div>  
        <div class="corner top-left"></div>  
        <div class="corner bottom-right"></div>  
  
        <header class="text-center mb-12">  
            <h1 id="main-title">Gift Letter to Sonam</h1>  
            <span class="sub-heading">"A chapter I couldn't keep..."</span>  
              
            <div class="header-bold-line">  
                PERSONAL & CONFIDENTIAL • PUBLISHED BY #SAM1803 • MAY 2026  
            </div>  
        </header>  
  
        <section class="content">  
            <div class="greeting-card">  
                <p class="hot-pink-text-handwritten">Hey Sonam Bacha 🌸</p>  
            </div>  
  
            <p>  
                Hope you are doing well. <span class="main-highlight">This is the final gift for you from my side 😭.</span> Let’s proceed, and I am sure you will understand and feel it. I would like to say—it was a lesson for me. Or we can say it was a <span class="bold-main italic hl-black text-black">chapter of a book</span> which has been turned now. Let’s focus on the new chapter and <span class="main-highlight">start the new beginning from zero</span>, because in a book, all chapters are different 🌸. <span class="italic-thought block my-4 border-l-4 border-pink-500 pl-4 italic text-gray-600">In simple words, life is like a book with all non-equal chapters. Sometimes there is a bad guide, sometimes a good one.</span> It depends, but I am wishing you a <span class="hl-pink">very, very bright future</span>, my dear loved one 🙂🥺.  
            </p>  
  
            <div class="quote-block">  
                Whatever I have done, or you have done, matters no more to me! It was a phase for both of us.  
            </div>  
  
            <p class="mt-6">  
                I wasn't able to complete your words, I didn't obey your orders, <span class="main-highlight">I always let you feel down, and I ignored you on top of everything without any reason.</span> If I had one, I would have shared it with you, but I couldn't do that. <span class="underline-black">The time which I spent now, these last few weeks, was memorable</span> because explaining it is a very complicated thing for me. If I started to elucidate your presence with me in chats, it might take the <span class="font-mono bg-gray-100 px-1 rounded text-red-600">full night</span> or even tomorrow 😀. It was a phase for both of us, Sonam, because we both have our private lives with different goals, intentions, and many more things.  
            </p>  
  
            <p class="mt-6">  
                The decision you took before was your personal choice because of me (I could say)—never understanding you, showing attitude, ignorance, using bad words, not caring, etc. <span class="main-highlight">It was a good decision as per your perspective</span>; if I were in your place as a girl, I might have chosen the same as you, <span class="font-bold underline">doll</span>. We both have different genders and faced issues caused by me or somehow by you. I never tried to understand you in the starting days when I left India. I know I should have informed you, but <span class="main-highlight">I couldn't do it 😭 even if I wanted to.</span>  
            </p>  
  
            <div class="page-break">✦ ✦ ✦</div>  
  
            <p class="mt-6">  
                Sonam, the past is the past. Moving away for you may be easy, mild, or severe, but for me, I have no need to say, right <span class="font-bold text-red-500">beta?</span> <span class="main-highlight">The more we think about the past, the more we will hurt ourselves.</span>   
                <span class="block my-6 border-l-4 border-gray-200 pl-6 italic text-gray-500">  
                    "The first meetup, your sudden lip kiss in a restaurant without even thinking for a minute..."  
                </span>  
                Afterward you were afraid, and I handled the situation, gave you a warm hug, and kept you calm. The next one: somebody’s guy that you know saw us together, and again you were scared, but <span class="main-highlight">I always protect and support you.</span>  
            </p>  
  
            <div class="minimal-quote">  
                "Sometimes you have to close a book, not because you've finished the story, but because the next chapter isn't meant for you."  
            </div>  
  
            <p class="mt-6">  
                Let’s proceed to that moment when I made my friend act as a security guard downstairs to keep us safe. <span class="hl-black">The shop owner was already on our side hahahah</span>, but there was a fear of the owner; still, he took the risk for us. Remember, we looked at each other; you were trying not to see my face, but I did it properly and you learned too, <span class="hl-pink">bachu</span>. We did lots of things that day, but we <span class="line-through text-gray-400">never ever completed any food</span> in a restaurant 😅. How could we eat? We were both lost in each other hahahha.  
            </p>  
  
            <p id="typewriter-header" class="mt-6 font-bold text-center text-2xl text-gray-800 tracking-widest uppercase typewriter">  
                ✨ THE MAIN TOPIC ✨  
            </p>  
  
            <p class="mt-4">  
                Now the main topic starts. I hope you remembered the day when I planned a surprise for you. By asking tricky questions, I got the size of your fingers. I diverted your non-working mind to other things. When we arrived at the restaurant, I said, <span class="main-highlight">"Close your eyes and do not open them without my permission,"</span> swearing on our love ❤️. You agreed and closed both eyes, then, then, then...   
                <span class="suspense-spoiler">I placed both ring boxes in front of you, opening both so you could see them with your eyes and I could see your reaction.</span> It was really a <span class="main-highlight">shocking reaction on your face</span>, as well as a lovingly smile 😊 on your pyara sa face.  
            </p>  
  
            <!-- PHOTO SECTION -->  
            <div class="photo-memories">  
                <div class="polaroid">  
                    <img src="https://i.ibb.co/TDk14ZrH/IMG-3263.jpg" alt="<img src="https://i.ibb.co/TDk14ZrH/IMG-3263.jpg" width="300">  
                    <div class="caption">Our Forever 💍❤️</div>  
                </div>  
            </div>  
  
            <p class="mt-6">  
                And one of the main reasons for fear was how you could take them home. But as a brave BF, I suggested something. By following the advice, you took both rings home and kept them safe. At the acceptance time, <span class="main-highlight">you were blushing a lot like a new bride 👰.</span> The fact is, yeah, you are a <span class="underline-black">queen who needs a king 👑</span> so he can keep her safe and fulfill all the dreams which you deserved, <span class="font-bold text-pink-600">gugu 😚.</span>  
            </p>  
  
            <div class="page-break">⌛</div>  
  
            <p class="mt-8 italic">  
                Now the time has come for our <span class="underline-black text-red-600 text-xl font-bold">last meetup 🙂</span> and <span class="main-highlight">I never thought this was really the last meetup with you.</span> <span class="hl-pink">If I had any clue, I would not have gone abroad 😭🙂.</span> Everything is already written in our destiny, so with a smile, we should accept it happily 🌟. I said these things because I never wanted to hide anything from you. The past is the past, although it’s a <span class="font-bold border-b-2 border-gray-800">part of life or a chapter of a book 📖.</span>  
            </p>  
  
            <!-- TIMELINE SECTION -->  
            <div class="timeline">  
                <div class="timeline-item">  
                    <span class="timeline-date">March 18</span>  
                    <p class="timeline-desc">The day that changed everything. #SAM1803</p>  
                </div>  
                <div class="timeline-item">  
                    <span class="timeline-date">The First Sight</span>  
                    <p class="timeline-desc">Jean kurti, punjabi jutti... and I lost my control. 🤍</p>  
                </div>  
                <div class="timeline-item">  
                    <span class="timeline-date">The Ring Day</span>  
                    <p class="timeline-desc">Blushing like a bride. Keeping the promise safe.</p>  
                </div>  
                <div class="timeline-item">  
                    <span class="timeline-date">The Final Step</span>  
                    <p class="timeline-desc">Saying goodbye, but wishing for your brightest future.</p>  
                </div>  
            </div>  
  
            <p class="mt-6">  
                Countless times I said that I want one thing: <span class="hl-black">your protection of yourself.</span> I was like a <span class="main-highlight">mentor to guide you</span> and you followed. But with the passage of time, everything changed. I should always have maintained calmness, but I couldn’t, which affected our relationship due to <span class="main-highlight">my faults 🥺.</span> What more could I say? I am sorry for hurting you 🫠. I know you have a big heart and you will definitely forgive me, <span class="font-mono text-sm bg-gray-100 p-1">beta 🤌🏻.</span>  
            </p>  
  
            <div class="quote-block">  
                "Always take care of yourself, mama, papa, and Kris... respect them well and you will get the same in return."  
            </div>  
  
            <p id="typewriter-header-2" class="mt-6 font-bold underline mb-4 text-gray-900 text-lg typewriter">  
                Last but not least: Be confident.  
            </p>  
            <p>  
                Never ever trap yourself in someone’s plan, please 🙏🏽. <span class="main-highlight">Before taking a step, think a thousand times 🫂.</span> Take care of your health, especially <span class="hl-pink">mental as well as physical health 👥.</span> Stay away from bad people in college specifically. Never be afraid of someone—you are brave and you can handle it. Never get attached easily to someone—I am advising you because <span class="main-highlight">I know you more than you know yourself.</span>  
            </p>  
  
            <div class="mt-10 p-6 bg-pink-50 border-l-4 border-pink-500 rounded-r-lg">  
                <p class="text-gray-800 italic">  
                    And yes, <span class="suspense-spoiler">I went to AIIMS yesterday and am taking treatment, including psychiatric treatment medicine, but do not worry.</span> Be cool and calm; I will be better soon. Due to overthinking, I wasn’t able to accept this yesterday, but now the truth is on your table ☺️😊. <span class="main-highlight">Grateful to have had you with me 😣😫.</span>  
                </p>  
            </div>  
  
            <p class="mt-8 text-center text-xl font-serif italic text-gray-700">  
                <span class="main-highlight">"I loved you, I love you, and I will continue to love you 😭🥺. Please accept it and move ahead to start the new journey of life 🤌🏻🌸."</span>  
            </p>  
  
            <p class="mt-10 text-lg font-semibold border-t pt-6">  
                It is hesitant to say a painful 😣 goodbye to my love, but <span class="main-highlight">I failed to understand it 🙂</span> <span class="text-red-600 font-mono text-sm">(Failed in love)</span>. Take care, my love—<span class="font-bold text-pink-600">Sonam Rajput 🥺.</span> It’s time to go now 😭.  
            </p>  
  
            <!-- DARK MESSAGE BOX -->  
            <div class="dark-message-box">  
                <p class="dark-message-text">  
                    KAASH HAMMMILE HI NA HOTE 💔🥺🥀  
                </p>  
            </div>  
  
            <p class="mt-6">  
                There might be something missing, but I added mostly all that I remembered. Again, take care, my princess. <span class="font-bold text-gray-800">Good Bye ✋ 😞</span>  
            </p>  
  
            <div class="mt-16 flex flex-col items-start border-t border-gray-100 pt-10">  
                <p class="text-sm uppercase tracking-widest text-gray-400 mb-1">With Love,</p>  
                  
                <div class="sig-box-white">  
                    <p class="signature-font-dark">Rohin Singh Saini</p>  
                    <p class="always-font-dark">#sam1803 — ALWAYS WITH YOU</p>  
                </div>  
                  
                <div class="stop-now-line">  
                    There is where i stop now … 🫡💫🥺🥺  
                </div>  
                  
                <div class="mt-6 opacity-20 text-3xl">🕊️</div>  
            </div>  
  
            <!-- Heart Divider -->  
            <div class="heart-divider">  
                <div class="line"></div>  
                <div class="tiny-heart">💔</div>  
                <div class="line"></div>  
            </div>  
  
            <div class="final-note-box">  
                <div class="final-note-title">FINAL MESSAGE</div>  
                <div class="leading-relaxed text-gray-700">  
                    <p class="mb-2">  
                        This is my <b>final expression</b> of true feelings 🥺.   
                        Bas apna dhyan rakhna aur hamesha <b>happy rehna</b> 🫂🌸.   
                    </p>  
                    <p class="text-pink-600 font-bold uppercase tracking-widest text-xs mt-4">  
                        START THE NEW JOURNEY • BEST WISHES 🤌🏻✨  
                    </p>  
                </div>  
            </div>  
  
            <p class="mt-12 text-center footer-end-text">  
                — End of the final chapter. Moving forward with peace. —  
            </p>  
              
            <!-- Secret Trigger -->  
            <div class="text-center mt-4">  
                <span id="secret-trigger" onclick="showSecret()">🤍</span>  
            </div>  
        </section>  
    </div>  
  
    <script>  
        function createPetal() {  
            const petal = document.createElement('div');  
            petal.className = 'petal';  
            petal.style.setProperty('--left', Math.random() * 100 + 'vw');  
            petal.style.width = Math.random() * 15 + 10 + 'px';  
            petal.style.height = petal.style.width;  
            petal.style.animationDuration = Math.random() * 5 + 5 + 's';  
            document.getElementById('petals-container').appendChild(petal);  
            setTimeout(() => petal.remove(), 10000);  
        }  
  
        function openLetter() {  
            const envelope = document.getElementById('envelope-overlay');  
            envelope.style.transform = 'translateY(-100%)';  
              
            const content = document.getElementById('main-content');  
            content.classList.remove('content-hidden');  
            content.classList.add('content-visible');  
  
            setInterval(createPetal, 500);  
  
            setTimeout(() => {  
                const head = document.getElementById('typewriter-header');  
                if(head) head.classList.add('animate-type');  
            }, 1500);  
  
            setTimeout(() => {  
                const head2 = document.getElementById('typewriter-header-2');  
                if(head2) head2.classList.add('animate-type');  
            }, 4000);  
        }  
  
        function showSecret() {  
            document.getElementById('overlay-dark').style.display = 'block';  
            document.getElementById('secret-message').style.display = 'block';  
        }  
  
        function closeSecret() {  
            document.getElementById('overlay-dark').style.display = 'none';  
            document.getElementById('secret-message').style.display = 'none';  
        }  
    </script>  
  
</body>  
</html>  
  
```  
