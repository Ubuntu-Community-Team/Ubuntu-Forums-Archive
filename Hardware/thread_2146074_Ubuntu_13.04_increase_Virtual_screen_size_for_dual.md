---
title: "Ubuntu 13.04 increase Virtual screen size for dual monitor"
date: 2013-05-17
forum: Hardware
---

### Post by doomster on 2013-05-17
So, i am working on Ubuntu13.04 on an FS Amilo pro V3505 laptop. it is equipped with Intel 945gpu and maximum screen resolution of 1280.x800. i wanna work Dual display with my main monitor, an LG22" that goes up to 1980x1050. 

The error :   
Requested size (2304, 800) exceeds 3D hardware limit (2048, 2048).
You must either rearrange the displays so that they fit within a (2048, 2048) square

Now as i recall, Virtual screen size can be set from xorg.conf, though im on a new installation, and using the default drivers, wich means that i have an empty xorg.conf. 
i tried also to use arandr application, but when it puts the monitors on the correct resolution, Desktop lags alot and/or freezes.

As i recall, no 2d support is embeded for unity on the last version. whats the way to change virtual screen size for the 3dunity to work correctly? 

Thank you in advance. 

Dimitris. 

PS: good to be back after long time of absence :)

---

### Post by doomster on 2013-05-17
common guys, im stuck here, any ideaS? or i rollback to previous version?

---

### Post by linrunner on 2013-05-17
Hi,

no way. 2048x2048 is a known limitation for that graphics chip.

---

### Post by doomster on 2013-05-18
well thanks. had to reroll to ubuntu-gnome. really nice work there,and with gnome-falback, its even faster:) will use unity when i get my system76 dream :)

---

