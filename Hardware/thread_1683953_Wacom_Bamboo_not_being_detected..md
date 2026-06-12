---
title: "Wacom Bamboo not being detected."
date: 2011-02-08
forum: Hardware
---

### Post by unhunkygiuy on 2011-02-08
Hi, I just bought a Wacom Bamboo Pen tablet, and ubuntu is not detectng it. I tried [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom) and [http://ubuntuforums.org/showpost.php?p=7234134&postcount=176](http://ubuntuforums.org/showpost.php?p=7234134&postcount=176)  but neither of those are working for me. When I run "xinput --list" or "more /proc/bus/input/devices" The tablet does not show up. Anyone have any idea of what to do?

Also, I have tried the steps on the Linux Wacom Project...

---

### Post by Favux on 2011-02-08
Hi unhunkygiuy,

What release of Ubuntu are you using?  What's the model number of your tablet (on the bottom)?  You can get the product ID by entering in a terminal:
```
lsusb
```
See the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").  There is a box near the top that lists the models.

---

### Post by unhunkygiuy on 2011-02-08
I am using 10.10, the model is "CTL-460".  lsusb gives me: 
Bus 004 Device 002: ID 056a:00d4 Wacom Co., Ltd

---

### Post by unhunkygiuy on 2011-02-08
> **Favux said:**
> See the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").  There is a box near the top that lists the models.

THANKS! That helped a lot. It is now fully working.:D

---

### Post by Favux on 2011-02-08
Good.  Nice job.  Remember if you use the sample script you can get rid of the other sections, you only want the stylus section.

---

