---
title: "Display viewport smaller than screen"
date: 2012-05-19
forum: Hardware
---

### Post by djailer on 2012-05-19
I have an old Inspiron 8100 and have loaded Ubuntu. Xubuntu desktop and xfce destops.  When it boots I suspect it is booting using ubuntu but it shows the Xubuntu splash screen while it loads.  I also get an error saying it cannot find the correct display resolution.   I tried it with ' nomodeset' and without.   I have the Nvidia common-update drivers and Nvidia is listed as the driver in /etc/x11/xorg.conf.  Where should I start to troubleshoot this?


Doug

---

### Post by papibe on 2012-05-19
Hi djailer.

My guess is you have a relatively old Nvidia card. GeForce2 Go?

I'm afraid at this moment, the oldest version of the driver (173 and 93) are not compatible with the new versions of Ubuntu (actually any Linux distribution using an up-to-date versions of the Xorg - the windows manager).

This may change in the near future if Nvidia decides to update their legacy drivers to support the current version of X.

For now, I would recommend uninstalling the nvidia driver, and using the default open source driver, called nouveau. This days it is working pretty well supporting Nvidia cards.

Regards.

P.D.: sources: [Bug #948053]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/948053") and [Bug #990539]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/990539").

---

### Post by djailer on 2012-05-19
Thank you.   After reading all I could find about trying to get nvidia to work I assumed nouveau was a bad idea.  I will get rid of nvidia and try that....nothing really to lose anyway.   I doubt the screen will get any smaller :rolleyes:

---

