---
title: "lost a cpu and now wont boot"
date: 2006-05-16
forum: Hardware &amp; Laptops
---

### Post by springer on 2006-05-16
for no apparent reason, one processor (on my dual athlon system) has stopped working. none of the other grub kernels are single amd, so i cant boot.
how can i get a generic amd kernel onto this system so i can boot it with just the one working cpu to get the data off before i start messing about with the hardware.
thanks....

---

### Post by hw-tph on 2006-05-17
Boot from the livecd (the livecd kernel is is uniprocessor, not SMP) and chroot into your installed system and do whatever you need to do.


Håkan

---

