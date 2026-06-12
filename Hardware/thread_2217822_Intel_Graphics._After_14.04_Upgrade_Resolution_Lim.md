---
title: "Intel Graphics. After 14.04 Upgrade Resolution Limited"
date: 2014-04-18
forum: Hardware
---

### Post by t-7 on 2014-04-18
I have a 30" Dell monitor connected through DVI to a System76 with Intel graphics (details below). After upgrading to 14.04 my resolution is now limited to 1920x1200, before I was running at 2560x1440 (or 2560x1600, I don't remeber).

I read that 14.04 has the latest driver and the Intel driver installer says trusty isn't supported. I assume it is a driver/kernel issue, is that safe to say?

```
 *-display
       description: VGA compatible controller
       product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)

```

---

### Post by Achlervor on 2014-04-21
Same problem here.

---

### Post by pxntium on 2014-04-22
Same problem here.
I have an Intel HD card and with 14.04 my resolution is limited to 1920x1080. My monitor support up to 2560x1080, and works fine in 13.10.

Regards.

---

