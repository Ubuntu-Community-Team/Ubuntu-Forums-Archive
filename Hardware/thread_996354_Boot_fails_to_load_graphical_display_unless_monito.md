---
title: "Boot fails to load graphical display unless monitor is plugged in."
date: 2008-11-28
forum: Hardware
---

### Post by FugitivePuppeT on 2008-11-28
I'm using an Averatec 3200 laptop, when I boot it up if I DONT have a monitor plugged in a get stuck at a loop of "Running boot scripts". However, if I DO have a monitor plugged in it boots perfectly and I can then unplug the monitor and use the laptop as normal.

Any ideas?

BTW Graphic Processor = S3 UniChrome.Using basic Ubuntu/Gnome fully updated.

---

### Post by mOOky on 2009-01-20
I have an Averatec 3700 that I'm installing Ubuntu 8.10 on (and then Edubuntu) and I could not get the installer to successfully load without adding "vga=792 xforcevesa" which forced it to use the VESA mode video at 1024x768 24-bit.

That allowed me to get it installed successfully, but now it is stuck in 800x600 max resolution so I'm trying to find a good Linux driver for the chipset.

---

