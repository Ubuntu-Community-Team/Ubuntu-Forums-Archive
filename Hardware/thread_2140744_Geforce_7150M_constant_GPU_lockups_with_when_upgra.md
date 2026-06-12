---
title: "Geforce 7150M constant GPU lockups with when upgraded to Ubuntu 13.04"
date: 2013-04-30
forum: Hardware
---

### Post by Yowan on 2013-04-30
So today I basically upgraded my previous 12.10 installation to 13.04, the procedure took more than 2 hours and ended up with the installer telling me that not all packages could be upgraded.

Everything from there went smooth except for the some warnings about my bcm b34 driving during the next boot, everything was still working until I clicked on the Unity bar, the display would flash, colors were lines appeared and I got those 'failed to idle channel' errors. To my understanding the cause is the half baked nouveau driver.

Booting with kernel 3.5.x is possible but everything is slow and the resolution is low. The software sources lists an 'unknown device', I also can't apply any changes there, whenever I select the Nvidia or Broadcom proprietary nothings happens upon authentication. Networking (external ralink wifi adapter or ethernet) doesn't work either, the same goes for mounting any usb drive.

My previous 12.10 was working fine, the previous nouveau driver never caused any issues. The laptop is an HP dv9608nr, what am I supposed to do that this point? A clean install isn't something that I'm considering since this system is used for Android kernel compiling.

[http://i.imgur.com/hjxOHvS.jpg](http://i.imgur.com/hjxOHvS.jpg)
[http://i.imgur.com/V3W33DG.jpg](http://i.imgur.com/V3W33DG.jpg)
[http://i.imgur.com/3aso4Dt.jpg](http://i.imgur.com/3aso4Dt.jpg)
[URL="http://i.imgur.com/UQYBe3l.jpg"]http://i.imgur.com/UQYBe3l.jpg



[/URL]

---

