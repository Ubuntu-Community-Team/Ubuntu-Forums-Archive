---
title: "Monitor not recognized correctly after install"
date: 2013-10-25
forum: Hardware
---

### Post by ForSquirel on 2013-10-25
I've searched till I can't search anymore.

currently running XUbuntu desktop 12.10 LTS on a 2 day old fresh install. Unfortunately anytime I've ever installed on the desktop I notice that a lot of my graphics get 'washed out' or blurry. Booting from a live USB the monitor recognizes correctly (ie settings> settings manager>display) as a Samsung 23" LCD and everything looks beautiful all around. 

However, after install to the desktop the display only recognizes the monitor as a CRT and blurry ensues. I've tried everything I can think about and searched today (as well as in the past before just giving up) with no solution found. 

I know it's probably just an easy fix but right now I just can't figure it out. Any help would be appreciated.

---

### Post by Bashing-om on 2013-10-25
ForSquirel; Hi !

For starters, show us what graphics card you have and if/what driver is in use:
Post back the outputs of terminal codes - between code tags- :
```

sudo lshw -C display
lspci | grep VGA
lspci -nnk | grep -iA3 vga

```

[INDENT][INDENT]where there are solutions there are no problems
[/INDENT][/INDENT]

---

### Post by ForSquirel on 2013-10-25
output from lshw
```

*-display               
       description: VGA compatible controller
       product: BeaverCreek [Radeon HD 6530D]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:44 memory:c0000000-cfffffff ioport:f000(size=256) memory:fef00000-fef3ffff

```

lspci | grep VGA
```

00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek [Radeon HD 6530D]

```

lspci -nnk | grep -iA3 vga
```

00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek [Radeon HD 6530D] [1002:964a]
    Subsystem: Lenovo Device [17aa:3625]
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

```


The difference between live and normal boot is shown in ```
xrandr -q
``` where it says in live boot that the device connected is VGA-0 and in normal boot is CRT1. Live boot looks perfect and all apps work like they should, not so much for normal boot. I've actually been dealing with this issue for a few years but usually just give up after a few days, get used to it, and never realize it's an issue until i reinstall/install the OS. Top is live, bottom is regular.

[IMG]http://imageshack.us/a/img593/8342/b4y1.png[/IMG][IMG]http://imageshack.us/a/img201/3199/n0ii.png[/IMG]

---

### Post by mörgæs on 2013-10-26
> **ForSquirel said:**
> 
currently running XUbuntu desktop 12.10 LTS 

12.10 is not LTS. Support is though april 2014.

---

### Post by ForSquirel on 2013-10-26
> **mörgæs said:**
> 12.10 is not LTS. Support is though april 2014.

Ok, and this helps fix my problem how?

---

