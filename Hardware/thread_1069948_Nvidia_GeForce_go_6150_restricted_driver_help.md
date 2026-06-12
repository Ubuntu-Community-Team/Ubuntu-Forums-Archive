---
title: "Nvidia GeForce go 6150 restricted driver help"
date: 2009-02-14
forum: Hardware
---

### Post by GHOST_TUX on 2009-02-14
hi i am using ubuntu 8.10 on wubi and i was able to acctivate my wireless card's restricted driver but not my video card's i have a nvidia GeForce 6150 video card and i went to nvidia's site to download the driver for linux and when i tried to install it using terminal it said "sh: Can't open NVIDIA-Linux-x86-180.29-pkg1.run" and here is the link to nvidia's site [http://www.nvidia.com/object/linux_display_ia32_180.29.html](http://www.nvidia.com/object/linux_display_ia32_180.29.html) can someone tell me how to install the driver and use it because i want to have the full 3d capabilities of this card and use desktop effects

---

### Post by cariboo on 2009-02-14
I'm not sure that driver will work with 8.10, I would suggest going to System-->Aministration--Synaptic Package Manager and installing **nvidia-glx-177**, then activating it in System-->Administration-->Hardware Drivers.

Jim

---

