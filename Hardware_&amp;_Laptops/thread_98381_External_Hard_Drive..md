---
title: "External Hard Drive."
date: 2005-12-03
forum: Hardware &amp; Laptops
---

### Post by Sunnz on 2005-12-03
My USB Sticks works fine but when I brought an external hard drive today, it simply doesn't work. It is USB2.0. Do I have to enable SCSI or something like that?

Thanks.

---

### Post by mlomker on 2005-12-03
Hmm.  Does your hardware support 2.0?  Probably doesn't matter because all of the hard disks that I know of will rever to 1.0 anyway.

Look at the output of **dmesg | tail** after plugging in the disk.  It should tell you if the kernel is recognizing that you've plugged something in.

---

### Post by Sunnz on 2005-12-04
It works now that I have the internal HDD's jumper setting to cable-select.

---

