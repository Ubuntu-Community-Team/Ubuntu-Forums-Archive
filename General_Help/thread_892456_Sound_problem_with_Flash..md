---
title: "Sound problem with Flash."
date: 2008-08-17
forum: General Help
---

### Post by Diya on 2008-08-17
I'm using Firefox, and Flash works fine (youtube, flash games, etc.).However, The problem is the sound.

1) The Flash game mutes the PC, and when I try playing any music file the audio program stop responding until I close Firefox, or close the game's web page.

2) If a music file was being played before the game started loading, the PC mutes the game, and the game runs much slower.

3) Sometimes the game is mute even though I'm not playing any music file. (Yes, the game has sounds, and I didn't press the mute button).   

In other words, I can't play music files as long as there is a flash program (youtube, games, etc.) running in my browser, and vice-versa.

I'm using Flash version 9.

---

### Post by eggdeng on 2008-08-17
Try
```
sudo apt-get install libflashsupport
```
and restart the browser.

---

### Post by leepesjee on 2008-08-17
Your sound problem is probobaly related to pulseaudio, the now default sound-server in Hardy. There are numerous threads about this topic and there are different solutions. It depends on your hardware, the apps you want to run and just a matter of taste which solution you choose.See:
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Diya on 2008-08-17
> **leepesjee said:**
> Your sound problem is probobaly related to pulseaudio, the now default sound-server in Hardy. There are numerous threads about this topic and there are different solutions. It depends on your hardware, the apps you want to run and just a matter of taste which solution you choose.See:
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Totally solved my problem. Thanks for pointing those topics out!

---

