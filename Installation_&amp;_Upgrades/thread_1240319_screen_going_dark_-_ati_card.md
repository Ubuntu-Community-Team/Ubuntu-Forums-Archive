---
title: "screen going dark - ati card"
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by stephan0h on 2009-08-14
hi group,

after last upgrade my system has a strange behaviour - intermittently the screen goes completely dark - and the system is dead - only hard-reboot revives it again.

This is the (k)ubuntu version:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"

Somehow i think it might be connected to my graphics-driver because for instance it happens when maximizing a window - and when doing the same action with the same window after reboot it happens again. I use the non-proprietory ati-driver.

Are there people out there having similar problems??

I want to try a clean reinstall of the graphics driver. What's the best way to accomplish this?

Thanks,
Stephan

---

### Post by stephan0h on 2009-09-04
this was a continous headache - but maybe there's a simple solution.

not using openGL features seems to do the trick. i turned off kde eye-candy and turned off my fancy openGL screen saver - and the system seems to be more stable now. 

i suppose the reason for the troubles was that jaunty prevented me from using the proprietory ati drivers - and the open ati driver is probably buggier.

see also [http://ubuntuforums.org/showthread.php?t=1257961](http://ubuntuforums.org/showthread.php?t=1257961)

---

