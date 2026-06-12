---
title: "display resolution limit on dual monitor thinkpad e555"
date: 2015-11-29
forum: Hardware
---

### Post by Kilarin on 2015-11-29
I just got a new Lenovo ThinkPad Edge E555 20DH002QUS AMD Dual Core A6-7000, 4GB RAM
Graphics adapter: AMD Radeon R5 (Kaveri), Core: 514 MHz, 14.201.1003.1001

One of the reasons I got a ThinkPad E55 was that it was listed as linux ready.

I have it set up to dual boot between windows 7 and Xubuntu 14.04 (32bit).  I have it set up for dual monitors through the extra vga port.  On either w7 or Xubuntu the maximum resolution of the laptop monitor is 1366x768, as I expected.

BUT, while in windows 7 I can set the secondary monitor to 1280x1024, **in Xubuntu, the maximum resolution on the second monitor is 1024x768, which is quite unacceptable to my old eyes.**  

Do I need to download a proprietary driver or something?  any help would be greatly appreciated.

---

### Post by Kilarin on 2015-11-29
Problem Solved!

App Button > All Settings > Additional Drivers
It showed:
* Using X.Org X server -- AMD/ATI display driver wrapper from xserver-xorg-video-ati(open source, tested)
I switched to:
* Using Video driver for the AMD graphics accelerators from fglrx-updates (proprietary)

And now I can not only go to 1280x1024, but even up to 1400x1050 (which my monitor can handle) or 1600x1200 (which my monitor can not)

---

