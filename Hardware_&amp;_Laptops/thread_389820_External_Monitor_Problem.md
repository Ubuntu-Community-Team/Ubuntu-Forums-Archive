---
title: "External Monitor Problem"
date: 2007-03-21
forum: Hardware &amp; Laptops
---

### Post by caspermyboy on 2007-03-21
Hi folks,

I'm running feisty on a X31 Thinkpad, everything runs great but i'm having trouble when connecting to an external monitor.

I cannot get the external monitor to work correctly at 1440x900. the Thinkpad has a screen res of 1080x786 and this works fine on both the laptop screen and the external monitor. What i would like to be able to do is use the external monitor at it's native 1440x900 setting but this does not seem to work. I have tried the following:

* Editing the xorg.conf to add in "1440x900" at each colour depth
* Running dpkg-reconfigure xserver-xorg and using the advanced options to manually enter the horizontal and vertical refresh rates from my screen (Benq FP91G+)

Each time i get the same result, the spalsh screen seems to be at the new 1440x900 res (but looks a bit odd - background does not reach the edge of the screen) then when Gnome starts its defaults to 1080x786 @ 75hz. I can change this to 1440x900 (but it will not let me select 75hz i can only get 60hz) the screen image is then not centered on the screen and the display has a strong yellow cast .

What am I doing wrong? I would love some tips as to how to get this external screen working correctly with this laptop.

thanks in advance,

casp.

---

