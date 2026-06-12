---
title: "Screen resolution"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by rijo_newbie on 2009-03-10
Hi
I have installed 8.04 and getting into it ,
but when i reboot system it switches screen resolution 
1st boot  1024 x1280
reboot
screen now 600 x 800
reboot
screen back to 1024 x 1280
reboot
screen now 600 x 800
etc
I am not selecting any start up switches 
so what am I missing please 

Rijo

---

### Post by Neo_The_User on 2009-03-10
System > Preferences > Screen resolution. If that doesn't help open up a terminal and read up on xrandr.

```

man xrandr

```

Also, post your xorg.conf file

---

