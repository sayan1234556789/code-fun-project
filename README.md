# code-fun-project
Welcome to our GitHub repository for the music player project developed during the thrilling college hackathon! 🚀

//html part

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Music Player</title>
    <link rel="stylesheet" href="style.css">
    <link rel="shortcut icon" href="favicon.ico" type="image/x-icon">  
    <link rel="stylesheet" href="https://fonts.googleapis.com/icon?family=Material+Icons">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
</head>
<body>
    <div class="player">
    <div class="wrapper">
        <div class="main">
            <p id="logo"><i class="fa fa-music"></i>Music</p>
        </div>

        <div class="top-bar">
            <i class="material-icons">expand_more</i>
            <span>Now Playing</span>
            <i class="material-icons">more_horiz</i>
        </div>

        <div class="img-area">
            <img src="images/music-11.jpg" alt="">
        </div>

        <div class="song-details">
            <p class="name"></p>
            <p class="artist"></p>
        </div>

        <div class="progress-area">
            <div class="progress-bar">
                <audio id="main-audio" src=""></audio>
                <span></span>
            </div>
            <div class="song-timer">
                <span class="current-time">0:00</span>
                <span class="max-duration">0:00</span>
            </div>
        </div>

        <div class="volume">
            <p id="volume_show">92</p>
            <i class="fa fa-volume-up" aria-hidden="true" onclick="mute_sound()" id="volume_icon"></i>
            <input type="range" min="0" max="100" value="92" onchange="volume_change()" id="volume">  
        </div>

        <div class="controls">
            <i id="repeat-plist" class="material-icons" title="Playlist looped">repeat</i>
            <i id="prev" class="material-icons">skip_previous</i>
            <div class="play-pause">
                <i class="material-icons play">play_arrow</i>
            </div>
            <i id="next" class="material-icons">skip_next</i>
            <i id="more-music" class="material-icons">queue_music</i>
        </div>

        <div id="wave">
            <span class="stroke"></span>
            <span class="stroke"></span>
            <span class="stroke"></span>
            <span class="stroke"></span>
            <span class="stroke"></span>
            <span class="stroke"></span>
            <span class="stroke"></span>
            <span class="stroke"></span>
            <span class="stroke"></span>
        </div>

        <div class="music-list">
            <div class="header">
                <div class="row">
                    <i class= "list material-icons">queue_music</i>
                    <span>Music list</span>
                </div>
                <i id="close" class="material-icons">close</i>
            </div>
            <ul>
                <!-- here li list are coming from js -->

                <!-- <li>
                    <div class="row">
                        <span>Despacito</span>
                        <p>Justin</p>
                    </div>
                    <span class="audio-duration">2:34</span>
                </li> -->
            </ul>
        </div>
    </div>
</div>

    <script src="music-list.js"></script>
    <script src="script.js"></script>
</body>
</html>



//css part

@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@200;300;400;500;600;700&display=swap');

*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: "Poppins", sans-serif;
}

*::before, *::after{
    padding: 0;
    margin: 0;
}

:root{
    --whitetype: #74daff;
    --blacktype: #746ea3;
    --lightblack: #515C6F;
    --white: #ffffff;
    --darkwhite: #abb9cf;
    --pinkshadow: #cbd1ff;
    --lightbshadow: rgba(0, 0, 0, 0.364);
}

body{
    display: flex;
    align-items: center;
    justify-content: center;
    background: linear-gradient(1800deg, black, white);
}

.player {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    min-height: 100vh;
    background: linear-gradient(45deg, rgb(15, 184, 218), rgb(203, 216, 216));
}

.wrapper{
    width: 450px;
    padding: 25px 30px;
    overflow: hidden;
    position: relative;
    border-radius: 15px;
    background: var(--white);
    box-shadow: 0px 6px 15px var(--lightbshadow);
}

.wrapper i{
    cursor: pointer;
}

.main {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 5px;
}

.main #logo {
    font-size: 20px;
    color: #1c1d1d;
}

.main #logo i {
    margin-right: 10px;
}

