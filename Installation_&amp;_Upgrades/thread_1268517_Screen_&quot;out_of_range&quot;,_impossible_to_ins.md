---
title: "Screen &quot;out of range&quot;, impossible to install any type of *buntu"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by Pyntix on 2009-09-17
Every time I try to install any kind of *buntu with a normal cd (not textbased install or with compatible graphics mode) I can't get X to start. Whenever I boot the computer the screen dies after the first loading bar with a "Screen out of range" message.

I did install a Kubuntu (8.10) with compatibility graphics mode (or if that's what it's called) but after that when I installed the latest NVidia propietary driver I got the same message again.

I've also tried installing with the alternate CD, but with the same result after updating the driver.

My specs:

CPU - AMD Athlon 64 X2 3800+
GPU - NVidia GeForce 7800 GT 256MB
RAM - 1GB
And about 40 GB of empty disk space.

---

### Post by kerry_s on 2009-09-17
you need to press esc key and use the rescue mode-> root shell

type-> **X -configure**

then edit the new xorg.conf with your screen rate:
**nano /root/xorg.conf.new**

then copy it:
**cat /root/xorg.conf.new > /etc/X11/xorg.conf**

type-> **reboot**

see if it works.

---

