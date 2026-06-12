---
title: "A fix for pixellated video issue with ATI cards."
date: 2008-09-03
forum: General Help
---

### Post by srikar on 2008-09-03
Many ATI users(esp, radeon users) had a problem with the restricted driver in Ubuntu , especially when watching videos in full screen mode, the video used to get pixellated.

Now the driver brings better support with 3d rendering.

--------------------------------------------------------------------------------------------------------------------------------------
In ubuntu,,
Just install ati fglrx driver through >System>Administration>Hardware drivers.

Restart da system .Play certain videos , if the video is **pixellated** enter this command in terminal * sudo aticonfig --ovt=Xv *

Relogin ( alt+ctrl+backspace).Issue gets fixed.

Documentation:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by Renault # on 2008-10-05
Hi thanks, it definitely worked to play my divx files in fullscreen mode using most popular players (vlc, totem). However, now I *have* to watch them in fullscreen only. I dont see any video in vlc during normal standard size playback, except for a little half second blip when I move the window. Any ideas as to what might cause this?

Other than that it works great!

BTW I have a Ati RX1050 TD512-E with the fglrx drivers

---

### Post by Renault # on 2008-10-05
Nevermind, I sorted this by setting the video output module in VLC to X11

---

