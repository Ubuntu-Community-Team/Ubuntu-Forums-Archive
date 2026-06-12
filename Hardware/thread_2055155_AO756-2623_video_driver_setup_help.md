---
title: "AO756-2623 video driver setup help"
date: 2012-09-08
forum: Hardware
---

### Post by viroscope on 2012-09-08
Hello I have an Acer One 756-2623 as per the specs the video card i have is Intel® HD Graphics but i need to setup the video driver and am not sure what to do.

```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

``````
 lsmod |grep video
uvcvideo               66101  0 
videodev               82668  1 uvcvideo
video                  18434  0 

``````
 hwinfo --gfxcard
09: PCI 02.0: 0300 VGA compatible controller (VGA)              
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_106
  Unique ID: _Znp.xjvsiuXfKl2
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: graphics card
  Model: "Intel VGA compatible controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x0106 
  SubVendor: pci 0x1025 "Acer Incorporated [ALI]"
  SubDevice: pci 0x0742 
  Revision: 0x09
  Memory Range: 0x90000000-0x903fffff (rw,non-prefetchable)
  Memory Range: 0x80000000-0x8fffffff (ro,non-prefetchable)
  I/O Ports: 0x2000-0x203f (rw)
  IRQ: 7 (no events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00008086d00000106sv00001025sd00000742bc03sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

Primary display adapter: #9

```If anyone can help point me in the correct direction I would appreciate it.

```
Linux bt 3.2.6 #1 SMP Fri Feb 17 10:40:05 EST 2012 i686 GNU/Linux

```Ubuntu Based Backtrack 5R3

---

