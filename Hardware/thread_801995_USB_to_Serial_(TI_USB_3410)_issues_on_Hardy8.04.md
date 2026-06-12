---
title: "USB to Serial (TI USB 3410) issues on Hardy/8.04"
date: 2008-05-21
forum: Hardware
---

### Post by kWahab on 2008-05-21
Help!
Having trouble getting the USB to Serial cable to work under a fresh install of Hardy. 
I have used the cable (with my WLL phone Huawei ETS 2xxx) in feisty and gutsy without any problems using this guide
[http://www.openpages.info/huawei.html](http://www.openpages.info/huawei.html)

My guess is that hardy has a newer version of udev and the rule file (026_ti_usb_3410.rules) doesn't work. I keep getting the "probe failed with error -5" message. 

I found a file in /etc/udev (i forget which, i'm in windows now) which had some instructions on rules file naming. so I tried different names (numbers other than 26, like 65 85 etc.) for the rule file. All to no avail, the error simply doesn't go away.

Tried the above on my laptop (Dell Inspiron 6400/E1505) and my desktop (dell something 1100) with same issues.

Currently I'm without internet in Linux and have to use Windows. Someone please help. 

Thanks
Khawar

---

### Post by lhommesc on 2008-05-24
I have the same issue on HH 8.04 amd64.

---

### Post by ali.shahbaz on 2008-05-25
me too...am thinking of rolling back to 7.10 till this gets solved....i did visit this site which helped me remove the '-5' error.but still no ttyUSB0

[http://www.pkuhar.com/blog/?cat=6](http://www.pkuhar.com/blog/?cat=6)

please visit the link urself and let me know if something comes up...i have also queried the ubuntu Launchpad system on this...will keep u updated

---

### Post by kimguru on 2008-05-28
me too its not udev problem i think as it works good with kernel<2.6.24.it has something to do with this kernel.

---

