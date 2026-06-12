---
title: "Back to monitor default settings"
date: 2016-05-17
forum: Hardware
---

### Post by eliyahu2 on 2016-05-17
The settings of my monitor are not to my liking, and I can't change them.   I think the settings are changed in the terminal, and I want to go back to the default settings.  How do I do that?

---

### Post by him610 on 2016-05-17
What is the default resolution?

How about running these commands in a terminal and posting the results, using code tags.
```
inxi -b
hwinfo --vbe
sudo lshw -c video
xrandr
```

---

### Post by eliyahu2 on 2016-05-18
> **him610 said:**
> What is the default resolution?

How about running these commands in a terminal and posting the results, using code tags.
```
inxi -b
hwinfo --vbe
sudo lshw -c video
xrandr
```

```
eliyahu@eliyahu-desktop:~$ inxi -b
System:    Host: eliyahu-desktop Kernel: 4.4.0-22-generic x86_64 (64 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Machine:   Mobo: Intel model: DH61HO v: AAG62445-102
           Bios: Intel v: HOH6110H.86A.0813.2012.0927.1708 date: 09/27/2012
CPU:       Dual core Intel Core i3-2120 (-HT-MCP-) speed/max: 1599/3300 MHz
Graphics:  Card: Intel 2nd Generation Core Processor Family Integrated Graphics Controller
           Display Server: X.Org 1.18.3 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1024x768@60.00hz
           GLX Renderer: Mesa DRI Intel Sandybridge Desktop
           GLX Version: 3.0 Mesa 11.2.0
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169
           Card-2: Edimax EW-7711UTn nLite Wireless Adapter [Ralink RT2870]
           driver: rt2800usb
Drives:    HDD Total Size: 500.1GB (2.1% used)
Info:      Processes: 211 Uptime: 5 min Memory: 975.6/3845.6MB
           Client: Shell (bash) inxi: 2.2.35 
eliyahu@eliyahu-desktop:~$ 


eliyahu@eliyahu-desktop:~$ hwinfo --vbe
01: None 00.0: 10105 BIOS                                       
  [Created at bios.186]
  Unique ID: rdCR.lZF+r4EgHp4
  Hardware Class: bios
  BIOS Keyboard LED Status:
    Scroll Lock: off
    Num Lock: off
    Caps Lock: off
  Config Status: cfg=new, avail=yes, need=no, active=unknown
eliyahu@eliyahu-desktop:~$ 


eliyahu@eliyahu-desktop:~$ sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:25 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)
eliyahu@eliyahu-desktop:~$ 


eliyahu@eliyahu-desktop:~$ xrandr
Screen 0: minimum 8 x 8, current 1024 x 768, maximum 32767 x 32767
VGA1 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00* 
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
eliyahu@eliyahu-desktop:~$ 

```
I don't know what the original settings were,  But I use an Innova monitor type NT 19132M.  Before I couldn't get the full screen to be used, on the sides I had black parts of about 2 inches wide on both sides.  Now the whole screen is being used, but the picture is distorted, it is too wide.  So I rather go back to the first situation.

---

### Post by him610 on 2016-05-18
> I use an Innova monitor type NT 19132M

I searched the internet for information on your monitor, but nothing showed up. We need to know which display resolutions your monitor is capable of. I see that you have your monitor connected through your VGA port. The results of *hwinfo --vbe* were non-informative. Let's try it a different way. Please post the results of ```
sudo hwinfo --vbe
```
The results, in a long listing, should show, at the bottom of the list, the resolution capabilities of both the graphics framebuffer and your monitor.

---

### Post by eliyahu2 on 2016-05-19
> **him610 said:**
> I searched the internet for information on your monitor, but nothing showed up. We need to know which display resolutions your monitor is capable of. I see that you have your monitor connected through your VGA port. The results of *hwinfo --vbe* were non-informative. Let's try it a different way. Please post the results of ```
sudo hwinfo --vbe
```
The results, in a long listing, should show, at the bottom of the list, the resolution capabilities of both the graphics framebuffer and your monitor.

```
02: None 00.0: 11001 VESA Framebuffer
  [Created at bios.459]
  Unique ID: rdCR.QgFYtsmQZBC
  Hardware Class: framebuffer
  Model: "Intel(R) Sandybridge/Ivybridge Graphics Controller"
  Vendor: "Intel Corporation"
  Device: "Intel(R) Sandybridge/Ivybridge Graphics Controller"
  SubVendor: "Intel(R) Sandybridge/Ivybridge Graphics Chipset Accelerated VGA BIOS"
  SubDevice: 
  Revision: "Hardware Version 0.0"
  Memory Size: 63 MB + 960 kB
  Memory Range: 0xe0000000-0xe3feffff (rw)
  Mode 0x033c: 1920x1440 (+1920), 8 bits
  Mode 0x034d: 1920x1440 (+3840), 16 bits
  Mode 0x035c: 1920x1440 (+7680), 24 bits
  Mode 0x033a: 1600x1200 (+1600), 8 bits
  Mode 0x034b: 1600x1200 (+3200), 16 bits
  Mode 0x035a: 1600x1200 (+6400), 24 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x037d: 1024x768 (+1024), 8 bits
  Mode 0x037e: 1024x768 (+2048), 16 bits
  Mode 0x037f: 1024x768 (+4096), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```

---

