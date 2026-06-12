---
title: "Video card/updating?"
date: 2011-08-04
forum: Hardware
---

### Post by mickeymouseatlinux on 2011-08-04
Sorry for such a dumb question (+ Sorry if this is in the wrong place) but....

How do i check what video card I have, and how do I update it?

~ BTW, I'm awful with computer and technology, so if possible, keeping the jargon to a minimum would help! :(

---

### Post by papibe on 2011-08-04
Post the result of this command:
```
$ lshw -C display
```
Regards.

---

### Post by mickeymouseatlinux on 2011-08-04
Thanks for the quick reply!

> WARNING: you should run this program as super-user.
PCI (sysfs)  




  *-display:0             
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:fc000000-fc0fffff memory:d0000000-dfffffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:fc100000-fc1fffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.


---

### Post by papibe on 2011-08-04
There you go. You are using the integrated graphic card of your motherboard:
```
Intel Mobile GM965/GL960 Integrated Graphics
```
Regards.

---

### Post by realzippy on 2011-08-04
> **mickeymouseatlinux said:**
> ..., and how do I update it?


You can 't.
You use the "i915" driver,which is a kernel module.
Variations of this exists (fighting video issues eg).
Do you have graphics issues ?
Which Ubuntu version ?

---

