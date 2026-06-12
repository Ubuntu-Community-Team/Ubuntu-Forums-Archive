---
title: "LM-Sensors Site Warns of Potential Hardware Damage"
date: 2013-09-14
forum: Hardware
---

### Post by buzzingrobot on 2013-09-14
A September 5, 2013 entry at the lm-sensors site ([http://www.lm-sensors.org/](http://www.lm-sensors.org/)) warns of "serious trouble", potentially hardware damage, running sensor-detect in lm-sensors version 3.3.2 or lower, and recommending patches for those packages.

The Raring repository contains 3.3.2 and the changelog does not indicate the patches have been included. 

Is a patched deb of 3.3.2 available elsewhere?

(3.3.3 is in the Saucy repo, but I'm not comfortable deleting the dependencies it wants to.)

---

### Post by tgalati4 on 2013-09-14
When you run through the sensors-detect query process, there are several warnings and disclaimers as probing the hardware directly can cause some issues on some hardware.  I have never heard or read about such an issue.  Immunizations are supposed to keep you from getting sick, yet people get sick from them.

---

### Post by buzzingrobot on 2013-09-15
Right, I am familiar with using sensor-detect.

The post by the lm-sensor devs does not make it clear if this problem is actually flagged by sensors-detect in 3.3.2 and lower. I suspect it is not because they went out of their way to post the warning and to create the patch.

It seems prudent that the package in the Raring repos would be patched and bumped to 3.3.3.  The most recent entry in the changelog in the repo is about one year old.

---

