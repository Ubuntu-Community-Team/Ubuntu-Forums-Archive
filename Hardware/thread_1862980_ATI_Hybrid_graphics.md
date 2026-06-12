---
title: "ATI Hybrid graphics"
date: 2011-10-17
forum: Hardware
---

### Post by Meefle on 2011-10-17
So I have a HP DV6t Quad-core Edition with an intel/ati hybrid graphics setup. I have a 11.10 working pretty well on it, but each time I start up I have to turn off the discrete ATI card using the built in gpu switcheroo. I don't have the fglx driver installed or the ATI drive either but I see that it's up to version 11.9.  Has anyone tried 11.9 with a hybrid graphics system? Does the later version of the driver detect the intel and ati graphics and allow for switching?

---

### Post by fantasm!c on 2011-10-17
As you can see in these threads:
[http://ubuntuforums.org/showthread.php?t=1861541](http://ubuntuforums.org/showthread.php?t=1861541)
[http://ubuntuforums.org/showthread.php?t=1862164](http://ubuntuforums.org/showthread.php?t=1862164)

And this bugreport
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/813809](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/813809)

You can see that the ATI driver is not working. And it is not a high priority issue unfortunately.

You can disable the ati with vgaswitcheroo and in it might be an idea to put it in the rc.local file so it will be automatically disabled at startup.

---

### Post by Meefle on 2011-10-17
Thanks! This setup will work and I edited rc.local to turn off the ATI card on startup.

---

