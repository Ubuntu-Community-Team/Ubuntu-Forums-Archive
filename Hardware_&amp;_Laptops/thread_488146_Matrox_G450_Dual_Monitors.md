---
title: "Matrox G450 Dual Monitors"
date: 2007-06-29
forum: Hardware &amp; Laptops
---

### Post by jleaman on 2007-06-29
Ok so you guys helped me out with my dell computer with dual monitors, can any one help me with Another computer, running a Amd Athlon with a Matrox G450 dual head with 2 vga ports, id like to run dual monitors to have them both working. As it sits they are both working but they are mirrored.  Any one help please ?

Thanks.

Jase

---

### Post by jleaman on 2007-06-30
Ttt

---

### Post by jleaman on 2007-07-03
Any one ? Please ?

---

### Post by IntuitiveNipple on 2007-07-04
I've been running Edgy on a Matrox G450 dual-head. I would assume the same configuration will work for Feisty although I've not tested it.

There are a couple of modes you can use: Xinerama and Merged Frame Buffer.

I prefer MergedFB.

I've attached  two xorg.conf files I prepared when the PC was originally configured and the current in-use xorg.conf (uses MergedFB). You'll need to alter them to reflect the abilities of your monitors, input devices, and the BusID of your G450.

---

### Post by jleaman on 2007-07-05
Thank's for your reply,  since i am running the AGP version just like you, i think i am able to copy your file, and use it, if not ill have to revert to the backup :D thanks for your help i really apreciate it, i am enjoying Ubuntu on my dell box using 2 23" lcd's and love it. :D

This form rocks. 

Jase

---

### Post by jleaman on 2007-07-08
This file worked IntuitiveNipple, i appreciate your help. Thanks. I now have my friend converted back to linux and he is so happy.

---

### Post by abbandon on 2007-08-01
Hi, 
Is anybody can confirm IntuitiveNipple`s config works at feisty ( xorg 7.2.0 ) with G450, because for me it isn`t at all.
Xinerama works perfect. I did number of tries with number xorg configurations for mergedFB with no success. Every time i have the sane result. In case I use official mga drivers  the monitors is cloned and image is doublesized by width for each one. Although, "unofficial" mga make it stucked. in log I can see well known error 
...
(WW) MGA(0): Mode pool is empty
(EE) MGA(0): CRTC2: No valid modes found
...
Also I confirm key ignoreABI applied in xorg.conf as well as gnom config.
I guess all works perfect at previous version Xorg\Ubuntu Edgy, so just tell me anybody it works for feisty with follow configuration:
matrox G450 dual VGA head, 32 Mb
Ubuntu feisty, Xorg 7.2.0, mergedFB, official\unofficial(4.4.3) mba 4.4.3 drivers 

Thanks

---

