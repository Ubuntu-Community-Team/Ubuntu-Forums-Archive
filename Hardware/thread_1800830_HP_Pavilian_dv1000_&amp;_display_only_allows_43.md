---
title: "HP Pavilian dv1000 &amp; display only allows 4:3"
date: 2011-07-09
forum: Hardware
---

### Post by boosted on 2011-07-09
Installed 11.04 on my grandfathers HP Pavilian dv1000 and everything seems fine except the display is stuck in 1024x768 4:3.  So now there is a black bar on each side of the screen.  This should be 1280x768 16:9 (I think).  Does anyone know how I can resolve this?  

Thanks!
  

```
xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
LVDS1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 305mm x 183mm
   1280x768       60.0 +
   1024x768       60.0*
   800x600        60.3     56.2 
   640x480        59.9 
VGA1 disconnected (normal left inverted right x axis y axis)
TV1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   848x480        30.0 +
   640x480        30.0 +
   1024x768       30.0*
   800x600        30.0 


lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
05:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

```

Also, I just ran this:

```

/usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945GM GEM 20100330 DEVELOPMENT x86/MMX/SSE2
OpenGL version string:  1.4 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes

```

---

### Post by boosted on 2011-07-10
Bump...

---

