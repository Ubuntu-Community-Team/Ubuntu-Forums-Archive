---
title: "LiveCD X finds no screen"
date: 2007-05-18
forum: Hardware &amp; Laptops
---

### Post by wildegnux on 2007-05-18
I'm trying to install Ubuntu 7.04. When booting up the liveCD i get a error message saying that X can't find a screen. (Safe graphics mode)

The Xorg log file says: 
```
(II) VESA(0): Total Memory: 256 64KB banks (16384kB)
(EE) VESA(0): No matching modes
(II) UnloadModule: "vesa"
(II) UnloadModule: "ddc"
(II) UnloadModule: "vm86"
(II) Unloading /usr/lib/xorg/modules//libvm86.so
(II) UnloadModule: "int10"
(II) UnloadModule: "vbe"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```
Complete logfile here: [http://www.goatsgotohell.com/gnux/Xorg.0.log]("http://www.goatsgotohell.com/gnux/Xorg.0.log")
I'm using a Acer 5110 laptop. AMD Turion 64 X2, ATI Xpress 1150 chipset, ATI X1600 mobility graphics card.

I've installed 6.06 on this computer before and did not get this error.

---

### Post by Dark_Neo on 2007-05-23
I'm getting the same problem on my Fujitsu Siemens Amilo XI 1546 (Intel Core Duo, 1GB RAM, unknown chipset, ATI X1800 Mobility), finally got it installed using the alternative CD, but the problem happens at boot too. I've tried editing the xorg.conf and removed all modes except 1440x900 but still no luck.

Sorry no log since I can't get wireless working either, but it looks like exactly the same problem as wildegnux.

---

### Post by swudee on 2007-05-24
Hi

I had a similar problem with Edgy. Try, I think it was F4, the options at the bottom of the screen to set VGA resolutions. It seems it was unable to determine the correct settings, Manually setting at the beginning worked for me.

---

### Post by Dark_Neo on 2007-05-24
I tried that, no luck, and now it's booting from my install it's definately something in the X configuration that's causing the problem. I'll try and post my xorg.conf when I get back from work.

---

### Post by Dark_Neo on 2007-05-24
Right I've got it working, just follow the guide here: [http://ubuntuforums.org/showthread.php?t=414194]("http://ubuntuforums.org/showthread.php?t=414194")

---

