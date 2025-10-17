<html lang="zh-CN"><head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>我的个人网站</title>
    <!-- 引入Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- 引入Font Awesome -->
    <link href="https://cdn.jsdelivr.net/npm/font-awesome@4.7.0/css/font-awesome.min.css" rel="stylesheet">
    <!-- 引入Chart.js -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.8/dist/chart.umd.min.js"></script>
    
    <!-- 配置Tailwind -->
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        primary: '#3B82F6',
                        secondary: '#10B981',
                        accent: '#8B5CF6',
                        dark: '#1E293B',
                        light: '#F8FAFC'
                    },
                    fontFamily: {
                        sans: ['Inter', 'system-ui', 'sans-serif'],
                        display: ['Montserrat', 'sans-serif']
                    },
                }
            }
        }
    </script>
    
    <style type="text/tailwindcss">
        @layer utilities {
            .content-auto {
                content-visibility: auto;
            }
            .text-shadow {
                text-shadow: 0 2px 4px rgba(0,0,0,0.1);
            }
            .text-gradient {
                background-clip: text;
                -webkit-background-clip: text;
                color: transparent;
            }
            .bg-blur {
                backdrop-filter: blur(8px);
            }
            .transition-custom {
                transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            }
            .file-drop-active {
                @apply border-primary bg-primary/5;
            }
            .gallery-item {
                @apply relative overflow-hidden rounded-lg shadow-md transition-custom hover:shadow-xl;
            }
            .gallery-overlay {
                @apply absolute inset-0 bg-dark/60 opacity-0 transition-custom flex items-center justify-center hover:opacity-100;
            }
        }
    </style>
    
    <!-- 引入Google字体 -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&amp;family=Montserrat:wght@500;600;700;800&amp;display=swap" rel="stylesheet">
</head>

