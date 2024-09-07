<!DOCTYPE html>
<html lang="ko">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://kit.fontawesome.com/5f672c3e52.js" crossorigin="anonymous"></script>
    <title>테스트</title>
    <style>
        @import url("https://cdn.jsdelivr.net/gh/wanteddev/wanted-sans@v1.0.1/packages/wanted-sans/fonts/webfonts/variable/split/WantedSansVariable.min.css");

        :root {
            --dark-outline: rgba(43, 43, 43, 0.466);
            --centerWidth: 80%;
        }

        * {
            color: white;
            box-sizing: border-box;
        }

        body {
            margin: 0;
            padding: 0;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            font-family: "Wanted Sans Variable", "Wanted Sans", -apple-system, BlinkMacSystemFont, sans-serif;
            background-color: rgb(24, 24, 24);
        }

        #topBar-Container {
            width: 100%;
            height: 80px;
            border-bottom: 1px solid var(--dark-outline);
            background: inherit;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }

        .topBar {
            width: var(--centerWidth);
            height: 100%;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        #logoBox {
            position: relative;
            width: 150px;
            border-radius: 10px;
            border: 1px solid var(--dark-outline);
            height: calc(100% - 30px);
            margin: 15px 0;
            background-color: rgba(255, 255, 255, 0.055);
            color: white;
        }

        .menuContainer {
            height: 100%;
            display: flex;
            justify-content: flex-end;
            align-items: center;
            flex-grow: 1;
            margin-left: 15px;
        }

        #mainContent {
            width: var(--centerWidth);
            flex-grow: 1;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: flex-start;
            margin: 0 auto;
            padding-bottom: 50px;
        }

        .scroll-indicator {
            position: absolute;
            bottom: 10px;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            flex-direction: column;
            align-items: center;
            cursor: pointer;
            animation: fadeIn 5s ease-in-out infinite;
            color: white;
        }

        .scroll-indicator .arrow {
            border: solid white;
            border-width: 0 1px 1px 0;
            display: inline-block;
            padding: 10px;
            transform: rotate(45deg);
            animation: bounce 5s infinite;
            margin-bottom: 10px;
        }

        @keyframes bounce {
            0%,
            20%,
            50%,
            80%,
            100% {
                transform: translateY(0) rotate(45deg);
            }

            40% {
                transform: translateY(-10px) rotate(45deg);
            }

            60% {
                transform: translateY(-5px) rotate(45deg);
            }
        }

        @keyframes fadeIn {
            0% {
                opacity: 0;
            }

            100% {
                opacity: 1;
            }
        }

        .scroll-indicator .text {
            font-size: 10px;
            letter-spacing: 2px;
            text-transform: uppercase;
        }

        .sectionContainer {
            display: flex;
            flex-direction: column;
            width: 100%;
        }

        .sectionBox {
            height: 100vh;
            width: 100%;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            color: white;
            border-bottom: 1px solid var(--dark-outline);
        }

        #section-1 {
            height: calc(100vh - 80px);
        }

        .menu {
            margin-left: 40px;
            font-size: 20px;
            font-weight: 600;
        }

        .menu i {
            margin-right: 10px;
            font-size: 15px;
        }

        .smallMenu i {
            margin-right: 5px;
            font-size: 12px;
        }

        .smallMenu {
            margin-left: 30px;
            font-size: 12px;
            font-weight: 400;
            color: rgba(255, 255, 255, 0.822);
        }

        .video-container {
            position: relative;
            width: 80%;
            height: 70%;
            border-radius: 60px;
            overflow: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
            background: rgba(255, 255, 255, 0.1);
            transition: width 0.3s ease;
        }

        .background-video {
            width: 100%;
            height: 100%;
            object-fit: cover;
            opacity: 0.8;
        }

        .slogan {
            position: absolute;
            color: white;
            font-size: 60px;
            text-align: center;
            z-index: 1;
        }

        .sub_slogan {
            position: absolute;
            color: white;
            font-size: 30px;
            margin-top: 150px;
            text-align: center;
            z-index: 1;
        }

        .shrink {
            width: 50% !important;
            height: 60% !important;
        }

        html {
            scroll-behavior: smooth;
        }

        /* Sidebar styles */
        .sidebar {
            position: fixed;
            right: -250px;
            top: 0;
            width: 250px;
            height: 100%;
            background-color: rgba(24, 24, 24, 0.9);
            border-left: 1px solid var(--dark-outline);
            padding: 20px;
            box-shadow: -2px 0 5px rgba(0, 0, 0, 0.5);
            transition: right 0.3s;
            z-index: 100;
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .sidebar.open {
            right: 0;
        }

        .menu-button {
            display: none;
            position: absolute;
            top: 20px;
            right: 20px;
            background: none;
            border: none;
            font-size: 30px;
            color: white;
            cursor: pointer;
            z-index: 101;
        }

        .sidebar .menu-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 5px;
        }

        .sidebar .menu-item i {
            font-size: 24px;
        }

        .sidebar .menu-item .menu-text {
            font-size: 14px;
        }

        @media (max-width: 768px) {
            .menuContainer {
                display: none;
            }

            .menu-button {
                display: block;
            }

            #mainContent {
                width: 100%;
                flex-grow: 1;
                display: flex;
                flex-direction: column;
                align-items: center;
                justify-content: flex-start;
                margin: 0 auto;
                padding-bottom: 50px;
            }
            .topBar {
                width: 100%;
            }

            .logoBox {
                position: relative;
                left: 55px;
            }
        }
    </style>
