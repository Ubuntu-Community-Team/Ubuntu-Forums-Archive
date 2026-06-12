---
title: "You've heard of Crazy Frog, Now comes Crazy Mouse!"
date: 2005-08-11
forum: Hardware &amp; Laptops
---

### Post by c-m on 2005-08-11
I am running ubuntu using a USB Keyboard and a ps/2 optical mouse. All was fine or so i thought untill all of a sudden my mouse pointer went into some sort of spasm and started randomly running about the screen and loading things up and clicking on items.

I've noticed it seems to have these spasms if i haven't used the mouse for a while (30mins) and come to use it again, or if i unplug the mouse to use in another computer plug it back it.

After the 10 second spasm all is seemingly normal, but its quite annoying.

Does anyone have any ideas on how to fix this?

---

### Post by Cyberkef on 2005-08-11
[QUOTE=c-m]... and a ps/2 optical mouse. [/QUOTE]
I had this some months ago, my mouse was broken :)

After the first "spasms" I used a ps/2 -> USB thingie, and it made my mouse "work" again... for 2 weeks, then it finally died.

In /var/log/messages i found:

Mar 27 20:22:40 localhost kernel: psmouse.c: bad data from KBC - bad parity
Mar 27 20:22:42 localhost kernel: psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.
Mar 27 20:50:25 localhost -- MARK --
Mar 27 21:06:01 localhost kernel: psmouse.c: bad data from KBC - bad parity
Mar 27 21:06:03 localhost kernel: psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.
Mar 27 21:07:11 localhost kernel: psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
Mar 27 21:30:25 localhost -- MARK --
Mar 27 21:36:58 localhost kernel: psmouse.c: bad data from KBC - bad parity
Mar 27 21:36:59 localhost kernel: psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.

---

### Post by c-m on 2005-08-12
my mouse is fine in windows, and was fine in yoper, its only ubuntu that i seem to have this problem. thought it is somethig i can live with i'd still like it sorted.

---