.top-bar, .progress-area .song-timer, .controls, .music-list .header, .music-list ul li {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.top-bar i{
  font-size: 30px;
  color: var(--lightblack);
}

.top-bar span{
    font-size: 18px;
    margin-left: -3px;
    color: var(--lightblack);
}

.img-area{
    width: 60%;
    height: 235px;
    margin: auto;
    overflow: hidden;
    margin-top: 15px;
    border-radius: 50%;
    -moz-box-shadow: 0px 6px 12px var(--lightbshadow);
    -webkit-box-shadow: 0px 6px 12px var(--lightbshadow);
    box-shadow: 0px 6px 12px var(--lightbshadow);
}

.img-area img{
    width: 100%;
    height: 100%;
    object-fit: cover;
}

.song-details{
    text-align: center;
    margin: 15px 0;
}

.song-details>p{
    color: rgba(0, 0, 0, 0.858);
}

.song-details .name{
    font-size: 21px;
}

.song-details .artist{
    font-size: 18px;
    opacity: 0.9;
    line-height: 35px;
}

.progress-area{
    height: 6px;
    width: 100%;
    border-radius: 50px;
    background: #f0f0f0;
    cursor: pointer;
}

.progress-area .progress-bar{
    height: inherit;
    width: 0%;
    position: relative;
    border-radius: inherit;
    background: linear-gradient(90deg, var(--whitetype) 0%, var(--blacktype) 100%);
}

.progress-bar::before{
    content: "";
    position: absolute;
    height: 12px;
    width: 12px;
    border-radius: 50%;
    top: 50%;
    right: -5px;
    z-index: 2;
    opacity: 0;
    pointer-events: none;
    transform: translateY(-50%);
    background: inherit;
    transition: opacity 0.2s ease;
}

.progress-area:hover .progress-bar::before{
    opacity: 1;
    pointer-events: auto;
}

.progress-area .song-timer{
    margin-top: 2px;

}
.song-timer span{
    font-size: 13px;
    color: var(--lightblack);
}

.volume{
    margin: 30px 0 15px 0;
    /* position: absolute; */
    display: flex;
    justify-content: center; 
    align-items: center;
    color: rgb(87, 86, 86)
}

.volume p {
    font-size: 15px;
}

.volume i {
    cursor: pointer;
    padding: 8px 12px;
    background: #ffffff;
}

.volume i:hover {
    background: rgba(109, 109, 109, 0.1);
}

.volume #volume_show {
    padding: 8px 12px;
    margin: 0 5px 0 0;
    background: rgba(122, 121, 121, 0.1);
}

.volume input {
    -webkit-appearance: none;
    width: 60%;
    outline: none;
    border: none;
    height: 3px;
    margin: 0 5px;
    background: rgb(118, 182, 196);
} 

input[type="range"]::-webkit-progress-value {
    -webkit-appearance: none;
    background-color: #31369f;
}

input[type="range"]::-webkit-slider-thumb {
    -webkit-appearance: none;
    height: 20px;
    width: 20px;
    background: #cbdbe3;
    border: 3px solid rgb(156, 153, 153);
    border-radius: 50%;
    cursor: pointer;
}

.controls{
    margin: 10px 0 5px 0;
}

.controls i{
    font-size: 28px;
    user-select: none;
    background: linear-gradient(var(--whitetype) 0%, var(--blacktype) 100%);  
    background-clip: text;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
}

.controls i:nth-child(2), .controls i:nth-child(4){
    font-size: 43px;
}

.controls #prev{
    margin-right: -13px;
}

.controls #next{
    margin-left: -13px;
}

.controls .play-pause{
    height: 54px;
    width: 54px;
    display: flex;
    cursor: pointer;
    align-items: center;
    justify-content: center;
    border-radius: 50%;
    background: linear-gradient(var(--white) 0%, var(--darkwhite) 100%);
    box-shadow: 0px 0px 5px var(--whitetype);
}

.play-pause::before{
    position: absolute;
    content: "";
    height: 43px;
    width: 43px;
    border-radius: inherit;
    background: linear-gradient(var(--whitetype) 0%, var(--blacktype) 100%);
}

.play-pause i{
    height: 43px;
    width: 43px;
    line-height: 43px;
    text-align: center;
    background: inherit;
    background-clip: text;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    position: absolute;
}

.music-list{
    position: absolute;
    background: var(--white);
    width: 100%;
    left: 0;
    bottom: -55%;
    opacity: 0;
    pointer-events: none;
    /* z-index: 5; */
    padding: 15px 30px;
    border-radius: 15px;
    box-shadow: 0px -5px 10px rgba(0,0,0,0.1);
    transition: all 0.15s ease-out;
}

.music-list.show{
    bottom: 0;
    opacity: 1;
    pointer-events: auto;
}

.header .row{
    display: flex;
    align-items: center;
    font-size: 19px;
    color: var(--lightblack);
}

.header .row i{
    cursor: default;
}

.header .row span{
    margin-left: 5px;
}

.header #close{
    font-size: 22px;
    color: var(--lightblack);
}

.music-list ul{
    margin: 10px 0;
    max-height: 260px;
    overflow: auto;
}

.music-list ul::-webkit-scrollbar{
    width: 0px;
}

