---
title: "Shutdown problem, related to HDMI output?"
date: 2007-08-13
forum: Hardware &amp; Laptops
---

### Post by hgu on 2007-08-13
I'm putting together a MythTV box with combined front-end/back-end. But I have problems with it sometimes not power off when it shall shutdown. I'm looking for advice on how to debug the problem or suggestions for fixes. What I have tried so far is changing things in BIOS like switching PCI clock auto on and turning off splash in boot, both seems to have helped to limit the problem. The splash thing I think helped with powering off more often when the TV was off (before it never succeeded with TV off). The BIOS switch for PCI clock made it sometimes to power off, before it never managed it (it also helped with removing the DVB-T cards).

I use ACPI, and as long as the shutdown is successful, it will restart at the specified time, I used the guide [https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake) Can't use the power off kernel since the restart time does not work then.

Nothing strange in the logs can be seen. When it does not power off, the screen is black but everything seems to be on even the harddisk, and does not react on input (more than the reset button).

EDIT: Solved it! It was the newest driver+firmware for the NOVA-T 500 PCI tthat was the problem. By unloading the modules before shutting down the computer powers off.

The HW I'm using is:
Motherboard:
ABIT IL-90MV 945GT Mobile S478 HDMI mATX
CPU:
Intel Core 2 Duo Mobile T5600 1.83GHz 2M
Power supply:
Seasonic S12 430W 120mm
Memory:
Corsair VS 2048MB Kit (2x1024) DDR2 667M
DVB-T card:
Hauppauge WinTV Nova-T 500 DVB-T & Twinhan VisionPlus DVB-T
DVD:
LG DVD±RW 16x USB 2.0 Extern
Hard disk:
Seagate Barracuda 7200.10 500GB SATA II
TV:
Samsung LE26S86BD, connected via the HDMI/DVI port.

And SW:
Ubuntu 7.04 Feisty Fawn
MythTV 0.20 (ubuntu package)
915resolution (for fixing the 1360x768 screen resolution)
Latest v4l-dvb drivers from the linux tv repository

---

