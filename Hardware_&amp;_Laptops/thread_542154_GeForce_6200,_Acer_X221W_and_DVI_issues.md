---
title: "GeForce 6200, Acer X221W and DVI issues"
date: 2007-09-03
forum: Hardware &amp; Laptops
---

### Post by smcmaster on 2007-09-03
Hello all.

First off, in case I fail to mention them later:
* AMD Athlon64 3200+ @ 2200MHz
* ULi m1689 Chipset
* 1,254 MB DDR 266 RAM
* BFG nVidia GeForce 6200 OC 256MB AGP
* Ubuntu Feisty Fawn 7.04 AMD64
* Linux Kernel 2.6.20-14-generic
* nVidia Proprietary drivers 100.14.11

I'm having some very difficult to describe issues, so if you don't understand what I mean, please don't pass it off as me being incompetent.

I just bought an Acer X221W, and for the most part I am very pleased with it. I'm running it at 1650x1080. According to Ubuntu (I run Ubuntu Feisty x64), the refresh rate is 50Hz but the monitor itself says 60Hz (I have a feeling this may have to do with the problem).

However, problems arise any time the computer has to render anything, ranging from glxgears to CounterStrike 1.6 under CrossOver to my screensaver (Colorfire). This is where the hard to describe comes in. When using VGA, everything works as it should. However, when using DVI (which is half the reason I bought a new monitor), the screen "flickers" for lack of a better word. I'm new to LCDs, so I'm sorry if LCDs don't do this, but its almost like the monitor is trying to change resolution, even though the resolution isn't changing.

Here are a few quirks I've found about this on my own:
* At 800x600@75Hz (according to Ubuntu AND the monitor), there is no flickering/blinking.
* Using Ubuntu's out-of-the-box drivers didn't have this issue, but lacked performance-wise

Anything else, please ask and I shall give.

I'm attaching my xorg.conf in case that helps.

Thanks,
Steve

---

### Post by kb7qqq on 2007-10-27
How did you get Ubuntu to recognize you monitor. I have the same monitor and cannot use it above 1280 x 1024. Some don't display right and some make monitor to go blank and I have to restart the computer in failsafe to change resolution back.
I am using Ubuntu 7.10

Sam Roe

---