.music-list ul li{
    list-style: none;
    display: flex;
    cursor: pointer;
    padding-bottom: 10px;
    margin-bottom: 5px;
    color: var(--lightblack);
    border-bottom: 1px solid #e5e5e5;
}

.music-list ul li:last-child{
    border-bottom: 0px;
}

.music-list ul li .row span{
    font-size: 17px;
}

.music-list ul li .row p{
    opacity: 0.9;
}

ul li .audio-duration{
    font-size: 16px;
}

.rotate {
    animation: rotation 7s infinite linear;
}
@keyframes rotation {
    from {
      transform: rotate(0deg);
    }
    to {
      transform: rotate(359deg);
    }
}

.loader {
    padding-top: 15px;
    height: 60px;
    display: flex;
    justify-content: center;
    align-items: center;
}

.loader .stroke{
    background: #f1f1f1;
    height: 120%;
    width: 8px;
    border-radius: 50px;
    margin: 0 5px;
    animation: animate 1s linear infinite;
}

@keyframes animate {
    30% {
        height: 20%;
        background: #39647d;
    }

    50% {
        height: 50%;
        background: #437793;
    }
  
    100% {
        background: #266a87;
        height: 100%;
    }
}

.stroke:nth-child(1){
    animation-delay: 0s;
}

.stroke:nth-child(2){
    animation-delay: 0.6s;
}

.stroke:nth-child(3){
    animation-delay: 0.2s;
}

.stroke:nth-child(4){
    animation-delay: 0.4s;
}

.stroke:nth-child(5){
    animation-delay: 0.8s;
}

.stroke:nth-child(6){
    animation-delay: 0.4s;
}

.stroke:nth-child(7){
    animation-delay: 0.2s;
}

.stroke:nth-child(8){
    animation-delay: 0.6s;
}

.stroke:nth-child(9){
    animation-delay: 0s;
}



//javascript part

let now_playing = document.querySelector('.now-playing');
const wrapper = document.querySelector(".wrapper"),
musicImg = wrapper.querySelector(".img-area img"),
musicName = wrapper.querySelector(".song-details .name"),
musicArtist = wrapper.querySelector(".song-details .artist"),
playPauseBtn = wrapper.querySelector(".play-pause"),
prevBtn = wrapper.querySelector("#prev"),
nextBtn = wrapper.querySelector("#next"),
mainAudio = wrapper.querySelector("#main-audio"),
progressArea = wrapper.querySelector(".progress-area"),
progressBar = progressArea.querySelector(".progress-bar"),
musicList = wrapper.querySelector(".music-list"),
moreMusicBtn = wrapper.querySelector("#more-music"),

closemoreMusic = musicList.querySelector("#close");

let recent_volume = document.querySelector('#volume');
let volume_show = document.querySelector('#volume_show');
let wave = document.getElementById('wave');



let musicIndex = Math.floor((Math.random() * allMusic.length) + 1);
isMusicPaused = true;

window.addEventListener("load", ()=>{
  loadMusic(musicIndex);
  playingSong(); 
});

function loadMusic(indexNumb){
  musicName.innerText = allMusic[indexNumb - 1].name;
  musicArtist.innerText = allMusic[indexNumb - 1].artist;
  musicImg.src = `images/${allMusic[indexNumb - 1].src}.jpg`;
  mainAudio.src = `songs/${allMusic[indexNumb - 1].src}.mp3`;
}

//play music function
function playMusic(){
  wrapper.classList.add("paused");
  playPauseBtn.querySelector("i").innerText = "pause";
  mainAudio.play();
  wave.classList.add('loader');
  musicImg.classList.add('rotate');
}

//pause music function
function pauseMusic(){
  wrapper.classList.remove("paused");
  playPauseBtn.querySelector("i").innerText = "play_arrow";
  mainAudio.pause();
  wave.classList.remove('loader');
  musicImg.classList.remove('rotate');
}

//prev music function
function prevMusic(){
  musicIndex--; //decrement of musicIndex by 1
  //if musicIndex is less than 1 then musicIndex will be the array length so the last music play
  musicIndex < 1 ? musicIndex = allMusic.length : musicIndex = musicIndex;
  loadMusic(musicIndex);
  playMusic();
  playingSong(); 
}

//next music function
function nextMusic(){
  musicIndex++; //increment of musicIndex by 1
  //if musicIndex is greater than array length then musicIndex will be 1 so the first music play
  musicIndex > allMusic.length ? musicIndex = 1 : musicIndex = musicIndex;
  loadMusic(musicIndex);
  playMusic();
  playingSong(); 
}

