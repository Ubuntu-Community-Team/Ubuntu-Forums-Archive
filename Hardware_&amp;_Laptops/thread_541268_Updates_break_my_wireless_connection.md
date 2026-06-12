---
title: "Updates break my wireless connection"
date: 2007-09-02
forum: Hardware &amp; Laptops
---

### Post by _Dave_ on 2007-09-02
My wireless worked fine after a clean installation until I applied the updates.The available network interfaces list will only display my ethernet connection. lshw gives:

                description: Network controller
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ipw3945 latency=0
                resources: iomemory:fa7ff000-fa7fffff irq:16

Does this have something to do with the restricted driver manager? Is there a package I shouldn't be updating.

---

### Post by eggdeng on 2007-09-02
Kernel updates are always a double-edged sword, they are notorious for breaking your graphics and sometimes other stuff too. Only the brave install anything with the word linux in the package name unless there is a real need to do so.

---

### Post by _Dave_ on 2007-09-02
So I'm reinstalling now, any suggestions on the updates? Should I only avoid the kernel updates?

---

### Post by eggdeng on 2007-09-03
Just a rule of thumb: if in doubt, leave it out.

---