<body class="bg-light text-dark antialiased">
    <!-- 导航栏 -->
    <nav id="main-nav" class="fixed w-full z-50 transition-custom bg-transparent">
        <div class="container mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center py-4">
                <a href="#home" class="text-2xl font-display font-bold text-white text-shadow">
                    <span id="nav-logo">JCZ的网站</span>
                </a>
                
                <!-- 桌面导航 -->
                <div class="hidden md:flex space-x-8">
                    <a href="#home" class="nav-link text-white hover:text-primary transition-custom">首页</a>
                    <a href="#about" class="nav-link text-white hover:text-primary transition-custom">关于我</a>
                    <a href="#portfolio" class="nav-link text-white hover:text-primary transition-custom">作品集</a>
                    <a href="#gallery" class="nav-link text-white hover:text-primary transition-custom">照片</a>
                    <a href="#documents" class="nav-link text-white hover:text-primary transition-custom">文件上传</a>
                    <a href="#contact" class="nav-link text-white hover:text-primary transition-custom">联系我</a>
                    <button id="admin-btn" class="text-white hover:text-primary transition-custom">
                        <i class="fa fa-cog mr-1"></i> 管理
                    </button>
                </div>
                
                <!-- 移动端菜单按钮 -->
                <button id="mobile-menu-btn" class="md:hidden text-white focus:outline-none">
                    <i class="fa fa-bars text-2xl"></i>
                </button>
            </div>
        </div>
        
        <!-- 移动端导航菜单 -->
        <div id="mobile-menu" class="md:hidden hidden bg-dark/90 bg-blur">
            <div class="container mx-auto px-4 py-3 space-y-3">
                <a href="#home" class="block py-2 text-white hover:text-primary transition-custom">首页</a>
                <a href="#about" class="block py-2 text-white hover:text-primary transition-custom">关于我</a>
                <a href="#portfolio" class="block py-2 text-white hover:text-primary transition-custom">作品集</a>
                <a href="#gallery" class="block py-2 text-white hover:text-primary transition-custom">照片</a>
                <a href="#documents" class="block py-2 text-white hover:text-primary transition-custom">文件上传</a>
                <a href="#contact" class="block py-2 text-white hover:text-primary transition-custom">联系我</a>
                <button id="mobile-admin-btn" class="w-full text-left py-2 text-white hover:text-primary transition-custom">
                    <i class="fa fa-cog mr-1"></i> 管理
                </button>
            </div>
        </div>
    </nav>

    <!-- 主内容区 -->
    <main id="main-content">
        <!-- 首页/英雄区 -->
        <section id="home" class="min-h-screen flex items-center relative overflow-hidden">
            <div class="absolute inset-0 z-0">
                <div id="hero-bg" class="absolute inset-0 bg-cover bg-center" style="background-image: url('https://picsum.photos/id/1005/1920/1080'); filter: brightness(0.6);"></div>
            </div>
            
            <div class="container mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
                <div class="max-w-3xl">
                    <h1 id="hero-title" class="text-[clamp(2.5rem,8vw,5rem)] font-display font-bold text-white leading-tight mb-6 animate-fade-in">
                        你好，我是<span class="text-primary">姜成卓</span>
                    </h1>
                    <p class="text-[clamp(1.2rem,4vw,1.8rem)] font-display text-white/90 mb-6">或者你也可以叫我 Sam</p>
                    <p id="hero-subtitle" class="text-[clamp(1rem,3vw,1.5rem)] text-white/90 mb-8 max-w-2xl">欢迎来到我的个人网站，这里展示了我的简历、作品和生活点滴。</p>
                    <div class="flex flex-wrap gap-4">
                        <a href="#about" class="px-8 py-3 bg-primary hover:bg-primary/90 text-white font-medium rounded-lg shadow-lg hover:shadow-xl transform hover:-translate-y-1 transition-custom">
                            了解更多
                        </a>
                        <a href="#portfolio" class="px-8 py-3 bg-white/10 hover:bg-white/20 backdrop-blur text-white font-medium rounded-lg border border-white/30 hover:shadow-lg transform hover:-translate-y-1 transition-custom">
                            查看作品
                        </a>
                    </div>
                </div>
            </div>
            
            <div class="absolute bottom-10 left-1/2 transform -translate-x-1/2 text-white animate-bounce">
                <a href="#about" class="flex flex-col items-center">
                    <span class="mb-2 text-sm">向下滚动</span>
                    <i class="fa fa-chevron-down"></i>
                </a>
            </div>
        </section>

        <!-- 关于/简历部分 -->
        <section id="about" class="py-20 bg-white">
            <div class="container mx-auto px-4 sm:px-6 lg:px-8">
                <div class="text-center mb-16">
                    <h2 class="text-[clamp(1.5rem,3vw,2.5rem)] font-display font-bold mb-4">关于我</h2>
                    <div class="w-20 h-1 bg-primary mx-auto"></div>
                </div>
                
                <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
                    <div class="order-2 lg:order-1">
                        <div id="about-content" class="space-y-6">
                            <h3 class="text-2xl font-display font-semibold text-dark">个人简介</h3>
                            <p id="about-bio" class="text-gray-600 leading-relaxed">我是一个有着工科背景的文科生，因为对文学的热爱和对现实帮助他人的渴望选择了从工科转到文科，在这一过程中我学了不少新的知识，并逐渐追求更全面的学科性发展。我力求在生活、学习和工作中找到平衡点，不断探寻生活和学习中的乐趣。</p>
                            
                            <h3 class="text-2xl font-display font-semibold text-dark">教育背景</h3>
                            <div id="education-container" class="space-y-4">
                                <div class="bg-gray-50 p-4 rounded-lg shadow-sm">
                                    <div class="flex justify-between items-start">
                                        <div>
                                            <h4 class="font-semibold text-lg">Lingnan University</h4>
                                            <p class="text-gray-500">Master of Social Sciences in Comparative Public Administration (CPA)</p>
                                        </div>
                                        <span class="bg-gray-200 px-3 py-1 rounded-full text-sm">2025</span>
                                    </div>
                                </div>
                                <div class="bg-gray-50 p-4 rounded-lg shadow-sm">
                                    <div class="flex justify-between items-start">
                                        <div>
                                            <h4 class="font-semibold text-lg">Henan University of Science and Technology</h4>
                                            <p class="text-gray-500">Bachelor of Engineering– Major in Automation</p>
                                        </div>
                                        <span class="bg-gray-200 px-3 py-1 rounded-full text-sm">2023</span>
                                    </div>
                                </div>
                            </div>
                            
                            <h3 class="text-2xl font-display font-semibold text-dark">工作经历</h3>
                            <div id="experience-container" class="space-y-4">
                                <div class="bg-gray-50 p-4 rounded-lg shadow-sm">
                                    <div class="flex justify-between items-start">
                                        <div>
                                            <h4 class="font-semibold text-lg">Office Assistant - Hong Kong Center for Construction Robotics (HKCRC)</h4>
                                            <p class="text-gray-500">Using Ps/AI and poster design apps to create promotional materials for events, optimized publicity content based on social media.</p>
                                        </div>
                                        <span class="bg-gray-200 px-3 py-1 rounded-full text-sm">2025</span>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <div class="order-1 lg:order-2 flex justify-center">
                        <div class="relative">
                            <div id="profile-picture-container" class="w-64 h-64 sm:w-80 sm:h-80 rounded-full overflow-hidden border-4 border-primary shadow-xl">
                                <img id="profile-picture" src="https://p9-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/code_assistant/5a964c03dc504bb38d24baf4b5bd9e89~tplv-a9rns2rl98-image.image?rcl=20251010014412E866C50F0E19E8A31EF9&amp;rk3s=8e244e95&amp;rrcfp=e75484ac&amp;x-expires=1760636653&amp;x-signature=MK31EzJ0dkNjjOHx1tzAjJwi4So%3D" alt="个人照片" class="w-full h-full object-cover">
                            </div>
                            <div class="absolute -bottom-4 -right-4 bg-secondary text-white p-4 rounded-lg shadow-lg">
                                <div id="age-display" class="text-2xl font-bold">24</div>
                                <div class="text-sm">年龄</div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- 技能部分 -->
                <div class="mt-20">
                    <h3 class="text-2xl font-display font-semibold text-dark mb-8 text-center">我的技能</h3>
                    <div id="skills-container" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
                        <div class="bg-gray-50 p-6 rounded-lg shadow-sm hover:shadow-md transition-custom">
                            <div class="flex items-center mb-3">
                                <i class="fa fa-adobe text-primary text-xl mr-3"></i>
                                <h4 class="font-semibold">Photoshop/Illustrator</h4>
                            </div>
                            <div class="w-full bg-gray-200 rounded-full h-2.5">
                                <div class="bg-primary h-2.5 rounded-full" style="width: 85%"></div>
                            </div>
                        </div>
                        <div class="bg-gray-50 p-6 rounded-lg shadow-sm hover:shadow-md transition-custom">
                            <div class="flex items-center mb-3">
                                <i class="fa fa-paint-brush text-primary text-xl mr-3"></i>
                                <h4 class="font-semibold">AI设计</h4>
                            </div>
                            <div class="w-full bg-gray-200 rounded-full h-2.5">
                                <div class="bg-primary h-2.5 rounded-full" style="width: 80%"></div>
                            </div>
                        </div>
                        <div class="bg-gray-50 p-6 rounded-lg shadow-sm hover:shadow-md transition-custom">
                            <div class="flex items-center mb-3">
                                <i class="fa fa-bullhorn text-primary text-xl mr-3"></i>
                                <h4 class="font-semibold">海报设计</h4>
                            </div>
                            <div class="w-full bg-gray-200 rounded-full h-2.5">
                                <div class="bg-primary h-2.5 rounded-full" style="width: 90%"></div>
                            </div>
                        </div>
                        <div class="bg-gray-50 p-6 rounded-lg shadow-sm hover:shadow-md transition-custom">
                            <div class="flex items-center mb-3">
                                <i class="fa fa-share-alt text-primary text-xl mr-3"></i>
                                <h4 class="font-semibold">社交媒体宣传</h4>
                            </div>
                            <div class="w-full bg-gray-200 rounded-full h-2.5">
                                <div class="bg-primary h-2.5 rounded-full" style="width: 85%"></div>
                            </div>
                        </div>
                        <div class="bg-gray-50 p-6 rounded-lg shadow-sm hover:shadow-md transition-custom">
                            <div class="flex items-center mb-3">
                                <i class="fa fa-file-image-o text-primary text-xl mr-3"></i>
                                <h4 class="font-semibold">活动宣传材料制作</h4>
                            </div>
                            <div class="w-full bg-gray-200 rounded-full h-2.5">
                                <div class="bg-primary h-2.5 rounded-full" style="width: 88%"></div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- 作品集部分 -->
        <section id="portfolio" class="py-20 bg-gray-50">
            <div class="container mx-auto px-4 sm:px-6 lg:px-8">
                <div class="text-center mb-16">
                    <h2 class="text-[clamp(1.5rem,3vw,2.5rem)] font-display font-bold mb-4">我的作品集</h2>
                    <p class="text-gray-600 max-w-2xl mx-auto">以下是我设计的一些海报和宣传材料，展示了我的设计能力和创意</p>
                    <div class="w-20 h-1 bg-primary mx-auto mt-4"></div>
                </div>
                
                <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
                    <!-- 作品1 -->
                    <div class="bg-white rounded-xl overflow-hidden shadow-md hover:shadow-xl transition-custom group">
                        <div class="relative overflow-hidden">
                            <img src="https://p3-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/code_assistant/fdaefc5c325646938349805fa73d6847~tplv-a9rns2rl98-image.image?rcl=20251010030438BE50C081EBC88D9D4929&amp;rk3s=8e244e95&amp;rrcfp=e75484ac&amp;x-expires=1760641478&amp;x-signature=JeoGkSJVfYE3RQIo6cdq3J9UNa4%3D" alt="活动海报设计" class="w-full h-64 object-cover transition-custom group-hover:scale-105">
                            <div class="absolute top-4 right-4 bg-primary text-white text-sm px-3 py-1 rounded-full">
                                海报设计
                            </div>
                        </div>
                        <div class="p-6">
                            <h3 class="text-xl font-semibold mb-2">户外活动宣传海报</h3>
                            <p class="text-gray-600 mb-4">为大学户外活动设计的宣传海报，结合了动漫和动物风格</p>
                            <a href="#" class="inline-flex items-center text-primary font-medium hover:underline">
                                查看详情 <i class="fa fa-arrow-right ml-2"></i>
                            </a>
                        </div>
                    </div>
                    
                    <!-- 作品2 -->
                    <div class="bg-white rounded-xl overflow-hidden shadow-md hover:shadow-xl transition-custom group">
                        <div class="relative overflow-hidden">
                            <img src="https://p3-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/code_assistant/59f26894cc714d06b115679b12224228~tplv-a9rns2rl98-image.image?rcl=2025101002550903AC092BC60D95902370&amp;rk3s=8e244e95&amp;rrcfp=e75484ac&amp;x-expires=1760640909&amp;x-signature=qLnkgR3fnTxtmbqr2Q1El2XV2dU%3D" alt="社交媒体宣传图" class="w-full h-64 object-cover transition-custom group-hover:scale-105">
                            <div class="absolute top-4 right-4 bg-accent text-white text-sm px-3 py-1 rounded-full">
                                社交媒体
                            </div>
                        </div>
                        <div class="p-6">
                            <h3 class="text-xl font-semibold mb-2">闲暇活动经营B站</h3>
                            <p class="text-gray-600 mb-4">主要进行游戏直播和游戏解说，主打消磨时光、锻炼剪辑能力</p>
                            <a href="#" class="inline-flex items-center text-primary font-medium hover:underline">
                                查看详情 <i class="fa fa-arrow-right ml-2"></i>
                            </a>
                        </div>
                    </div>
                    
                    <!-- 作品3 -->
                    <div class="bg-white rounded-xl overflow-hidden shadow-md hover:shadow-xl transition-custom group">
                        <div class="relative overflow-hidden">
                            <img src="https://p3-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/code_assistant/c815583a076343c284ad8da3cb163e5d~tplv-a9rns2rl98-image.image?rcl=202510100252065D4F7B0E5F7228DBDEFE&amp;rk3s=8e244e95&amp;rrcfp=e75484ac&amp;x-expires=1760640727&amp;x-signature=OJpZgNTvI%2FRII6sZKI6M%2Fi80nsE%3D" alt="活动手册设计" class="w-full h-64 object-cover transition-custom group-hover:scale-105">
                            <div class="absolute top-4 right-4 bg-secondary text-white text-sm px-3 py-1 rounded-full">
                                印刷设计
                            </div>
                        </div>
                        <div class="p-6">
                            <h3 class="text-xl font-semibold mb-2">指导手册设计</h3>
                            <p class="text-gray-600 mb-4">为湾区竞赛夏令营设计的指导手册，包含封面和内页排版设计</p>
                            <a href="#" class="inline-flex items-center text-primary font-medium hover:underline">
                                查看详情 <i class="fa fa-arrow-right ml-2"></i>
                            </a>
                        </div>
                    </div>
                    
                    <!-- 作品4 -->
                    <div class="bg-white rounded-xl overflow-hidden shadow-md hover:shadow-xl transition-custom group">
                        <div class="relative overflow-hidden">
                            <img src="https://picsum.photos/id/20/600/400" alt="AI生成艺术作品" class="w-full h-64 object-cover transition-custom group-hover:scale-105">
                            <div class="absolute top-4 right-4 bg-accent text-white text-sm px-3 py-1 rounded-full">AI设计</div>
                        </div>
                        <div class="p-6">
                            <h3 class="text-xl font-semibold mb-2">AI辅助创意图片</h3>
                            <p class="text-gray-600 mb-4">灵活运用AI工具创作的创意图片，我很乐意探索AI与设计的结合</p>
                            <a href="#" class="inline-flex items-center text-primary font-medium hover:underline">
                                查看详情 <i class="fa fa-arrow-right ml-2"></i>
                            </a>
                        </div>
                    </div>
                    
                    <!-- 作品5 -->
                    <div class="bg-white rounded-xl overflow-hidden shadow-md hover:shadow-xl transition-custom group">
                        <div class="relative overflow-hidden">
                            <img src="https://p9-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/code_assistant/dfef1d5f33fa4c6da209c506965dc160~tplv-a9rns2rl98-image.image?rcl=202510100301028DDF84DC6CCAD18DEBF8&amp;rk3s=8e244e95&amp;rrcfp=e75484ac&amp;x-expires=1760641263&amp;x-signature=mB2pqiVV1VRGM6WUKfIkhhpDmJE%3D" alt="环保主题海报" class="w-full h-64 object-cover transition-custom group-hover:scale-105">
                            <div class="absolute top-4 right-4 bg-primary text-white text-sm px-3 py-1 rounded-full">建模设计</div>
                        </div>
                        <div class="p-6">
                            <h3 class="text-xl font-semibold mb-2">Blender建模设计</h3>
                            <p class="text-gray-600 mb-4">除了简单的立体logo外、还能熟练进行展厅或部分物体细节的建模</p>
                            <a href="#" class="inline-flex items-center text-primary font-medium hover:underline">
                                查看详情 <i class="fa fa-arrow-right ml-2"></i>
                            </a>
                        </div>
                    </div>
                    
                    <!-- 作品6 -->
                    <div class="bg-white rounded-xl overflow-hidden shadow-md hover:shadow-xl transition-custom group">
                        <div class="relative overflow-hidden">
                            <img src="https://p9-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/code_assistant/d301382d3519414b9f7ab28d11e7659e~tplv-a9rns2rl98-image.image?rcl=20251010030007AA3A595C79ED21C8D28A&amp;rk3s=8e244e95&amp;rrcfp=e75484ac&amp;x-expires=1760641208&amp;x-signature=zAB%2Bz4lPoqdwcFJA9FWBiUSaqME%3D" alt="应用界面设计" class="w-full h-64 object-cover transition-custom group-hover:scale-105">
                            <div class="absolute top-4 right-4 bg-secondary text-white text-sm px-3 py-1 rounded-full">Logo设计</div>
                        </div>
                        <div class="p-6">
                            <h3 class="text-xl font-semibold mb-2">LOGO排版设计</h3>
                            <p class="text-gray-600 mb-4">实习时曾参与LOGO排版设计、LOGO的修改与重新装饰等工作</p>
                            <a href="#" class="inline-flex items-center text-primary font-medium hover:underline">
                                查看详情 <i class="fa fa-arrow-right ml-2"></i>
                            </a>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- 照片部分 -->
        <section id="gallery" class="py-20 bg-white">
            <div class="container mx-auto px-4 sm:px-6 lg:px-8">
                <div class="text-center mb-16">
                    <h2 class="text-[clamp(1.5rem,3vw,2.5rem)] font-display font-bold mb-4">我的照片</h2>
                    <p class="text-gray-600 max-w-2xl mx-auto">记录生活中的美好瞬间，旅行、学习和日常点滴</p>
                    <div class="w-20 h-1 bg-primary mx-auto mt-4"></div>
                </div>
                
                <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4">
                    <!-- 照片1 -->
                    <div class="gallery-item">
                        <img src="https://p3-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/code_assistant/925c3ec3f2e0409cac002eae58e74c6b~tplv-a9rns2rl98-image.image?rcl=20251010030740034CBDB8D48B1DC62C91&amp;rk3s=8e244e95&amp;rrcfp=e75484ac&amp;x-expires=1760641660&amp;x-signature=s0Doo9M7hQBiDMcE13%2FGMb%2FubAI%3D" alt="风景照" class="w-full h-64 object-cover">
                        <div class="gallery-overlay">
                            <button class="bg-white text-primary p-2 rounded-full">
                                <i class="fa fa-search-plus"></i>
                            </button>
                        </div>
                    </div>
                    
                    <!-- 照片2 -->
                    <div class="gallery-item">
                        <img src="https://p3-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/code_assistant/6e6a4cd848604997ae8d76045e8d4bd9~tplv-a9rns2rl98-image.image?rcl=20251010030750C8CDF9FA401E3DBB241D&amp;rk3s=8e244e95&amp;rrcfp=e75484ac&amp;x-expires=1760641671&amp;x-signature=fSP8Oz4dvu%2BLbJdOout%2FRd%2BSTQk%3D" alt="建筑照" class="w-full h-64 object-cover">
                        <div class="gallery-overlay">
                            <button class="bg-white text-primary p-2 rounded-full">
                                <i class="fa fa-search-plus"></i>
                            </button>
                        </div>
                    </div>
                    
                    <!-- 照片3 -->
                    <div class="gallery-item">
                        <img src="https://p3-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/code_assistant/5f9b723d55ec4815b38a46d189adddfc~tplv-a9rns2rl98-image.image?rcl=20251010030801E6F3E821FC2A579224EC&amp;rk3s=8e244e95&amp;rrcfp=e75484ac&amp;x-expires=1760641681&amp;x-signature=ANKt3wfX7DCx7GDrHbytjK4799Y%3D" alt="自然照" class="w-full h-64 object-cover">
                        <div class="gallery-overlay">
                            <button class="bg-white text-primary p-2 rounded-full">
                                <i class="fa fa-search-plus"></i>
                            </button>
                        </div>
                    </div>
                    
                    <!-- 照片4 -->
                    <div class="gallery-item">
                        <img src="https://p3-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/code_assistant/57c236d1e98c47798151b14805396e4b~tplv-a9rns2rl98-image.image?rcl=2025101003090750A58B24E282B889FDF1&amp;rk3s=8e244e95&amp;rrcfp=e75484ac&amp;x-expires=1760641748&amp;x-signature=7Vv8UtcjBQqRTpv2in4v8QdJAI8%3D" alt="城市照" class="w-full h-64 object-cover">
                        <div class="gallery-overlay">
                            <button class="bg-white text-primary p-2 rounded-full">
                                <i class="fa fa-search-plus"></i>
                            </button>
                        </div>
                    </div>
                    
                    <!-- 照片5 -->
                    <div class="gallery-item">
                        <img src="https://p9-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/code_assistant/98b9be34fa0f4289ba4497af36e4f0df~tplv-a9rns2rl98-image.image?rcl=202510100309175C8EDE1199B445C7BA59&amp;rk3s=8e244e95&amp;rrcfp=e75484ac&amp;x-expires=1760641757&amp;x-signature=BgmX9Q2D%2FIV3EFrwUgrJZg21%2F0Y%3D" alt="静物照" class="w-full h-64 object-cover">
                        <div class="gallery-overlay">
                            <button class="bg-white text-primary p-2 rounded-full">
                                <i class="fa fa-search-plus"></i>
                            </button>
                        </div>
                    </div>
                    
                    <!-- 照片6 -->
                    <div class="gallery-item">
                        <img src="https://p9-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/code_assistant/c7b4f1eaef4e482e8176497b11dbedef~tplv-a9rns2rl98-image.image?rcl=20251010030955DDEBB818ED144FCFC54F&amp;rk3s=8e244e95&amp;rrcfp=e75484ac&amp;x-expires=1760641796&amp;x-signature=exZDdhf754Wp%2F2vo%2FEeFCoOqMEc%3D" alt="旅行照" class="w-full h-64 object-cover">
                        <div class="gallery-overlay">
                            <button class="bg-white text-primary p-2 rounded-full">
                                <i class="fa fa-search-plus"></i>
                            </button>
                        </div>
                    </div>
                </div>
                
                <!-- 查看更多按钮 -->
                <div class="text-center mt-12">
                    <button id="load-more-photos" class="px-6 py-3 bg-primary hover:bg-primary/90 text-white font-medium rounded-lg shadow hover:shadow-md transition-custom">
                        <i class="fa fa-picture-o mr-2"></i>查看更多照片
                    </button>
                </div>
            </div>
        </section>

        <!-- 文件上传页面 -->
        <section id="documents" class="py-20 bg-gray-50">
            <div class="container mx-auto px-4 sm:px-6 lg:px-8">
                <div class="text-center mb-16">
                    <h2 class="text-[clamp(1.5rem,3vw,2.5rem)] font-display font-bold mb-4">我的简历和作品集</h2>
                    <p class="text-gray-600 max-w-2xl mx-auto">以下文件均可下载</p>
                    <div class="w-20 h-1 bg-primary mx-auto mt-4"></div>
                </div>
                
                <!-- 文件上传区域 -->
                <div class="max-w-3xl mx-auto mb-16">
                    <div id="file-drop-area" class="border-2 border-dashed border-gray-300 rounded-xl p-10 text-center hover:border-primary transition-custom cursor-pointer">
                        <input type="file" id="file-input" class="hidden" multiple="" accept=".pdf,.doc,.docx,.xls,.xlsx,.ppt,.pptx">
                        
                        <div class="flex flex-col items-center">
                            <i class="fa fa-cloud-upload text-5xl text-primary mb-4"></i>
                            <h3 class="text-xl font-semibold mb-2">拖放文件到这里上传</h3>
                            <p class="text-gray-500 mb-6">支持 PDF, Word, Excel, PowerPoint 等格式</p>
                            <button id="browse-files-btn" class="px-6 py-2 bg-primary hover:bg-primary/90 text-white font-medium rounded-lg shadow hover:shadow-md transition-custom">
                                <i class="fa fa-folder-open mr-2"></i>浏览文件
                            </button>
                        </div>
                        
                        <!-- 上传进度条 (默认隐藏) -->
                        <div id="upload-progress" class="hidden mt-6">
                            <div class="w-full bg-gray-200 rounded-full h-2.5">
                                <div id="progress-bar" class="bg-primary h-2.5 rounded-full" style="width: 0%"></div>
                            </div>
                            <p id="progress-text" class="text-sm text-gray-500 mt-2">准备上传...</p>
                        </div>
                    </div>
                </div>
                
                <!-- 已上传文件列表 -->
                <div class="max-w-4xl mx-auto">
                    <h3 class="text-xl font-semibold mb-6 flex items-center">
                        <i class="fa fa-file-text-o text-primary mr-2"></i>已上传文件
                    </h3>
                    
                    <div id="uploaded-files-list" class="space-y-4">
                        <!-- 已上传文件将通过JavaScript动态添加 -->
                        <div class="text-center text-gray-500 py-10">
                            <i class="fa fa-folder-open-o text-4xl mb-4 opacity-30"></i>
                            <p>暂无上传的文件</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- 联系部分 -->
        <section id="contact" class="py-20 bg-white">
            <div class="container mx-auto px-4 sm:px-6 lg:px-8">
                <div class="text-center mb-16">
                    <h2 class="text-[clamp(1.5rem,3vw,2.5rem)] font-display font-bold mb-4">联系我</h2>
                    <p class="text-gray-600 max-w-2xl mx-auto">如果您有任何问题或合作意向，欢迎随时联系我</p>
                    <div class="w-20 h-1 bg-primary mx-auto mt-4"></div>
                </div>
                
                <div class="grid grid-cols-1 lg:grid-cols-2 gap-12">
                    <!-- 联系表单 -->
                    <div>
                        <form id="contact-form" class="bg-gray-50 p-8 rounded-xl shadow-sm">
                            <div class="mb-6">
                                <label for="name" class="block text-gray-700 font-medium mb-2">姓名</label>
                                <input type="text" id="name" name="name" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-primary focus:border-transparent transition-custom" placeholder="请输入您的姓名">
                            </div>
                            
                            <div class="mb-6">
                                <label for="email" class="block text-gray-700 font-medium mb-2">邮箱</label>
                                <input type="email" id="email" name="email" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-primary focus:border-transparent transition-custom" placeholder="请输入您的邮箱">
                            </div>
                            
                            <div class="mb-6">
                                <label for="subject" class="block text-gray-700 font-medium mb-2">主题</label>
                                <input type="text" id="subject" name="subject" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-primary focus:border-transparent transition-custom" placeholder="请输入消息主题">
                            </div>
                            
                            <div class="mb-6">
                                <label for="message" class="block text-gray-700 font-medium mb-2">消息</label>
                                <textarea id="message" name="message" rows="5" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-primary focus:border-transparent transition-custom" placeholder="请输入您的消息内容"></textarea>
                            </div>
                            
                            <button type="submit" class="w-full py-3 bg-primary hover:bg-primary/90 text-white font-medium rounded-lg shadow hover:shadow-md transition-custom">
                                <i class="fa fa-paper-plane mr-2"></i>发送消息
                            </button>
                        </form>
                    </div>
                    
                    <!-- 联系信息 -->
                    <div class="flex flex-col justify-center">
                        <div class="space-y-8">
                            <div>
                                <h3 class="text-2xl font-display font-semibold mb-6">联系方式</h3>
                                
                                <div class="space-y-4">
                                    <div class="flex items-start">
                                        <div class="bg-primary/10 p-3 rounded-full text-primary mr-4">
                                            <i class="fa fa-envelope"></i>
                                        </div>
                                        <div>
                                            <h4 class="font-medium text-lg">邮箱</h4>
                                            <p class="text-gray-600">tuanduituandui@gmail.com</p>
                                        </div>
                                    </div>
                                    
                                    <div class="flex items-start">
                                        <div class="bg-primary/10 p-3 rounded-full text-primary mr-4">
                                            <i class="fa fa-phone"></i>
                                        </div>
                                        <div>
                                            <h4 class="font-medium text-lg">电话</h4>
                                            <p class="text-gray-600">+852 90535020&nbsp; &nbsp; &nbsp; +86 15539371673</p>
                                        </div>
                                    </div>
                                    
                                    <div class="flex items-start">
                                        <div class="bg-primary/10 p-3 rounded-full text-primary mr-4">
                                            <i class="fa fa-map-marker"></i>
                                        </div>
                                        <div>
                                            <h4 class="font-medium text-lg">地址</h4>
                                            <p class="text-gray-600">8B2, Tower 6, St.Martin, 12 Fo Chun Road, Tai Po</p>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            
                            <div>
                                <h3 class="text-2xl font-display font-semibold mb-6">社交媒体</h3>
                                
                                <div class="flex flex-wrap gap-4">
                                    <a href="https://instagram.com" target="_blank" class="bg-primary/10 hover:bg-primary/20 text-primary p-3 rounded-full transition-custom" title="Instagram">
                                        <i class="fa fa-instagram"></i>
                                    </a>
                                    <a href="https://bilibili.com" target="_blank" class="bg-primary/10 hover:bg-primary/20 text-primary p-3 rounded-full transition-custom" title="Bilibili">
                                        <i class="fa fa-play-circle"></i>
                                    </a>
                                    <a href="https://linkedin.com" target="_blank" class="bg-primary/10 hover:bg-primary/20 text-primary p-3 rounded-full transition-custom" title="LinkedIn">
                                        <i class="fa fa-linkedin"></i>
                                    </a>
                                    <a href="#" class="bg-primary/10 hover:bg-primary/20 text-primary p-3 rounded-full transition-custom" title="微信">
                                        <i class="fa fa-weixin"></i>
                                    </a>
                                    <a href="https://wa.me/85290535020" target="_blank" class="bg-primary/10 hover:bg-primary/20 text-primary p-3 rounded-full transition-custom" title="WhatsApp">
                                        <i class="fa fa-whatsapp"></i>
                                    </a>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>
    </main>

    <!-- 页脚 -->
    <footer class="bg-dark text-white py-12">
        <div class="container mx-auto px-4 sm:px-6 lg:px-8">
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
                <div>
                    <h3 class="text-xl font-display font-bold mb-4">姜成卓</h3>
                    <p class="text-gray-400 mb-4">
                        拥有工科背景的文科生，热爱设计与创作，追求全面发展
                    </p>
                    <div class="flex space-x-4">
                        <a href="https://www.instagram.com/iwater.meloni/?next=%2F" target="_blank" class="text-gray-400 hover:text-white transition-custom" title="Instagram">
                            <i class="fa fa-instagram"></i>
                        </a>
                        <a href="https://space.bilibili.com/177778970?spm_id_from=333.1007.0.0" target="_blank" class="text-gray-400 hover:text-white transition-custom" title="Bilibili">
                            <i class="fa fa-play-circle"></i>
                        </a>
                        <a href="https://www.linkedin.com/in/chengzhuo-jiang-9b9807325/" target="_blank" class="text-gray-400 hover:text-white transition-custom" title="LinkedIn">
                            <i class="fa fa-linkedin"></i>
                        </a>
                        <a href="#" class="text-gray-400 hover:text-white transition-custom" title="微信">
                            <i class="fa fa-weixin"></i>
                        </a>
                        <a href="https://wa.me/85290535020" target="_blank" class="text-gray-400 hover:text-white transition-custom" title="WhatsApp">
                            <i class="fa fa-whatsapp"></i>
                        </a>
                    </div>
                </div>
                
                <div>
                    <h3 class="text-lg font-semibold mb-4">快速链接</h3>
                    <ul class="space-y-2">
                        <li><a href="#home" class="text-gray-400 hover:text-white transition-custom">首页</a></li>
                        <li><a href="#about" class="text-gray-400 hover:text-white transition-custom">关于我</a></li>
                        <li><a href="#portfolio" class="text-gray-400 hover:text-white transition-custom">作品集</a></li>
                        <li><a href="#gallery" class="text-gray-400 hover:text-white transition-custom">照片</a></li>
                        <li><a href="#documents" class="text-gray-400 hover:text-white transition-custom">文件上传</a></li>
                        <li><a href="#contact" class="text-gray-400 hover:text-white transition-custom">联系我</a></li>
                    </ul>
                </div>
                
                <div>
                    <h3 class="text-lg font-semibold mb-4">服务</h3>
                    <ul class="space-y-2">
                        <li><a href="#" class="text-gray-400 hover:text-white transition-custom">海报设计</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white transition-custom">社交媒体宣传</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white transition-custom">活动材料制作</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white transition-custom">AI辅助设计</a></li>
                    </ul>
                </div>
                
                <div>
                    <h3 class="text-lg font-semibold mb-4">联系信息</h3>
                    <ul class="space-y-2">
                        <li class="flex items-center text-gray-400">
                            <i class="fa fa-envelope mr-2"></i>
                            <span>tuanduituandui@gmail.com</span>
                        </li>
                        <li class="flex items-center text-gray-400">
                            <i class="fa fa-phone mr-2"></i>
                            <span>+852 90535020</span>
                        </li>
                        <li class="flex items-start text-gray-400">
                            <i class="fa fa-map-marker mr-2 mt-1"></i>
                            <span>08/F, Tower 6, St. Martin, Pak Shek Kok, Tai Po</span>
                        </li>
                    </ul>
                </div>
            </div>
            
            <div class="border-t border-gray-800 mt-10 pt-6 flex flex-col md:flex-row justify-between items-center">
                <p class="text-gray-400 text-sm">© 2025 Jcz. 保留所有权利.</p>
                <div class="mt-4 md:mt-0">
                    <ul class="flex space-x-6">
                        <li><a href="#" class="text-gray-400 hover:text-white text-sm transition-custom">隐私政策</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white text-sm transition-custom">使用条款</a></li>
                    </ul>
                </div>
            </div>
        </div>
    </footer>

    <!-- JavaScript 代码 -->
    <script>
        // 导航栏滚动效果
        window.addEventListener('scroll', function() {
            const nav = document.getElementById('main-nav');
            if (window.scrollY > 50) {
                nav.classList.add('bg-dark/90', 'bg-blur', 'shadow-lg');
                nav.classList.remove('bg-transparent');
            } else {
                nav.classList.remove('bg-dark/90', 'bg-blur', 'shadow-lg');
                nav.classList.add('bg-transparent');
            }
        });

        // 移动端菜单切换
        document.getElementById('mobile-menu-btn').addEventListener('click', function() {
            const mobileMenu = document.getElementById('mobile-menu');
            mobileMenu.classList.toggle('hidden');
        });

        // 文件上传功能实现
        document.addEventListener('DOMContentLoaded', function() {
            const fileDropArea = document.getElementById('file-drop-area');
            const fileInput = document.getElementById('file-input');
            const browseFilesBtn = document.getElementById('browse-files-btn');
            const uploadProgress = document.getElementById('upload-progress');
            const progressBar = document.getElementById('progress-bar');
            const progressText = document.getElementById('progress-text');
            const uploadedFilesList = document.getElementById('uploaded-files-list');
            
            // 支持的文件类型和图标映射
            const fileTypes = {
                'pdf': 'fa-file-pdf-o text-red-500',
                'doc': 'fa-file-word-o text-blue-500',
                'docx': 'fa-file-word-o text-blue-500',
                'xls': 'fa-file-excel-o text-green-500',
                'xlsx': 'fa-file-excel-o text-green-500',
                'ppt': 'fa-file-powerpoint-o text-orange-500',
                'pptx': 'fa-file-powerpoint-o text-orange-500'
            };
            
            // 从本地存储加载已上传的文件
            loadUploadedFiles();
            
            // 点击浏览文件按钮
            browseFilesBtn.addEventListener('click', function() {
                fileInput.click();
            });
            
            // 文件选择变化时
            fileInput.addEventListener('change', function() {
                if (this.files.length > 0) {
                    uploadFiles(this.files);
                }
            });
            
            // 拖放功能
            fileDropArea.addEventListener('dragover', function(e) {
                e.preventDefault();
                fileDropArea.classList.add('file-drop-active');
            });
            
            fileDropArea.addEventListener('dragleave', function() {
                fileDropArea.classList.remove('file-drop-active');
            });
            
            fileDropArea.addEventListener('drop', function(e) {
                e.preventDefault();
                fileDropArea.classList.remove('file-drop-active');
                
                if (e.dataTransfer.files.length > 0) {
                    uploadFiles(e.dataTransfer.files);
                }
            });
            
            // 模拟文件上传
            function uploadFiles(files) {
                // 过滤不支持的文件类型
                const validFiles = Array.from(files).filter(file => {
                    const ext = file.name.split('.').pop().toLowerCase();
                    return Object.keys(fileTypes).includes(ext);
                });
                
                if (validFiles.length === 0) {
                    alert('请上传支持的文件类型: PDF, Word, Excel, PowerPoint');
                    return;
                }
                
                // 显示上传进度
                uploadProgress.classList.remove('hidden');
                progressBar.style.width = '0%';
                progressText.textContent = `正在上传 ${validFiles.length} 个文件...`;
                
                // 模拟上传进度
                let progress = 0;
                const interval = setInterval(() => {
                    progress += 10;
                    progressBar.style.width = `${progress}%`;
                    
                    if (progress >= 100) {
                        clearInterval(interval);
                        progressText.textContent = '上传完成!';
                        
                        // 保存文件信息到本地存储
                        validFiles.forEach(file => {
                            saveFileInfo(file);
                        });
                        
                        // 重新加载文件列表
                        loadUploadedFiles();
                        
                        // 3秒后隐藏进度条
                        setTimeout(() => {
                            uploadProgress.classList.add('hidden');
                        }, 3000);
                    }
                }, 300);
            }
            
            // 保存文件信息到本地存储
            function saveFileInfo(file) {
                const files = JSON.parse(localStorage.getItem('uploadedFiles') || '[]');
                const ext = file.name.split('.').pop().toLowerCase();
                
                const fileInfo = {
                    id: Date.now() + Math.random().toString(36).substr(2, 9),
                    name: file.name,
                    size: formatFileSize(file.size),
                    type: ext,
                    date: new Date().toLocaleString()
                };
                
                files.push(fileInfo);
                localStorage.setItem('uploadedFiles', JSON.stringify(files));
            }
            
            // 从本地存储加载文件列表
            function loadUploadedFiles() {
                const files = JSON.parse(localStorage.getItem('uploadedFiles') || '[]');
                
                if (files.length === 0) {
                    uploadedFilesList.innerHTML = `
                        <div class="text-center text-gray-500 py-10">
                            <i class="fa fa-folder-open-o text-4xl mb-4 opacity-30"></i>
                            <p>暂无上传的文件</p>
                        </div>
                    `;
                    return;
                }
                
                // 清空列表
                uploadedFilesList.innerHTML = '';
                
                // 添加文件到列表
                files.forEach(file => {
                    const fileIcon = fileTypes[file.type] || 'fa-file-o text-gray-500';
                    
                    const fileElement = document.createElement('div');
                    fileElement.className = 'bg-white p-4 rounded-lg shadow-sm border border-gray-100 flex items-center justify-between hover:shadow-md transition-custom';
                    fileElement.innerHTML = `
                        <div class="flex items-center">
                            <i class="fa ${fileIcon} text-2xl mr-4"></i>
                            <div>
                                <h4 class="font-medium">${file.name}</h4>
                                <p class="text-sm text-gray-500">${file.size} · ${file.date}</p>
                            </div>
                        </div>
                        <div class="flex space-x-2">
                            <button class="text-primary hover:text-primary/80 transition-custom download-file" data-id="${file.id}">
                                <i class="fa fa-download"></i>
                            </button>
                            <button class="text-gray-500 hover:text-red-500 transition-custom delete-file" data-id="${file.id}">
                                <i class="fa fa-trash"></i>
                            </button>
                        </div>
                    `;
                    
                    uploadedFilesList.appendChild(fileElement);
                });
                
                // 添加删除文件事件监听
                document.querySelectorAll('.delete-file').forEach(button => {
                    button.addEventListener('click', function() {
                        const fileId = this.getAttribute('data-id');
                        deleteFile(fileId);
                    });
                });
                
                // 添加下载文件事件监听（模拟）
                document.querySelectorAll('.download-file').forEach(button => {
                    button.addEventListener('click', function() {
                        const fileId = this.getAttribute('data-id');
                        const files = JSON.parse(localStorage.getItem('uploadedFiles') || '[]');
                        const file = files.find(f => f.id === fileId);
                        
                        if (file) {
                            alert(`正在下载: ${file.name}\n(实际应用中这里会触发文件下载)`);
                        }
                    });
                });
            }
            
            // 删除文件
            function deleteFile(fileId) {
                const files = JSON.parse(localStorage.getItem('uploadedFiles') || '[]');
                const updatedFiles = files.filter(file => file.id !== fileId);
                
                localStorage.setItem('uploadedFiles', JSON.stringify(updatedFiles));
                loadUploadedFiles();
            }
            
            // 格式化文件大小
            function formatFileSize(bytes) {
                if (bytes === 0) return '0 Bytes';
                const k = 1024;
                const sizes = ['Bytes', 'KB', 'MB', 'GB'];
                const i = Math.floor(Math.log(bytes) / Math.log(k));
                return parseFloat((bytes / Math.pow(k, i)).toFixed(2)) + ' ' + sizes[i];
            }
        });

        // 联系表单提交处理
        document.getElementById('contact-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            // 获取表单数据
            const name = document.getElementById('name').value;
            const email = document.getElementById('email').value;
            const subject = document.getElementById('subject').value;
            const message = document.getElementById('message').value;
            
            // 简单验证
            if (!name || !email || !subject || !message) {
                alert('请填写所有必填字段');
                return;
            }
            
            // 模拟表单提交
            const submitButton = this.querySelector('button[type="submit"]');
            const originalText = submitButton.innerHTML;
            
            submitButton.disabled = true;
            submitButton.innerHTML = '<i class="fa fa-spinner fa-spin mr-2"></i>发送中...';
            
            setTimeout(() => {
                // 模拟提交成功
                alert('消息发送成功！我会尽快回复您。');
                this.reset();
                
                submitButton.disabled = false;
                submitButton.innerHTML = originalText;
            }, 1500);
        });

        // 加载更多照片功能
        document.getElementById('load-more-photos').addEventListener('click', function() {
            const galleryContainer = document.querySelector('#gallery .grid');
            const button = this;
            
            // 更改按钮状态
            button.disabled = true;
            button.innerHTML = '<i class="fa fa-spinner fa-spin mr-2"></i>加载中...';
            
            // 模拟加载延迟
            setTimeout(() => {
                // 新增照片
                const photoIds = [11, 22, 33, 44, 55, 66];
                photoIds.forEach(id => {
                    const galleryItem = document.createElement('div');
                    galleryItem.className = 'gallery-item';
                    galleryItem.innerHTML = `
                        <img src="https://picsum.photos/id/${id}/600/400" alt="照片" class="w-full h-64 object-cover">
                        <div class="gallery-overlay">
                            <button class="bg-white text-primary p-2 rounded-full">
                                <i class="fa fa-search-plus"></i>
                            </button>
                        </div>
                    `;
                    galleryContainer.appendChild(galleryItem);
                });
                
                // 恢复按钮状态并更改文本
                button.disabled = false;
                button.innerHTML = '<i class="fa fa-check mr-2"></i>已加载全部照片';
                button.classList.add('bg-secondary');
                button.classList.remove('bg-primary', 'hover:bg-primary/90');
                
                // 点击事件移除，防止重复加载
                button.removeEventListener('click', arguments.callee);
            }, 1500);
        });

        // 平滑滚动
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                
                const targetId = this.getAttribute('href');
                const targetElement = document.querySelector(targetId);
                
                if (targetElement) {
                    window.scrollTo({
                        top: targetElement.offsetTop - 80,
                        behavior: 'smooth'
                    });
                    
                    // 关闭移动菜单（如果打开）
                    document.getElementById('mobile-menu').classList.add('hidden');
                }
            });
        });
    </script>


    
    </body></html>
