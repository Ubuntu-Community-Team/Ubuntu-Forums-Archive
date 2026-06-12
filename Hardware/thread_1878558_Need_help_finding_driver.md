---
title: "Need help finding driver"
date: 2011-11-10
forum: Hardware
---

### Post by vacevedo on 2011-11-10
I am new to Ubuntu, I have just installed ver.11.10 on a Dell Latitude D500 and it does not have the video driver for it, does anybody knows where I could get an { Intel 82852/855 GM graphics driver}?

---

### Post by papibe on 2011-11-10
Hi vacevedo. Welcome to the forums.

Do you have any video problem? As far as I know there is a open source driver (module) for Intel integrated graphics. You should be using it automatically.

But to make sure, could you post the results of these 2 commands?
```
lspci -nn | grep -i vga
```
and
```
sudo lshw -C display
```
Regards.

---

### Post by vacevedo on 2011-11-11
display:0
description: vga compatible controller
Product: 82852/855 Gm Integrated Graphics Device.
Vendor: Intel Corporation
Physical ID: 2
bus info: PCI@0000:00:02.0
version: 02
width: 32 bits
clock: 33 mhz
capabilities: pm vga-controller bus_master cap_list rom
configuration: driver=i915 latency=0
resources: irq 11 memory: f0000000-f7ffffff memory: faf80000-fafffffff ioport c000 (size=8
display:1 UNCLAIMED
description:display controller
product: 82852/855 gm integrated Integrated graphics device
vendor: Intel Corporation
physical id: 2.1
bus info: PCI@0000:00:02.1
version:02
width: 32 bits
clock: 33 mhz
capabilities: pm bus_master cap_list
configuration: latency=0
resources: memory: e8000000-efffffff memory:faf00000-faf7ffff

Does this means that this graphics card supports 2 monitors?
I am a little confused is Ubuntu using the display:0 and there is a second driver for the same card?
Can you tell me what I am suppost to do.

Thank's for your help.

---

### Post by papibe on 2011-11-11
> **vacevedo said:**
> 
...
configuration: **driver=i915** latency=0
...

There it is. You are already using the Intel driver (i915). As for the second monitor, it should use the same driver (because it is the same card). My guess is since it is not connected, it is not being used (loaded).

Use the applications 'Monitors' to set the other display.

Regards.

---

### Post by vacevedo on 2011-11-12
But the boot process stops once it starts detecting the video card, it freezes at that point, the only way I could go in is in safe mode by pressing on the shift key before it even starts, but is annoying to go thru that all the time.

Thanks 
for taking the time to help me.

---

### Post by MoreOrLess on 2011-11-12
You should use the vesa driver as default, because apparently you have one of those problematic i855's that freezes with the intel driver: [https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

---

