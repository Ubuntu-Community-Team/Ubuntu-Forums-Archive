---
title: "hell of a time trying to install some linux"
date: 2006-02-13
forum: Installation &amp; Upgrades
---

### Post by jswan on 2006-02-13
First let me tell you about my computer, maybe there is something incompatable since its all pretty new.

DFI LANPARTY nF4 SLI-DR
AMD64 2x3800
eVGA GeForce7800 GT
2GB Corsair XMS
WD Caviar 250GB SATA

now the problem :( 
so far i've installed: ubuntu i386, ubuntu AMD64, fedora core 4 AMD64
all with the same results!

When ever i boot in, the screen will freeze almost instantly after logging into ubuntu. in Fedora it will wait like 30 seconds before freezing. It freezes when I do failsafe terminal, it freezes when i load GNOME, it freezes when i run KDE, it just ALWAYS FREeZES!!~!! I tried installing new Video drivers, but it usually freezes before it completely installs. The only time it doesn't freeze is when i work out of a plain text terminal.


SOOOOOOO
has anyone had this problem? Anyone have any ideas that can fix it?

---

### Post by taurus on 2006-02-13
Sounds like there is some problem with your video card.  Boot into a terminal and have a look at your /etc/X11/xorg.conf.  Make sure you use a "nv" driver for your nVidia video card right now and as soon as you have X running again, upgrade it to nVidia driver...  Otherwise, you can also use "vesa" as a driver for your video card for now.

---

### Post by jswan on 2006-02-14
thanks buddy

---

