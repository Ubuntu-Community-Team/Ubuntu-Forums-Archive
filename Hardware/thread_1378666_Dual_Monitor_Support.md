---
title: "Dual Monitor Support"
date: 2010-01-11
forum: Hardware
---

### Post by Niko Johnson on 2010-01-11
Hey Everyone, I just got a new monitor with and a VGA2USB adapter. it works good in windows but I don't want to use windows!! its a Tritton USB2VGA and i cant seem to find any drivers for it or any good documentation on how to add a vga2usb monitor in my /etc/x11/xorg.conf file... any help is well appreciated

---

### Post by windoze87 on 2010-01-11
[https://help.ubuntu.com/community/USB2VGA](https://help.ubuntu.com/community/USB2VGA)

Dig that. It may help you out.

---

### Post by Niko Johnson on 2010-01-11
i already tried that artical, thanks thoe. do you know of anyother ones i can take a look at? has anyone else successfully set up dual monitors in ubuntu karmic?

---

### Post by ironstorm on 2011-09-10
There **may** to be a distro that implements support for the MCT 0711:5110 chipset found in your device (if its an XD300)... see here about MAXI:  [http://ubuntuforums.org/showthread.php?p=11239619](http://ubuntuforums.org/showthread.php?p=11239619)

You need to do lsusb and look for MCT to know if it's the same chipset...

---

