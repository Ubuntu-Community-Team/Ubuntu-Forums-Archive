---
title: "VLC, MPlayer crash/freeze Ubuntu"
date: 2008-07-28
forum: General Help
---

### Post by tom66 on 2008-07-28
When trying to play an ogg file my system freezes. It used to be able to play them but for some reason it can't now. Everything stops; widget animations, clock, terminal blinker, everything. The only thing that still moves is the mouse.

Ubuntu 8.04 HH

All help appreciated,
Tom

---

### Post by UbuntuNerd on 2008-07-28
are you running compiz fusion b/c there seems to be a problem between compiz and vlc try this

open vlc (no video, just open it as a program), and do the following:
click - settings > preferences > video
in the bottom right, put a checkmark in "advanced options"
then click - output modules
and change "video output module" from "opengl video output" to "x11 video output".

note:
if you later want to run vlc while in using compiz, you may have to change this setting back to opengl.
__________________

---

### Post by tom66 on 2008-07-28
Thanks, works fine now! :)

---

### Post by kenlar on 2008-09-11
thanks :)

---

### Post by Hilko on 2008-09-23
Thanks a lot !
I just bought a new Lenovo thinkpad T500 with intel graphics. Vlc crashed the system completely. I was reallly dissapointed in my new laptop. Now it works perfectly. Many thanks to UbuntuNerd !

---

