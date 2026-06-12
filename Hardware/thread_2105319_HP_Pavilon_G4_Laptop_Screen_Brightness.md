---
title: "HP Pavilon G4 Laptop Screen Brightness"
date: 2013-01-15
forum: Hardware
---

### Post by MrAndroid007 on 2013-01-15
can you help me with the brightness problem? i can't control the brightness of my hp pavilon g4

---

### Post by Toz on 2013-01-15
Hello and welcome to the forums. 

I have moved your post to its own thread.

Which version of Ubuntu are you using?

Can you open a terminal window, type in (or copy/paste) the following commands, and post back the results:
```
cat /proc/cmdline
```
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
```
```
sudo lspci -vnn | grep -A12 VGA
```

---

