---
title: "Dual screen not working correctly Since Ubuntu 9.04"
date: 2011-11-28
forum: Hardware
---

### Post by CWildUK on 2011-11-28
Hi :D
 
Hope someone can help. I'm relatively inexperience in Linux, and this forum but have been using Linux on and off for quite a while.  I have a slight issue with using dual display.
 
I'm using a Laptop (Lenovo T61) with 3gb and running Windows 7 alongside Ubuntu 11.10 64bit on Wubi, though i've also tried 32 bit version native and WUBI too... This all worked fine on 9.04, the issue has occured on every version since then.
 
Whenever I connect my second monitor (either in the docking station or directly) it says that it's an unknown display and only gives me 2 resolution options for the monitor 1024x764 and 800x600. The laptop display remains able to give all its resolutions.  Unlike many of the issues with dual display i've found listed, both the displays are uncorrupted and appear to be rendered correctly.
 
The laptop graphics card is an intel M965 (typical in many laptops), however the linux driver being used is an i915 module and i'm not sure if this is correct.
 
I have no idea how to change this, or even if it's possible.
 
Here is the output to lshw, just in case it may help - thanks in advance
 
Craig.
 
 
 
*-display:0
description: VGA compatible controller
product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
vendor: Intel Corporation
physical id: 2
bus info: [pci@0000:00:02.0]("wlmailhtml:{DC82CA00-62E5-4BBB-B42F-0115285DC61B}mid://00000176/!x-usc:mailto:pci@0000:00:02.0")
version: 0c
width: 64 bits
clock: 33MHz
capabilities: msi pm vga_controller bus_master cap_list rom
configuration: driver=i915 latency=0
resources: irq:47 memory:f8100000-f81fffff 
memory:e0000000-efffffff ioport:1800(size=8)
*-display:1 UNCLAIMED
description: Display controller
product: Mobile GM965/GL960 Integrated Graphics Controller 
(secondary)
vendor: Intel Corporation
physical id: 2.1
bus info: [pci@0000:00:02.1]("wlmailhtml:{DC82CA00-62E5-4BBB-B42F-0115285DC61B}mid://00000176/!x-usc:mailto:pci@0000:00:02.1")
version: 0c
width: 64 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: latency=0
resources: memory:f8200000-f82fffff

---

