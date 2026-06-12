---
title: "Resolution Woas"
date: 2009-11-25
forum: Hardware
---

### Post by Chaos Punk on 2009-11-25
I have a Dell monitor and Ubuntu Studio installed on my desktop. I can't seem to get the resolution higher, so everything is extremely huge on screen. I tried detecting the monitor in Preferences-->Display, but it says the max resolution is 800 by 600. I can't even see the bottom of some windows to press any buttons. The first time I installed Ubuntu (Jaunty), it found the right resolution just fine, right after installation. It's the same monitor and PC as before, so why isn't the resolution right now? Do I need to install a driver?

---

### Post by Chaos Punk on 2009-11-26
Here's more information and a small bump 

*-display               
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:f0000000-f7ffffff(prefetchable) memory:ffa80000-ffafffff

I'm not sure exactly what my max resolution is, but I'm sure it's much higher than it is now. When I had Jaunty and Windows installed, the resolution was set much higher.

NVRMND: ran this command and it solved it:
xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr --addmode VGA1 1024x768_60.00
xrandr --output VGA1 --mode 1024x768_60.00

---

