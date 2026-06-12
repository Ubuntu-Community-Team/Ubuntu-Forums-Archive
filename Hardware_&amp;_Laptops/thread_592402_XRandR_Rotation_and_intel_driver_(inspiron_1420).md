---
title: "XRandR Rotation and intel driver (inspiron 1420)"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by ghstzr0 on 2007-10-26
I have a Dell Inspiron 1420n pre-loaded with Ubuntu.  I have since upgraded to 7.10 (fresh install).  Most everything works fantastic, but obviously I have a problem:

I would like to use an external Samsung 21" widescreen monitor in PORTRAIT mode.  I have noticed that compiz and the new intel 945gm cards are "incompatible"... but it seems that compiz is also incompatible with xrandr rotation... So I tried it in metacity - no dice.

When I issue the command `xrandr --ouput LVDS --off --output VGA --mode 1680x1050 --rotate left` (in metacity) the screen properly rotates.  However the screen refresh is all choppy and things aren't drawn correctly.  Interestingly enough, if I enable my LVDS as an extended desktop, the screen refreshes correctly, but EXTREMELY SLOW!

What's the deal?  Should I go back to using i810?  I would really hate to dump Gutsy...:confused:

---

### Post by ghstzr0 on 2007-10-26
Bumb... Help!

---

### Post by ivanov on 2007-11-14
did you have any luck with this? I'm having the same issue

---

### Post by ivanov on 2007-11-15
for me it was the known issue about screen size bigger than 2048x2048 that caused really slow refreshes on the external monitor. resizing to 2047x2047 solved the problem.

---