</head>

<body>
    <button class="menu-button"><i class="fa-solid fa-bars"></i></button>

    <div class="sidebar" id="sidebar">
        <div class="menu-item">
            <i class="fa-solid fa-house"></i>
            <div class="menu-text">홈</div>
        </div>
        <div class="menu-item">
            <i class="fa-solid fa-info-circle"></i>
            <div class="menu-text">소개</div>
        </div>
        <div class="menu-item">
            <i class="fa-solid fa-briefcase"></i>
            <div class="menu-text">프로젝트</div>
        </div>
        <div class="menu-item">
            <i class="fa-solid fa-envelope"></i>
            <div class="menu-text">문의</div>
        </div>
        <div class="menu-item">
            <i class="fa-solid fa-arrow-up-right-from-square"></i>
            <div class="menu-text">링크 1</div>
        </div>
        <div class="menu-item">
            <i class="fa-solid fa-arrow-up-right-from-square"></i>
            <div class="menu-text">링크 2</div>
        </div>
    </div>

    <div class="scroll-indicator">
        <div class="arrow"></div>
        <div class="text">아래로 스크롤</div>
    </div>

    <div id="container">
        <div id="topBar-Container">
            <div class="topBar">
                <div id="logoBox"></div>
                <div class="menuContainer">
                    <div class="menu">홈</div>
                    <div class="menu">소개</div>
                    <div class="menu">프로젝트</div>
                    <div class="menu">문의</div>
                    <div class="menu smallMenu"><i class="fa-solid fa-arrow-up-right-from-square"></i>링크 1</div>
                    <div class="menu smallMenu"><i class="fa-solid fa-arrow-up-right-from-square"></i>링크 2</div>
                </div>
            </div>
        </div>

        <div id="mainContent">
            <div class="sectionContainer">
                <div class="sectionBox" id="section-1">
                    <div class="video-container">
                        <video autoplay muted loop class="background-video">
                            <source src="https://cdn.pixabay.com/video/2019/04/01/22512-328261507_large.mp4"
                                type="video/mp4">
                            Your browser does not support the video tag.
                        </video>
                        <h1 class="slogan">테스트. 테스트 테스트.</h1>
                        <h3 class="sub_slogan">테스트. 테스트 테스트에 대한 설명</h3>
                    </div>

                </div>

                <div class="sectionBox" id="section-2">
                    <h1>다른 섹션</h1>
                    <h3>다른 섹션에 대한 설명</h3>
                </div>
            </div>
        </div>
    </div>

    <script>
        document.addEventListener('scroll', function () {
            const section1 = document.getElementById('section-1');
            const videoContainer = document.querySelector('.video-container');
            const sectionHeight = section1.offsetHeight;
            const scrollPosition = window.scrollY;

            if (scrollPosition > sectionHeight / 4) {
                videoContainer.classList.add('shrink');
            } else {
                videoContainer.classList.remove('shrink');
            }
        });

        // Sidebar toggle functionality
        const menuButton = document.querySelector('.menu-button');
        const sidebar = document.getElementById('sidebar');

        menuButton.addEventListener('click', () => {
            sidebar.classList.toggle('open');
        });
    </script>
</body>

</html>
