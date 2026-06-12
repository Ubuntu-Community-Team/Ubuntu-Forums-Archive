---
title: "x.org - video card STB ET6000 problem"
date: 2005-05-18
forum: Hardware &amp; Laptops
---

### Post by matej on 2005-05-18
I have problem with x.org tseng driver. My card is STB ET6000 with tseng chip and when I use tseng driver, almost all parts of gui of some apps (mainly xlib and qt apps) are filled with solid color (see [http://www.dvojka.cz/matej/desktop.jpg](http://www.dvojka.cz/matej/desktop.jpg)). These apps are completly unusable.

When I use vesa driver, everything is ok (but I have not hw acceleration, etc). 

In bugzilla there isn't anything relevant in tseng driver. 

My xorg.conf is attached.

Thanks for any suggestion.

---

### Post by matej on 2005-05-22
I have solved that problem.

I have to add these options to "device" section in xorg.conf:

Option "XaaNoSolidFillRect"
Option "XaaNoScanlineCPUToScreenColorExpandFill"

There is bug in acceleration part of tseng driver. See bugzilla: [https://bugs.freedesktop.org/show_bug.cgi?id=3361]("https://bugs.freedesktop.org/show_bug.cgi?id=3361")

---

