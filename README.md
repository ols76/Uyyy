<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <title>Happy Level Up!</title>
  <link href="https://fonts.googleapis.com/css2?family=Pacifico&display=swap" rel="stylesheet" />
  <style>
    body {
      background-color: #ffeef2;
      background-image: radial-gradient(#ffd1dc 1px, transparent 1px);
      background-size: 20px 20px;
      font-family: 'Pacifico', cursive;
      margin: 0;
      padding: 0;
      text-align: center;
      color: #444;
    }

    .container {
      max-width: 90%;
      margin: auto;
      padding: 60px 10px 40px;
    }

    .slide {
      display: none;
      transform: translateY(30px);
      opacity: 0;
      transition: all 0.6s ease-in-out;
    }

    .slide.active {
      display: block;
      transform: translateY(0);
      opacity: 1;
    }

    img, video {
      max-width: 100%;
      border-radius: 20px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
    }

    button {
      background-color: #ffafcc;
      border: none;
      color: white;
      padding: 10px 20px;
      font-size: 18px;
      border-radius: 10px;
      margin: 20px 10px;
      cursor: pointer;
      font-family: 'Pacifico', cursive;
    }

    .sticker {
      position: absolute;
      width: 80px;
      z-index: 10;
    }

    .sticker1 {
      top: 20px;
      left: 20px;
    }

    .sticker2 {
      top: 30px;
      right: 30px;
    }

  </style>
</head>
<body>

  <img src="https://i.imgur.com/WQ3Y1ZG.png" class="sticker sticker1" />
  <img src="https://i.imgur.com/35RRyGb.png" class="sticker sticker2" />

  <h1>Happy Level Up Najipah!</h1>
  <div class="container" id="slideshow">
    <!-- Slides will be added here -->
  </div>

  <button onclick="prevSlide()">Prev</button>
  <button onclick="nextSlide()">Next</button>

  <script>
    const files = [
      "9236718622fdf8ea7c24794b6fd79fc1.jpg",
      "f5f644cce8d930568ab45257ffad9ae1.mp4",
      "400a2337594af3a582178b8dbb67d0fb.jpg",
      // lanjutkan sesuai file kamu yaa~
    ];

    const container = document.getElementById("slideshow");

    files.forEach((file, index) => {
      const slide = document.createElement('div');
      slide.classList.add('slide');
      if (index === 0) slide.classList.add('active');

      const ext = file.split('.').pop();
      if (["mp4", "webm", "ogg"].includes(ext)) {
        const video = document.createElement('video');
        video.src = file;
        video.controls = true;
        slide.appendChild(video);
      } else {
        const img = document.createElement('img');
        img.src = file;
        slide.appendChild(img);
      }

      container.appendChild(slide);
    });

    let current = 0;
    const slides = document.querySelectorAll(".slide");

    function showSlide(i) {
      slides[current].classList.remove("active");
      current = (i + slides.length) % slides.length;
      slides[current].classList.add("active");
    }

    function nextSlide() {
      showSlide(current + 1);
    }

    function prevSlide() {
      showSlide(current - 1);
    }
  </script>

</body>
</html>
