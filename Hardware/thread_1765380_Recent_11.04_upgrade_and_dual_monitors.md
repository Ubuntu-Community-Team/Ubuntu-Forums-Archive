---
title: "Recent 11.04 upgrade and dual monitors"
date: 2011-05-23
forum: Hardware
---

### Post by krlcmpbll on 2011-05-23
I recently upgraded to 11.04 and my dual monitor display has stopped working properly. I am on a Dell 1440 laptop, with an external 24" samsung display. There are issues with the monitor and the only way to get it up to it's proper resolution was to use the following script:

#!/bin/sh
xrandr --newmode "1920x1200_60.00"   193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync 
xrandr --addmode VGA1 1920x1200_60.00
xrandr --output VGA1 --mode 1920x1200_60.00

This took me forever to figure out, and it was finally working like a charm on 10.10 Now of course it's broken and when I run this, I end up with blank areas on my desktop and ultimately have to reboot to retain my desktop (however at the wrong resolution). 

If anyone might be able to help it would be much appreciated, otherwise I'm going to have to start from scratch and reinstall 10.10.

Thanks

---

### Post by greencookie on 2011-05-26
I just submitted a [similar thread]("http://ubuntuforums.org/showthread.php?p=10863373#post10863373"). Also, have you tried running ```
unity --replace
```

It worked for me, but not 100% of the time.

---

### Post by svast on 2011-05-31
I have a toshiba R830, with Intel HD graphics, no discrete card.

in order to properly have dual display running (also 24" 1920x1200 external display), I had to disable Unity, and start only with Gnome classic (no 3D effect / compiz).
There seems to be a bug with the latest Intel drivers not properly dealing with the Sandy bridge gpu, in my case...

---

