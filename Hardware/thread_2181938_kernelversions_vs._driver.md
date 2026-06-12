---
title: "kernelversions vs. driver"
date: 2013-10-19
forum: Hardware
---

### Post by hvn2 on 2013-10-19
Hi,

I'm trying to build a hardware driver for Ubuntu12.04 ARM. For this I'm using a couple of tools coming with the hardware, but now I notice that 1 of the tools contains an especially prepared kernel that needs to be built for the driver to compile. This kernel is 2.6.37 and Ubuntu12.04 runs 3.2.0. Now I wonder if this kernel driver will ever work? From kernel 2.6.34 to 2.6.35 fundamental stuff changed, but the rest I don't know. Can someone tell please tell me?

Thanks.

---

### Post by hvn2 on 2013-10-21
OK, found the answer. Won't ever work unless a driver is built for the exact kernel.

---

