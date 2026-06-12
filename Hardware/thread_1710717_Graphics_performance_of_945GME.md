---
title: "Graphics performance of 945GME"
date: 2011-03-20
forum: Hardware
---

### Post by l0b0 on 2011-03-20
(Copy of a [Stack Exchange question]("http://askubuntu.com/questions/31174/graphics-performance-of-945gme"))

I'm getting terrible graphics performance in **NeverWinter Nights** (native with SoU+HotU+CEP2) on my Eee PC 1005HAB. Even with all graphics settings (including the "advanced" ones) at minimum I get about 2-10 FPS, depending on the scene. **Firefox** is really sluggish as well - Changing tabs often takes a second, and scrolling is laggy. The rest of the OS is running OK, although general performance seems to be even *worse* than my old Eee PC 900.

glxgears gives about 60 FPS, which is apparently as it should be (synchronized with the monitor refresh rate).

Bugs like [Launchpad #252094]("https://bugs.launchpad.net/ubuntu/karmic/+source/xserver-xorg-video-intel/+bug/252094") and the instructions for [Reverting the Jaunty Xorg intel driver to 2.4]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") are old enough that I'm afraid following the instructions would render the system unusable.

Are there any tips for improving graphics performance on this system that are still relevant for 10.10?

```
$ uname -a
Linux l0b0eee 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686 GNU/Linux

$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
    
$ glxinfo 
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
...
```

---

### Post by Shmantiv_Radio on 2011-03-20
> **l0b0 said:**
> (Copy of a [Stack Exchange question]("http://askubuntu.com/questions/31174/graphics-performance-of-945gme"))

I'm getting terrible graphics performance in **NeverWinter Nights** (native with SoU+HotU+CEP2) on my Eee PC 1005HAB. Even with all graphics settings (including the "advanced" ones) at minimum I get about 2-10 FPS, depending on the scene. **Firefox** is really sluggish as well - Changing tabs often takes a second, and scrolling is laggy. The rest of the OS is running OK, although general performance seems to be even *worse* than my old Eee PC 900.

glxgears gives about 60 FPS, which is apparently as it should be (synchronized with the monitor refresh rate).

Bugs like [Launchpad #252094]("https://bugs.launchpad.net/ubuntu/karmic/+source/xserver-xorg-video-intel/+bug/252094") and the instructions for [Reverting the Jaunty Xorg intel driver to 2.4]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") are old enough that I'm afraid following the instructions would render the system unusable.

Are there any tips for improving graphics performance on this system that are still relevant for 10.10?

```
$ uname -a
Linux l0b0eee 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686 GNU/Linux

$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
    
$ glxinfo 
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
...
```

You might want to try [apt:driconf](apt:driconf)

I would find a guide before you mess around with it.

---

