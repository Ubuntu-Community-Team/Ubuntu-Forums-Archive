---
title: "Crashes when power cable unplugged"
date: 2011-01-19
forum: Hardware
---

### Post by shapiska on 2011-01-19
I recently installed ubuntu 9.04 (64 bit) on my dell laptop. I am having a problem using it when it is unplugged. If i boot it without it being unplugged i get to the login screen but cannot move the mouse or type. If it is plugged in everything works fine, but as soon as I unplug it everything on the screen freezes, the mouse and keyboard don't work, and the sound stops. Thank you in advance for your help.

---

### Post by jamesa00789 on 2011-02-19
I am also having the exact same problem on a Pakcard Bell EasyNote MZ.

---

### Post by DaveJ1337 on 2011-03-18
I have the same problem on Dell Inspiron 11.

---

### Post by Cloudane on 2011-04-25
Checking in with this problem on my Eee 901.  Next boot I get a corrupted display and minimum brightness and it locks up again - I have to yank the battery and start from cold.

Edit: Solved.  It doesn't seem to like switching CPU performance modes via Jupiter Applet - when I was doing so earlier I had to move the mouse around or else it'd crash in the same way.  But I never thought - it also tries to switch when the power cord is added or removed.  Even though I have "power save" set for both modes it obviously triggers something enough to crash it in any case.  Moving 00-jupiter-cpu out of /etc/pm/power.d removes this functionality, and the bug with it.

---

