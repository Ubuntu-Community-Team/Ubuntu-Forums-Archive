---
title: "Video resolution problem"
date: 2016-08-31
forum: Hardware
---

### Post by panamahank on 2016-08-31
When I run Xubuntu 16.04 from DVD on my aging Intel Atom, I have full 1920x1080 resolution. After installation to hard drive, the best resolution I can get is 1024x768. 

Does anyone have any suggestions to fix this?

---

### Post by Bucky Ball on 2016-08-31
Welcome. Have you checked in 'Additional Drivers' to see if there's anything there for your video card? If nothing, could you supply the output of this from a terminal, please, inside code tags (see the link in my signature for how).

```
sudo lshw -C video
```

---

### Post by panamahank on 2016-09-15
I have looked for additional drivers. Here is the output for sudo lshw -C video
Thanks for helping.

*-display               
       description: VGA compatible controller
       product: Atom Processor D2xxx/N2xxx Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=gma500 latency=0
       resources: irq:29 memory:80100000-801fffff ioport:20d0(size=8)
henry@Panama1:~$

---

