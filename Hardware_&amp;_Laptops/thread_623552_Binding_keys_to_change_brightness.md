---
title: "Binding keys to change brightness"
date: 2007-11-26
forum: Hardware &amp; Laptops
---

### Post by eitan_a on 2007-11-26
Hi, I'm on a Sony Vaio VGN-N130 laptop.  I would like to bind 2 keys to increase and decrease LCD brightness.  Right now, I'm using the brightness applet to change it, but it's a bit cumbersome.  Gnome power manager can change my brightness too but I don't know what commands those 2 programs are using to change my brightness.  

I would like to bind it to a key, and it would be even better if I can get a graphical way to see what my brightness is at when I change it, like my volume does.  The best thing would be to bind them using FN-F5 and F6 (keys for changing brightness in XP) but they don't do anything, even when using xev to test.

---

### Post by eitan_a on 2007-11-26
OK so I binded two keys to brightness up and down scripts.  I would like to get the graphical pop-up telling me what level of brightness I'm at, like when changing volume.  How do I go about doing this?

---

### Post by cknight on 2007-11-28
While not a graphical popup, there is a program called 'osdsh' (daemon) and its controller counterpart 'osdctl' which will allow you to output a line graph to the screen.  The fluxbox keys tutorial in my signature has a screenshot of what this looks like for a volume change, however the same concept could be built for a brightness change assuming you have access to the numbers involved in the brightness setting.

Could you post your solution for binding keys to the brightness scripts?  I'd be interested in seeing the script involved or how it was accomplished.  Thanks!

---

