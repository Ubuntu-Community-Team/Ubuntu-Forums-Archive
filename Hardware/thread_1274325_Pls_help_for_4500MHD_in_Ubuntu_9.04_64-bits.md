---
title: "Pls help for 4500MHD in Ubuntu 9.04 64-bits"
date: 2009-09-24
forum: Hardware
---

### Post by joseantmm on 2009-09-24
Hello, 

I have a fairly new install of Ubuntu 9.04 64-bits, kernel 2.6.28-15, on a 15" ThinkPad T500 (2089-2RG) with Intel 4500MHD. Compiz works just fine but Google Earth flickers until unusable. Can I do anything to improve my laptop's graphics performance without any shortcomings in stability? Thanks for your help. I copy the output of a couple of commands:


$ glxinfo | grep direct
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)


$ sudo lshw -C display
  *-display:0 UNCLAIMED
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0


$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc


And from xorg.conf:
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

