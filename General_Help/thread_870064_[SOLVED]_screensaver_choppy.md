---
title: "[SOLVED] screensaver choppy"
date: 2008-07-25
forum: General Help
---

### Post by Archimedes0212 on 2008-07-25
Hey all -

So before I upgraded to hardy, my screensaver worked smoothly.  After my upgrade, this changed.  Now when my computer goes to screensaver the graphics are incredibly choppy.

I thought this might be attributed to using mesa instead of my ati graphics.  When I finally got around to changing my settings so that it uses my ati graphics the problem still persisted. 

Does anyone know what could be causing this problem and how to fix it?

I have an IBM thinkpad T60 laptop.

It has:
Intel Core Duo T2500 processors (2.0Ghz)
1GB RAM
128MB ATI Mobility Radeon X1400 video chipset

Thanks in advance everyone

---

### Post by vexorian on 2008-07-25
I just upgraded from hardy 8.04 to 8.04.1 (I guess yours upgraded to 8.04.1 automatically) And I am experiencing the same thing, during the upgrade process I noticed it uninstalled xscreensaver and replaced it with gnome-screensaver? Could that be the cultprit?

It is floating ubuntu that got amazingly slower, other screensavers also seem slower, but some heavy 3d ones , glxgears and warcraft III all are working smooth, so I am gonna call "bug" on this one, will also take a look to the bug tracker to see if there's something similar around.

---

### Post by rossjman1 on 2008-07-25
I have this problem as well. It is a problem caused by running the screensaver and Compiz at the same time. Any openGL program will have this problem when Compiz is running.

---

### Post by vexorian on 2008-07-25
The problem is, I am not running compiz.

---

### Post by Archimedes0212 on 2008-07-26
so, i reinstalled my ati graphics card and it works perfectly fine now.  really weird but im not complaining.  hmmm

---

