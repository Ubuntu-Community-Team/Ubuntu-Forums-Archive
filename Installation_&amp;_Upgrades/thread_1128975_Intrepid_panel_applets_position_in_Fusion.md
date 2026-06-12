---
title: "Intrepid panel applets position in Fusion"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by L0wCr4WL on 2009-04-18
I have installed Intrepid Ibex on Mac OS X running in a VMWare Fusion 2.0.4, latest VMWare tools installed.

The aplets in the Gnome panels are stuck halfway across the screen width (1440 x 900 standard MacBook Pro resolution).

I tried reading up on Gnome panel configuration and checking for lock condiitons on applets, etc. Nothing seems to work to get them into place.

It's really just an annoyance thing. I have included a screenshot of my desktop as well as the output of gconftool 

```
gconftool-2 -R /apps/panel
```

utility as metioned on [another thread]("http://ubuntuforums.org/showthread.php?t=1115977&highlight=panel+applet+position&page=2") for (hopefully) more info.

Anyone got any ideas how to fix this one?

---

### Post by ajgreeny on 2009-04-18
Right click on the applet icon, uncheck "Locked" if it shows a check mark and then right click again and choose "Move".  Now when you move your mouse the icon will move with it.  It should be as simple as that; it certainly is in a PC.

---

### Post by L0wCr4WL on 2009-04-18
WOW! Don't I feel silly!! :D

I was missing that "Move" step. I guess I have gotten too used to Windows!!

THANKS!!! problem solved!

---

