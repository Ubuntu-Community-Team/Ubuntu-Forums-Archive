---
title: "amd 6870 driver support for 10.4?"
date: 2010-12-29
forum: Hardware
---

### Post by cinohpa on 2010-12-29
Will it ever happen? Should I just upgrade to 10.10 right now?

I recently upgraded to the 6870 and now I have to run in low-graphics mode to login at all.

I am kind of surprised things are working this poorly. To upgrade, I just swapped the cards and turned my machine back on. Should I have explicitly removed drivers or something? I'm wondering if my machine is in an in-between state trying to use proprietary drivers, and then not properly using the built in drivers....

Thanks.

---

### Post by IcarusR on 2010-12-29
First off Ubuntu does not write 'drivers'. Linux video drivers are built into xorg. 
Some video drivers are proprietary & can not be packaged into xorg or ubuntu. For those we have to use 'Hardware Drivers' application.

This video card is quite new & amd do not have linux drivers on their site yet. There is no support for it in xorg either.

Don't blame Ubuntu.

---

### Post by cinohpa on 2010-12-29
Thanks icarusR. I never said Ubuntu writes drivers.

Amd has released dev drivers for 10.10. I am asking if anyone thinks Amd will release similar drivers for 10.4 or if anyone has gotten the 10.10 drivers to work on 10.4.

I'm also asking if I should explicitly uninstall the proprietary drivers I have for an older card to properly take advantage of the drivers in the kernel.

---

### Post by IcarusR on 2010-12-29
cinohpa

Sorry it sounded like you were disappointed with Ubuntu level of support.

Kind of surprising that there are drivers for 10.10 but not 10.04 as it is LTS.

Not really got any advice here.

---

