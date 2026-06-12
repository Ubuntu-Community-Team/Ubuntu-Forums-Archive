---
title: "USB Troubleshooting Advice - IBM X30 laptop"
date: 2005-09-19
forum: Hardware &amp; Laptops
---

### Post by tardi on 2005-09-19
Hi,

I reinstalled Ubuntu 5.04 from CD on my IBM X30 and now my USB ports are not working. Typically I use an optical mouse and a thumbdrive. My USB ports are 1.1 and my devices are 2.0 (don't think that matters as everything worked before). After my first install about 3 weeks ago I didn't have any issues. Both installations, I'm pretty sure, went exactly the same (except for disk carving).

Any (easy to understand) links or methods I could try to solve this issue with would be greatly appreciated. Technically I'm not too bad once I'm on the right path. Thanks.

Damian

---

### Post by mlomker on 2005-09-19
The USB drivers are uhci and ohci (depending on the chipset in your machine) for 1.x and ehci for 2.0.  You could start by seeing if they are loading and what is in the kernel log from when they load.

It looks like the 1.x drivers are built into the kernel but the 2.0 driver is loaded as a module (and can, therefore, be listed by **lsmod**).

```

lsmod | grep ehci
dmesg | grep uhci
dmesg | grep ohci
dmesg | grep ehci

```

The **lsusb** command lists what devices your machine can see.

---

### Post by tardi on 2005-09-20
Hi,

This morning everything is working. The USB ports are fine?! Mouse is working etc. Also my built-in wireless card is responding. Can't make heads or tails or that. 

Thanks for the starting point. I've written that down for any future installs. Cheers.

Damian

---

