---
title: "Thinkpad T42 LCD after undocking"
date: 2006-09-29
forum: Hardware &amp; Laptops
---

### Post by samm on 2006-09-29
I have a Thinkpad T42 with the docking station.  Normally I use an external CRT display hooked up to the VGA port of the dock and leave the laptop closed. How can I enable the LCD display to turn on when I undock my laptop?

---

### Post by samm on 2006-09-29
I answered my own question after some more googling:

[http://www.thinkwiki.org/wiki/Fglrx](http://www.thinkwiki.org/wiki/Fglrx)

aticonfig --enable-monitor=lvds

then

xrandr -s 1024x768

---

