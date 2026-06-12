---
title: "How to change resolution from outside ubuntu"
date: 2005-11-23
forum: General Help
---

### Post by floboe on 2005-11-23
I just installed ubuntu yesterday but i cant really get to use it since my monitor doesnt support the resolution chosen by ubuntu. Whenever i try to start ubuntu, my monitor flashes a warning signal, and turns off after a few seconds. 

Is it possible to change the screen resolution from outside ubuntu? Like from a recovery console or such.. I am a linux noob, so i dont know much about it.

My gfx card is an gf4 ti4200 128mb.

---

### Post by olavi on 2005-11-23
I'm not sure, but I guess you could try recovery mode from the boot menu. If it opens up the console, run "sudo nano /etc/X11/xorg.conf" and remove the troublemaking resolutions.

---

