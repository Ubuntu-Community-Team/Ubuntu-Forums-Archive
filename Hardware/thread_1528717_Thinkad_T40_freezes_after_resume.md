---
title: "Thinkad T40 freezes after resume"
date: 2010-07-11
forum: Hardware
---

### Post by softwarejonas on 2010-07-11
Suspend to RAM/Resume does not seem to work on my system anymore. It used to work just fine with Ubuntu 09.04 but since I reinstalled/upgraded to Xubuntu 10.04, my Thinkpad freezes on resume.
I have tried using the build-in "pm-suspend" script as well as manually suspending using 
```
echo -n mem > /sys/power/state
```
So if I use pm-suspend, I end up with a black screen (backlight turned on) and the system is unresponsive.
If I suspend manually (without vbetool), I just get weird colors and an unresponsive X (that even is not an X anymore).
Btw Hibernating works fine.

Any help would be greatly appreciated.

---