// play or pause button event
playPauseBtn.addEventListener("click", ()=>{
  const isMusicPlay = wrapper.classList.contains("paused");
  //if isPlayMusic is true then call pauseMusic else call playMusic
  isMusicPlay ? pauseMusic() : playMusic();
  playingSong();
});

//prev music button event
prevBtn.addEventListener("click", ()=>{
  prevMusic();
});

//next music button event
nextBtn.addEventListener("click", ()=>{
  nextMusic();
});

// update progress bar width according to music current time
mainAudio.addEventListener("timeupdate", (e)=>{
  const currentTime = e.target.currentTime; //getting playing song currentTime
  const duration = e.target.duration; //getting playing song total duration
  let progressWidth = (currentTime / duration) * 100;
  progressBar.style.width = `${progressWidth}%`;

  let musicCurrentTime = wrapper.querySelector(".current-time"),
  musicDuartion = wrapper.querySelector(".max-duration");
  mainAudio.addEventListener("loadeddata", ()=>{
    // update song total duration
    let mainAdDuration = mainAudio.duration;
    let totalMin = Math.floor(mainAdDuration / 60);
    let totalSec = Math.floor(mainAdDuration % 60);
    if(totalSec < 10){ //if sec is less than 10 then add 0 before it
      totalSec = `0${totalSec}`;
    }
    musicDuartion.innerText = `${totalMin}:${totalSec}`;
  });
  // update playing song current time
  let currentMin = Math.floor(currentTime / 60);
  let currentSec = Math.floor(currentTime % 60);
  if(currentSec < 10){ //if sec is less than 10 then add 0 before it
    currentSec = `0${currentSec}`;
  }
  musicCurrentTime.innerText = `${currentMin}:${currentSec}`;
});

// update playing song currentTime on according to the progress bar width
progressArea.addEventListener("click", (e)=>{
  let progressWidth = progressArea.clientWidth; //getting width of progress bar
  let clickedOffsetX = e.offsetX; //getting offset x value
  let songDuration = mainAudio.duration; //getting song total duration
  
  mainAudio.currentTime = (clickedOffsetX / progressWidth) * songDuration;
  playMusic(); //calling playMusic function
  playingSong();
});

//change loop, shuffle, repeat icon onclick
const repeatBtn = wrapper.querySelector("#repeat-plist");
repeatBtn.addEventListener("click", ()=>{
  let getText = repeatBtn.innerText; //getting this tag innerText
  switch(getText){
    case "repeat":
      repeatBtn.innerText = "repeat_one";
      repeatBtn.setAttribute("title", "Song looped");
      break;
    case "repeat_one":
      repeatBtn.innerText = "shuffle";
      repeatBtn.setAttribute("title", "Playback shuffled");
      break;
    case "shuffle":
      repeatBtn.innerText = "repeat";
      repeatBtn.setAttribute("title", "Playlist looped");
      break;
  }
});

//code for what to do after song ended
mainAudio.addEventListener("ended", ()=>{
  // we'll do according to the icon means if user has set icon to
  // loop song then we'll repeat the current song and will do accordingly
  let getText = repeatBtn.innerText; //getting this tag innerText
  switch(getText){
    case "repeat":
      nextMusic(); //calling nextMusic function
      break;
    case "repeat_one":
      mainAudio.currentTime = 0; //setting audio current time to 0
      loadMusic(musicIndex); //calling loadMusic function with argument, in the argument there is a index of current song
      playMusic(); //calling playMusic function
      break;
    case "shuffle":
      let randIndex = Math.floor((Math.random() * allMusic.length) + 1); //genereting random index/numb with max range of array length
      do{
        randIndex = Math.floor((Math.random() * allMusic.length) + 1);
      }while(musicIndex == randIndex); //this loop run until the next random number won't be the same of current musicIndex
      musicIndex = randIndex; //passing randomIndex to musicIndex
      loadMusic(musicIndex);
      playMusic();
      playingSong();
      break;
  }
});

//show music list onclick of music icon
moreMusicBtn.addEventListener("click", ()=>{
  musicList.classList.toggle("show");
});
closemoreMusic.addEventListener("click", ()=>{
  moreMusicBtn.click();
});

