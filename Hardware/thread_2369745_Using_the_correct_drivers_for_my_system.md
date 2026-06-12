---
title: "Using the correct drivers for my system"
date: 2017-08-26
forum: Hardware
---

### Post by RobGoss on 2017-08-26
Hello everyone, I have been wondering if I'm using the correct video drivers for my system, the reason I ask this is because I've noticed when I use my video USB video cam it kind of lags a bit. Here's the video drivers info I pulled form my system


```
@###-Inspiron-3646:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display (rev 0e)
robert@robert-Inspiron-3646:~$ sudo lshw -C video


[sudo] password for ###: 
  *-display               
       description: VGA compatible controller
       product: Atom Processor Z36xxx/Z37xxx Series Graphics & Display
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:90 memory:90000000-903fffff memory:80000000-8fffffff ioport:2050(size=8) memory:c0000-dffff

 
```

Right now I'm using the proprietary drivers provided by Ubuntu

I wanted to see if maybe I can get better videos results. Thanks so much guys

---

### Post by gsahli on 2017-08-26
Read this:
[https://01.org/linuxgraphics](https://01.org/linuxgraphics)

---

