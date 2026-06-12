---
title: "RT2860 Drivers in Karmic 9.10 - can't load module"
date: 2010-04-20
forum: Hardware
---

### Post by score100 on 2010-04-20
Hey guys,
i'm just trying to get my wifi up and running without constantly disconnecting on my eee 1008ha, running ubuntu netbook remix 9.10. I downloaded the correct drivers and followed the instructions from [http://ubuntuforums.org/showthread.php?t=1045703](http://ubuntuforums.org/showthread.php?t=1045703) ,
but I always seem to fail at this part
> **Fass said:**
> 

Now, while still root modprobe the driver module:

```
modprobe rt2860sta
```Give it a minute to create the ra0 device node, and network manager should now be able to display all visible wireless networks in your area, meanwhile you can stop being root and make sure that the module was probed correctly by checking the output of lsmod looking for the rt2860sta module.



when I enter modprobe I only get - ```
[root@moritz-laptop:/home/moritz# modprobe rt2860sta
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-date-here.bkp, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

```The warning thing is a common appearance that doesn't bother I think, but there's nothing happening further. No creation of a device node or whatsoever.
And my iwconfig shows no sign of  a rt2860sta.

So guys, got any idea?

---

### Post by score100 on 2010-04-22
bump

---

