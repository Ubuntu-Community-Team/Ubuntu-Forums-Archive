---
title: "Intel core i7 integrated graphics starts flickering and spams xorg.log"
date: 2011-12-19
forum: Hardware
---

### Post by samy234 on 2011-12-19
Hi I have a dell vostro 3550 laptop with hybrid graphics. An amd radeon hd 6600m and the integrated intel graphics. 

I'm only using the integrated chip. 

After a few days my Desktop started flickering, most of the time when I'm reading or editing text.

I noticed that xorg.log will get spammed with those messages over and over each time the display is flickering:

[  1754.512] (II) intel(0): Printing DDC gathered Modelines:
[  1754.512] (II) intel(0): Modeline "1366x768"x0.0   76.00  1366 1402 1450 1564  768 771 776 810 -hsync -vsync (48.6 kHz)
[  1754.512] (II) intel(0): Modeline "1366x768"x0.0   51.00  1366 1402 1450 1564  768 771 776 814 -hsync -vsync (32.6 kHz)
[  1756.693] (II) intel(0): EDID vendor "LGD", prod id 739
[  1756.693] (II) intel(0): Printing DDC gathered Modelines:
[  1756.694] (II) intel(0): Modeline "1366x768"x0.0   76.00  1366 1402 1450 1564  768 771 776 810 -hsync -vsync (48.6 kHz)
[  1756.694] (II) intel(0): Modeline "1366x768"x0.0   51.00  1366 1402 1450 1564  768 771 776 814 -hsync -vsync (32.6 kHz)
[  1757.540] (II) intel(0): EDID vendor "LGD", prod id 739
[  1757.540] (II) intel(0): Printing DDC gathered Modelines:
[  1757.540] (II) intel(0): Modeline "1366x768"x0.0   76.00  1366 1402 1450 1564  768 771 776 810 -hsync -vsync (48.6 kHz)
[  1757.540] (II) intel(0): Modeline "1366x768"x0.0   51.00  1366 1402 1450 1564  768 771 776 814 -hsync -vsync (32.6 kHz)
[  1760.994] (II) intel(0): EDID vendor "LGD", prod id 739


can anyone help me with this problem?

---

### Post by dabl on 2011-12-19
It seems there is a known bug:  [https://bugzilla.redhat.com/show_bug.cgi?format=multiple&id=753716](https://bugzilla.redhat.com/show_bug.cgi?format=multiple&id=753716)

More:  [http://ubuntuforums.org/archive/index.php/t-1559264.html](http://ubuntuforums.org/archive/index.php/t-1559264.html)

A person found a fix in Debian:  [http://forums.debian.net/viewtopic.php?f=10&t=71556](http://forums.debian.net/viewtopic.php?f=10&t=71556)

(may or may not work for Ubuntu, which is Debian-based but NOT the same as)

Seems Fedora users are also having it:  [http://estrip.org/articles/read/tinypliny/55328/](http://estrip.org/articles/read/tinypliny/55328/)[Solved]-External-Monitor-problems-on-Fedora-15.html

---

