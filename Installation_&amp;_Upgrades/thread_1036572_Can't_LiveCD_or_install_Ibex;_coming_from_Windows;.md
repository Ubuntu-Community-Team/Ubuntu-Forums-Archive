---
title: "Can't LiveCD or install Ibex; coming from Windows; no previous Linux"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by Tagus on 2009-01-10
Whether I select Install or Try without installing, the bar bounces back and forth, then fills 2&4/5 squares and stops. I've waited five minutes. I have to hold the computer's power button to turn it off. The CD and computer memory passed the tests; they're good.

---

### Post by chex_m8 on 2009-01-11
How much RAM u got?

---

### Post by Tagus on 2009-01-11
1 gb.

---

### Post by chex_m8 on 2009-01-11
Ok, might be a bad CD, was this CD made from download. did you run checksum to make sure all is good. You might try F4 and boot to safe mode.

---

### Post by Tagus on 2009-01-11
It passed MD5 when I downloaded. Roxio verified when it burnt the CD, and the Ubuntu disk verified itself. 
I just discovered F6 > remove quiet splash when booting; I'll try that and F4/safe mode.

---

### Post by Tagus on 2009-01-11
In regular mode without quiet start, it ended with a full screen of

udevd-event[xxxx]: run-program: exec of program '/sbin/modprobe' failed

with xxxx containing 4130, 4132, 4133, 4135, and a lot of others.

In safe graphics mode without quiet start, it ended

udevd-event[4298]: run-program: exec of program '/lib/udev/path_id' failed
udevd-event[4295]: run-program: '/lib/udev/path_id' abnormal exit
udevd-event[4842]: run-program: exec of program '/sbin/modprobe' failed
udevd-event[4924]: run-program: exec of program '/sbin/modprobe' failed
udevd-event[4926]: run-program: exec of program '/sbin/modprobe' failed
udevd-event[4930]: run-program: exec of program '/sbin/modprobe' failed

---

