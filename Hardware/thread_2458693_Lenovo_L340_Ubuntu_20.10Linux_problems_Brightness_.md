---
title: "Lenovo L340 Ubuntu 20.10/Linux problems: Brightness + Wifi + Suspension (+Battery opt"
date: 2021-03-02
forum: Hardware
---

### Post by julio-netu on 2021-03-02
I'll request help and try to organize here any  information on  issues regards Lenovo L340 (my specific model is  81tr003br) with current Ubuntu 20.10 Kernel 5.8.0-44-generic

 **1. Brightness (backlight) can't be changed.**
 I've tried some tweaks, but nothing seems to work.
 I'm using the following program as a workaround:[INDENT] sudo apt install brightness-controller

 [/INDENT]
This won't fix anything but works to change brightness until system is restarted
  
 > I have already tried an early Ubuntu 21.04 live image, still the same problem.

 > I already tried Noveau and Nvidia drivers, nothing changed.

This bug was already addressed (not solved):
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1863407](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1863407)

  

 **2. System can't resume from suspension.**

 Maybe some advanced tweaks with kernel and all that can fix it, but I haven't tried then yet.

  

 **3. Wifi sometimes doesn't work.**

 Wifi seems to work fine, but sometimes it just won't work after system boot, usually it will work after restart.

_ Workaround_: turn wifi off and on again seems to fix this problem in the current session.
  

 **4. Batery **

 Batery consumption is within "normal", which gives around 3:30 hours  of not intensive use. But Ubuntu lacks any preinstalled tweak to improve  battery consumption. Later i'll try auto-cpufreq and TLP.

**5. Touchpad hotkey toggle (F6 or FN+F6) doesn't work**

---

