---
title: "Fsck mount for small device  : new design required"
date: 2007-08-12
forum: Hardware &amp; Laptops
---

### Post by kentsin on 2007-08-12
When porting linux to small device or notebooks, the original design of filesystem and fsck is not acceptable,

fsck is called to perform check durign mount is not acceptable: fast boot time is required

fsck consume a lots of power, which is valuable for small device or notebook.

when filesystem is full, which is quite often for a small device, the filesystem need to be fsck, this is bad

---

### Post by shad0w_walker on 2007-08-13
Whilst i agree that boot times are important on portable devices, the fsck boot time scan can be disabled i believe so that really doesn't need to be redesigned. As for the whole fsck needs to be run when the disk is full, i have never heard of that before and can't imagine why it would need to be run.

P.S. This would probably be better off in the development section of the forum. Fiesty is long released and this area is for hardware problems not suggestions and complaints about problems.

---

