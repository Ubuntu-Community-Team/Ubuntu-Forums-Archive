---
title: "VSYNC not working when window maximized / fullscreen?"
date: 2014-08-27
forum: Hardware
---

### Post by ic3man5 on 2014-08-27
Have a strange issue and not sure if this is the right place to post or any idea on where to start to understand this. Its an HD4600 and nvidia 870M hybrid using prime-selector in intel mode.

I have screen tearing but only seems to happen on maximized and fullscreen openGL.

For some reason I get more than 60FPS in glx as soon as I make the window maximized:


```
:~ > glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
305 frames in 5.0 seconds = 60.993 FPS
301 frames in 5.0 seconds = 60.003 FPS
301 frames in 5.0 seconds = 60.008 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.007 FPS
299 frames in 5.0 seconds = 59.796 FPS
301 frames in 5.0 seconds = 60.011 FPS
301 frames in 5.0 seconds = 60.003 FPS
318 frames in 5.0 seconds = 63.338 FPS
381 frames in 5.0 seconds = 76.015 FPS
401 frames in 5.0 seconds = 79.889 FPS
356 frames in 5.0 seconds = 71.011 FPS
302 frames in 5.0 seconds = 60.400 FPS
301 frames in 5.0 seconds = 60.003 FPS
301 frames in 5.0 seconds = 60.003 FPS
301 frames in 5.0 seconds = 60.003 FPS
301 frames in 5.0 seconds = 60.003 FPS


```


```
 lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.1 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #2 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GK104M [GeForce GTX 870M] (rev ff)
03:00.0 PCI bridge: Texas Instruments XIO2213A/B/XIO2221 PCI Express to PCI Bridge [Cheetah Express] (rev 01)
04:00.0 FireWire (IEEE 1394): Texas Instruments XIO2213A/B/XIO2221 IEEE-1394b OHCI Controller [Cheetah Express] (rev 01)
05:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
05:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0a)
06:00.0 Network controller: Intel Corporation Wireless 7260 (rev 73)
```

---