const ulTag = wrapper.querySelector("ul");
// let create li tags according to array length for list
for (let i = 0; i < allMusic.length; i++) {
  //let's pass the song name, artist from the array
  let liTag = `<li li-index="${i + 1}">
                <div class="row">
                  <span>${allMusic[i].name}</span>
                  <p>${allMusic[i].artist}</p>
                </div>
                <span id="${allMusic[i].src}" class="audio-duration">3:40</span>
                <audio class="${allMusic[i].src}" src="songs/${allMusic[i].src}.mp3"></audio>
              </li>`;
  ulTag.insertAdjacentHTML("beforeend", liTag); //inserting the li inside ul tag

  let liAudioDuartionTag = ulTag.querySelector(`#${allMusic[i].src}`);
  let liAudioTag = ulTag.querySelector(`.${allMusic[i].src}`);
  liAudioTag.addEventListener("loadeddata", ()=>{
    let duration = liAudioTag.duration;
    let totalMin = Math.floor(duration / 60);
    let totalSec = Math.floor(duration % 60);
    if(totalSec < 10){ //if sec is less than 10 then add 0 before it
      totalSec = `0${totalSec}`;
    };
    liAudioDuartionTag.innerText = `${totalMin}:${totalSec}`; //passing total duation of song
    liAudioDuartionTag.setAttribute("t-duration", `${totalMin}:${totalSec}`); //adding t-duration attribute with total duration value
  });
}

//play particular song from the list onclick of li tag
function playingSong(){
  const allLiTag = ulTag.querySelectorAll("li");
  
  for (let j = 0; j < allLiTag.length; j++) {
    let audioTag = allLiTag[j].querySelector(".audio-duration");
    
    if(allLiTag[j].classList.contains("playing")){
      allLiTag[j].classList.remove("playing");
      let adDuration = audioTag.getAttribute("t-duration");
      audioTag.innerText = adDuration;
    }

    //if the li tag index is equal to the musicIndex then add playing class in it
    if(allLiTag[j].getAttribute("li-index") == musicIndex){
      allLiTag[j].classList.add("playing");
      audioTag.innerText = "Playing";
    }

    allLiTag[j].setAttribute("onclick", "clicked(this)");
  }
}

//particular li clicked function
function clicked(element){
  let getLiIndex = element.getAttribute("li-index");
  musicIndex = getLiIndex; //updating current song index with clicked li index
  loadMusic(musicIndex);
  playMusic();
  playingSong();
}

//mute sound function
function mute_sound() {
	mainAudio.volume = 0;
	volume.value = 0;
	volume_show.innerHTML = 0;
}

// change volume
function volume_change() {
	volume_show.innerHTML = recent_volume.value;
	mainAudio.volume = recent_volume.value / 100;
}


//music list.js

let allMusic = [
    {
        name: "Aadat Se Majboor",
        artist: "Benny Dayal",
        img: "music-11",
        src: "music-11"
    },
    {
        name: "Pyaar Hota Kayi Baar Hai",
        artist: "Arijit Singh",
        img: "music-12",
        src: "music-12"
    },
    {
        name: "Bhool Bhulaiyaa 2",
        artist: "Neeraj Shridhar",
        img: "music-13",
        src: "music-13"
    },
    {
        name: "Hale Dil",
        artist: "Harshit Saxena",
        img: "music-14",
        src: "music-14"
    },
    {
        name: "Dil Sambhal Ja Zara",
        artist: "Mohd. Irfan, Arijit Singh and Salim Bhatt. ",
        img: "music-15",
        src: "music-15"
    },
    {
        name: "Shape-of-You",
        artist: "Ed Sheeran",
        img: "music-1",
        src: "music-1"
    },
    {
        name: "Calm-Down",
        artist: "Rema, Selena Gomez",
        img: "music-2",
        src: "music-2"
    },
    {
        name: "Let Me Down Slowly",
        artist: "Alec Benjamin",
        img: "music-3",
        src: "music-3"
    },
    {
        name: "Love Me Like You Do",
        artist: "Ellie Goulding",
        img: "music-4",
        src: "music-4"
    },
    {
        name: "Starboy",
        artist: "The Weeknd",
        img: "music-5",
        src: "music-5"
    },
    {
        name: "Girls Like You",
        artist: "Maroon 5",
        img: "music-6",
        src: "music-6"
    },
    {
        name: "On My Way",
        artist: "Alan Walker",
        img: "music-7",
        src: "music-7"
    },
    {
        name: "Sorry",
        artist: "Justin Beiber",
        img: "music-8",
        src: "music-8"
    },
    {
        name: "Sugar and Brownies",
        artist: "Dharia",
        img: "music-9",
        src: "music-9"
    },
    {
        name: "Faded",
        artist: "Alan Walker",
        img: "music-10",
        src: "music-10"
    },
    {
        name: "CGMP",
        artist: "CarryMinati",
        img: "music-16",
        src: "music-16"
    },
    {
        name: "ALBELE TANGEWALE",
        artist: "albele tange",
        img: "music-16",
        src: "music-17"
    },
];
        
