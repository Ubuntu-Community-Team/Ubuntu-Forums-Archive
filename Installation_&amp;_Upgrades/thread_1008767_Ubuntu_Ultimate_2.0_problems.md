---
title: "Ubuntu Ultimate 2.0 problems"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by cgsraRude on 2008-12-11
I have an Alienware Aurora m9700 laptop sporting dual Nvidia Geforce Go 7900 gs.

Anyways, I throw on Ubuntu Ultimate 2.0, everything goes relatively well, then I install my graphics drivers. I decided to install them through Terminal after downloading them off the Nvidia site. Afterward I restart and the start up gets stuck at Timidity. 

I hit ctrl+alt+f1 and have no resume image. After trying to disable the usplash nothing happens, it says it cannot find the resume image (or something to that effect, I can't quite remember.)

How should I go about properly getting back to the splash screen, or alternatively could I get a detailed FAQ on how to install that driver?

---

### Post by albinootje on 2008-12-11
Try booting with the "recovery mode" option.
Then choose "drop to root shell", and do :
nano /etc/X11/xorg.conf 
Scroll down till you find the driver line with the word "nvidia".
Change that into "nv", save the file (ctrl x), and type :
reboot

---

### Post by Partyboi2 on 2008-12-11
You could also boot into recovery and try choosing "xfix"

---

### Post by cgsraRude on 2008-12-12
Thanks I'll try it out.

---

