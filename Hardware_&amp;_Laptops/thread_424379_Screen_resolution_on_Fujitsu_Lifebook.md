---
title: "Screen resolution on Fujitsu Lifebook"
date: 2007-04-26
forum: Hardware &amp; Laptops
---

### Post by dmsynck on 2007-04-26
Hi all,

I have a fairly new Fujitsu Lifebook laptop (Model C1410) that I have installed Ubuntu 7.04 on. Everything is good except the screen resolution. I know from the laptop documentation that it is capable of 1280x800 max, but the best that I can get it to do is 1024x768. I have run sudo dpkg-reconfigure xserver-xorg a couple of times and set it up for "1280x800", "1024x768", and "800x600". However, when I get to the screen for "best" resolution, "1280x800" is not listed, so I have to end up going with a "safe" setting of "1024x768". Here is the relevant section from the hardware listing so you know what type of graphics hardware I am dealing with..



```


lshw

 *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 03
             size: 256MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: latency=0
             resources: iomemory:f0300000-f037ffff ioport:1800-1807 iomemory:e0000000-efffffff iomemory:f0400000-f043ffff irq:11
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: 03
             size: 512KB
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: iomemory:f0380000-f03fffff



```

Thanks in advance.

---

### Post by Matchless on 2007-04-29
Install 915resolution and reboot and you should be OK

---

### Post by dmsynck on 2007-04-30
Thanks for the advice. I installed the 915resolution package and configured /etc/defaults/915resolution and now I can get 1280x800. Thanks once again.

---

