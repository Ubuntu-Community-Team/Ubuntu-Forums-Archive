---
title: "Bumblebee and GeForce GT 555M"
date: 2013-11-22
forum: Hardware
---

### Post by kyon.0308 on 2013-11-22
[COLOR=#000000][FONT=Arial]I'm trying to use Point Cloud Library with Ubuntu 12.04. However when I execute point cloud visualization program, I get the following error:
[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Arial]Xlib: extension "GLX" missing on display ":0".[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Arial]These are my system information:

[/FONT][/COLOR]```

$ glxinfo
name of display: :0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't find RGB GLX visual or fbconfig


Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".


$ sudo lshw -C display
  *-display
       description: VGA compatible controller
       product: GF106M [GeForce GT 555M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f2000000-f3ffffff memory:d0000000-dfffffff memory:e0000000-e3ffffff ioport:d000(size=128) memory:f4000000-f407ffff
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

       resources: irq:49 memory:f4400000-f47fffff memory:c0000000-cfffffff ioport:e000(size=64)

```[COLOR=#000000][FONT=Arial]

[/FONT][/COLOR]Because my laptop is with Nvidia GT 555M graphics card and optimus, I tried to install Bumblebee. But when I execute ```
apt-get install bumblebee
``` then my PC stops and turn into black screen. How can I solve this?

---

