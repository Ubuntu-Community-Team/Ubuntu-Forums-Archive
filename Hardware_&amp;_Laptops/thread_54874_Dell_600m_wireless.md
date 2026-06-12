---
title: "Dell 600m wireless?"
date: 2005-08-06
forum: Hardware &amp; Laptops
---

### Post by obladi on 2005-08-06
My laptop is Dell Laptop Inspiron 600m. I have downloaded the recent version of Ubuntu Hoary and installed it. Ubuntu successfully detected my wireless card and it worked fine at first. But it is easily disconnected, and never returned, unless I reboot the laptop. Do I need to update some drivers or install additional softwares? 

By the way, how can I know what wireless card I am using?

---

### Post by luca_linux on 2005-08-06
It should be an Intel Pro wireless card.
So you'd better update the driver to the latest version.
Just follow the first part of this HowTo: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

Edit: it's an ipw2100 and not ipw2200. So you have to install the ipw2100 driver from [here](http://ipw2100.sourceforge.net) instead of the one mentioned in the HowTo. Also the firmware is different and you have to download it from [here](http://ipw2100.sourceforge.net/firmware.php?fid=4).
Anyway, the install steps are the same of ipw2200, so you can follow the HowTo as reference.

---

### Post by SqdnGuns on 2005-08-07
[QUOTE=obladi]My laptop is Dell Laptop Inspiron 600m. I have downloaded the recent version of Ubuntu Hoary and installed it. Ubuntu successfully detected my wireless card and it worked fine at first. But it is easily disconnected, and never returned, unless I reboot the laptop. Do I need to update some drivers or install additional softwares? 

By the way, how can I know what wireless card I am using?[/QUOTE]

I have a new 600m too but I have to use the ipw2200. Eveything is working great on my end, have you tried this: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

---

### Post by FrozenBubble on 2005-08-07
[QUOTE=SqdnGuns]I have a new 600m too but I have to use the ipw2200. Eveything is working great on my end, have you tried this: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)[/QUOTE]

ndiswrapper seems to work well
[www.ubuntuguide.org](www.ubuntuguide.org) has many useful tips

---

### Post by gmmazlum on 2006-02-11
hi all, I recently installed ubuntu and my wireless device is a Broadcom BCM4309 any ideas how to moun it?? (for a newbie) thanks in advanced.

---

### Post by gmmazlum on 2006-06-29
Finally I Can't use my wireless card... but have to change from breezy to dapper.. and follow these instruccions.. [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper#head-2d0c63404ca00426255ef1158a8afffc67925ef6](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper#head-2d0c63404ca00426255ef1158a8afffc67925ef6)

Thank you all

---

