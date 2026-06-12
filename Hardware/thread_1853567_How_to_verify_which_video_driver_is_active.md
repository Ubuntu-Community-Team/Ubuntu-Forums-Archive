---
title: "How to verify which video driver is active?"
date: 2011-10-02
forum: Hardware
---

### Post by markmaus on 2011-10-02
Hello,
I've just installed Ubuntu 11.04 (64-bit).  After installation I selected "NVIDIA accelerated graphics driver (version current) [Recommended] from the Additional Drivers dialog box and let it download and install.  Once I re-booted the Additional Drivers dialog box says that the driver is "activated but not currently in use"  I can go into nVidia X Server Settings and change the screen resolution, etc.  This leads me to believe that the nVidia driver is actually being used.  A search of /etc/X11/xorg.conf turns up nothing.  I guess that this file is no longer used?  I have a Gforce 9500 GT graphics card.  How do I determine which video driver is being used?  Any help is appreciated.  Thanks.

---

### Post by coffeecat on 2011-10-02
The "activated but not in use" message is a bug. It's almost certainly in use. To be sure, try this in a terminal:

```
sudo lshw -C video
```

It should show "driver=nvidia" if the proprietary driver is in use, or "driver=nouveau" if the open-source driver.

---

### Post by markmaus on 2011-10-02
Thanks coffeecat.  Terminal command returns the following:
description: VGA compatible controller
       product: G96 [GeForce 9500 GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fd000000-fdffffff memory:d0000000-dfffffff memor

driver=nvidia so I'm good to go.
Thanks again.

---

