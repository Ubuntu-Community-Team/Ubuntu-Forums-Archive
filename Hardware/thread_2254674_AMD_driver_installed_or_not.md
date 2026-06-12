---
title: "AMD driver installed or not?"
date: 2014-11-29
forum: Hardware
---

### Post by hodja on 2014-11-29
Hi everyone,

I'm on Ubuntu 14.04, 
Video card is an AMD Radeon HD 5570
Monitor HP w2007v

I just updated display drivers to "AMD Catalyst™ 14.9 Proprietary Linux x86 Display Driver" from AMD website. Installation went flawless. 

When I do fglrxinfo;

```
~$ fglrxinfo
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 5570
OpenGL version string: 4.4.13084 Compatibility Profile Context 12.104
```

```
~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Redwood PRO [Radeon HD 5550/5570/5630/6510/6610/7570] [1002:68d9]

```

However on system settings details page I see: 
```
Graphics: VESA: 001  
```

Also the monitor is displayed as HP Generic (It used to be HP w2007v before the update) in Display settings. However AMD Catalyst Center shows correctly HP w2007v as the monitor.  Btw white areas on web pages are now pink after the update :)

In this case I believe the drivers are not properly installed. What do you think?

Any input will be appreciated. 

Thanks

---

### Post by ajgreeny on 2014-11-29
What does command **sudo lshw -c display** show you in the **configuration: driver=** line?

---

### Post by hodja on 2014-11-29
Here is the output of sudo lshw -c display

```
*-display                      description: VGA compatible controller
       product: Redwood PRO [Radeon HD 5550/5570/5630/6510/6610/7570]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
**       configuration: driver=fglrx_pci latency=0**
       resources: irq:46 memory:c0000000-cfffffff memory:d1000000-d101ffff ioport:9000(size=256) memory:d0000000-d001ffff



```

---

### Post by ajgreeny on 2014-11-29
[B]```
configuration: driver=fglrx_pci latency=0
```
[/B]Yes you're using the AMD driver, not the open source driver.

---

### Post by hodja on 2014-11-29
Thanks for the assistance ajgreeny. 

So this means new driver is not compatible with current setup as white areas on web pages are now pink after the update? Or is this a misconfiguration?

---

### Post by hodja on 2014-11-29
Update: Uninstalled AMD Catalyst&#8482; 14.9 and installed AMD proprietary drivers through Additional Drivers section of Ubuntu and pinkish areas went away.

---

