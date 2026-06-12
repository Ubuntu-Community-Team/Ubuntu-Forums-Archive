---
title: "APM level 255 (disabled) - good or bad?"
date: 2012-12-05
forum: Hardware
---

### Post by mgngapyin on 2012-12-05
I have a HP-mini-110-3525 netbook with Ubutu 12.10 installed. Hard Disk is giving me weird noises whenever I use Ubuntu with default settings. The nosie is not present in Windows or Ubuntu Live Flash Drive. 

I was feared that my Hard Disks might be failing, and ran Smart Test from Disks (gnome-disks) from Ubuntu and Crystal Disk Info from Windows. Both tests showed the overall assessment is OK, and drive is healthy. 

I found out that my hard disk is 

> ATA Hitachi HTS72503
powered on for one and a half yearsSince the hard disk was giving me weird sound, I set the APM level to 255 (disabled) from the gnome-disk - "Drive Settings". The weird sound disappeared, and the performance improved a little bit. 

I run the SMART test again, and found out that 

> "start/stop count" level is 3974.

"load/unload cycle count" is 410845. 

Hard Disk is working fine. No more weird noises. But I'm curious whether setting APM levle to 255 would shorten my hard disk lifespan. I've read [http://ubuntuforums.org/showthread.php?t=1924159](http://ubuntuforums.org/showthread.php?t=1924159), but doesn't understand at all. My netbook is powered on 24/7, and suspend after one hour of inactivity.

---

### Post by lancecherry on 2012-12-05
I highly recommend you should setting it's value to 255 for protecting the HDD lifetime(which means disable the function).
I also have a HT HDD in my thinkpad x220i,which have the "C1 issue".It s working on a unstable speed with sound like scratching... I cannt take it anymore so i turn the APM off by its official tools.
When it s done,i feel much better and HDD works on regular finally.
BTW, You could google it with key words "load cycle count problem" or "hdd C1 issue",actually the same thing they were talking about.
That s my experience and hope it can be helpful :)

---

### Post by mgngapyin on 2012-12-05
Thanks, lancecherry. This is a great help.

---

