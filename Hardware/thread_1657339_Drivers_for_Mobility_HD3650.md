---
title: "Drivers for Mobility HD3650"
date: 2011-01-01
forum: Hardware
---

### Post by gianvito on 2011-01-01
Hi all,
I'm asking myself if I'll never get a really working graphic with Ubuntu .....

I have an ATI Mobility HD3650 ... 

If I install FGLRX drivers, they works but they have the famous tearing problem (if I set VSync to Always ON in amdcccle, it resets at reboot...and, when enable the system is slower!)

If I keep the open driver...they works VERY WELL..really much better than closed ones! BUT.....power management doesn't work...my cards is always at maximum clock and so my notebook fan is at 100%...

I found this and tried it (dynamic clocks):
echo "dynpm" > /sys/class/drm/card0/device/power_method

it gives me flickering one time each 2-3 seconds....unusable

then tried thi (fixed profile, to medium clocks):
echo "mid" > /sys/class/drm/card0/device/power_profile

it gives me lots of graphic corruption..unusable

So.....is there a way to fix it? :( 
Thanks

---

### Post by gianvito on 2011-01-02
bump..

---

### Post by gianvito on 2011-01-03
Nothing to do? :(

---

