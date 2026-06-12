---
title: "ubuntu with intel (graphics)"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by DeezOnLinux on 2009-02-23
alright so ive searched the forums, and i cant seem to find something that pretains to my quetion. 

i installed ubuntu 8.04 and because im using an intel graphics card i guess, it installed in safe graphics mode. which sucks. i downloaded something off linux threw my updates, it said something about intel driver support? please can anyone help me get out of graphics safe mode.......my display is also at 800x600


i have a Vaio sr if it helps at all

---

### Post by bazzer on 2009-03-13
In the past I've had to tell xorg (the display server) that I want it to use a particular driver. To do that, I've edited the /etc/X11/xorg.conf file and put one of the following lines inside the 'Device' section:
```
Driver "i810"
```
or
```
Driver "intel"
```
Let us know how you get on with that?

---

