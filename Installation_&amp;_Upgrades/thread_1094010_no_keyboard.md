---
title: "no keyboard"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by D4P5 on 2009-03-12
hey guys,

i'm trying to install ubuntu 8.04 on my new pc but i can't get the keyboard running (enermax aurora). 

i actually just tried to start the live system, so it will probably run after the full installation. what do you think? is it just a problem of the live dvd? and is it possible to install ubuntu without a properly working keyboard?

i tried to find other guys which have the same problem (the keyboard is also not dedected in the bootscreen of ubuntu but it works perfektly well in the bios settings and other systems).

thank you very much for your help,
D4P5


Spec of my pc:
Harddisk: Western Digital Scorpio Blue 320GB
Motherboard: ASRock AOD790GX
CPU: AMD Athlon X2 5050e
RAM: A-DATA Value DIMM Kit 4GB PC2-6400U CL5 (DDR2-800)
Cardreader: Lian Li Cardreader CR-36B - black
DVD: Sony NEC Optiarc AD-7203S-0B, SATA
Wifi-card: TP-Link TL-WN651G
keyboard: Enermax Aurora
screen: Iiyama ProLite B2403WS-B

---

### Post by Mark Phelps on 2009-03-12
OF course, at this point, everyone will be saying ... open a terminal and type ...

Problem is, without a working keyboard, you can't do that.

While it might be possible to install without a keyboard (you'd have to do an unattended install and provide some kind of config file with the values needed), what good will the results be if it still does not detect the keyboard?

My suggestion is to either get a dirt-cheap USB keyboard (they're available for $10 and less around here) or if your PC still has a PS/2 keyboard jack, get a ps/2 keyboard.  Hook both keyboards (the enermax and the other that will work) up to the machine, boot into the Live CD, open a terminal (now that you have a working keyboard), and enter "lsusb" -- to see if Linux detects both keyboards.

If it doesn't see the enermax, you're faced with finding Linux drivers for it -- which could be quite a challenge.

---

### Post by D4P5 on 2009-03-13
hi mark,

thank you for your answer!

i found an old ps2 keyboard and installed the full version of ubuntu 8.04 (amd64) on my pc. unfortunately the enermax keyboard is again not running.

any ideas how to fix this problem? it is possible for me to use the terminal with the old keyboard.

thank you very much,
D4P5

---

### Post by Mark Phelps on 2009-03-13
Not personally familiar with the enermax, but use a Logitech USB keyboard myself and all the basic functions work.  Logitech has software that must be installed for the advanced functions -- which, of course, do NOT work in Linux because that software can't be installed.

I would think, which you've discovered to be wrong, that any USB keyboard would basically work in Linux.

Your only recourse at this point would be to contact enermax and see what they suggest.

---

