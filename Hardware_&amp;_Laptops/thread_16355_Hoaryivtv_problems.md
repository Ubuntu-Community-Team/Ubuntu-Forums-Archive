---
title: "Hoary/ivtv problems"
date: 2005-02-20
forum: Hardware &amp; Laptops
---

### Post by ToS on 2005-02-20
Trying to setup the drivers for my PVR-250 using the instructions found [here](http://ubuntuforums.org/showpost.php?p=21407&postcount=8) , and I was able to compile and install the drivers (after installing my kernel headers). But when, I try to modprobe the ivtv module I get the following error:
```
$ sudo modprobe ivtv
FATAL: Error inserting ivtv (/lib/modules/2.6.10-3-386/kernel/drivers/media/vide o/ivtv.ko): Invalid module format

```

Doing a google search came up fruitless.  Any ideas?

edit: forgot to mention that I'm using hoary array5 with kernel version 2.6.10-3-386 and trying to install ivtv-0.2.0-rc3f

---

### Post by stults on 2006-04-11
I am having the same problem with breezy.  I am trying to get mythtv up and running with my Plextor Convertx TV-402U, but hit a snag right here.  Any help would be welcome.

---

