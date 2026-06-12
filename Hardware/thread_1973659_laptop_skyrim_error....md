---
title: "laptop skyrim error...?"
date: 2012-05-05
forum: Hardware
---

### Post by aveplatter on 2012-05-05
the graphics are horrible[IMG]http://i.imgur.com/Rhwvu.png[/IMG]I'm sorry im a newbie i don't know how to go about fixing this. i'm running steam off of wine 1.4. I have a sandybridge i5 intel processor. oh and ubuntu 11.10

---

### Post by Axxon95 on 2012-05-05
You should post your iGPU, or your GPU(if you're on a high-priced laptop), that will be helpful.

---

### Post by aveplatter on 2012-05-06
how do find that info?

edit:
is this it...?
> 
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
       resources: irq:41 memory:e8400000-e87fffff memory:d0000000-dfffffff ioport:1800(size=64)
avery@avery-Rev-1



---

### Post by Axxon95 on 2012-05-06
"sudo apt-get install mesa-utils" then "sudo glxinfo | grep render". To check if installed correctly.

Intel HD Graphics, HD Graphics 2000, HD Graphics 3000? [ Example: Should look similar to this, due to both being Intel, source my Intel Atom Netbook. ] [IMG]http://img29.imageshack.us/img29/7077/gpul.png[/IMG] 

I think(not totally sure) some of the HD graphics drivers aren't That good yet in Ubuntu

Report back with what you get.

---

### Post by aveplatter on 2012-05-07
"direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile x86/MMX/SSE2
    GL_NV_conditional_render, GL_ARB_ES2_compatibility,"

---

