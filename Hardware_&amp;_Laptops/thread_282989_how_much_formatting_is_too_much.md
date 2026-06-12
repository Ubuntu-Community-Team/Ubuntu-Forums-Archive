---
title: "how much formatting is too much?"
date: 2006-10-23
forum: Hardware &amp; Laptops
---

### Post by Denn1s on 2006-10-23
i have a simple question, how do you know when you have formatted your hard drive too much? Is it risky to format a hard drive frecuently?

---

### Post by Courtney90 on 2006-10-23
well.. i've had to reformat my laptop about 2 times in a week. i really do not think there is harm to your computer if you do. Can i ask your reasons for having to reformat frequently?

---

### Post by bsussman on 2006-10-23
While it is probably not the most harmful wearing thing to do, formatting often is usually not useful, unless you have some security-related reason or you need to keep changing the format (like from ext3 to reiser to vfat, etc.).  I never reformat unless I suspect a problem, have run diagnostics and cannot find anything.  Then the disk is reformatted and used for non-ctitical purposes, if at all.

Formatting doesnt check for bad blocks, which is much more important.  ubuntu defaults to checking every (20? 30?) so many mounts (each reboot would count for 1.  This is usually often enough, though I set critical disks to a lower number or so many days, whichever comes firse.  the program tune2fs does this for ext2 and ext3 volumes,  which is mostly what I use.  be very very careful when using this or any other low-level program - make sure you understand the purpose and consequences of its actions.

---

### Post by az on 2006-10-23
> **Denn1s said:**
> i have a simple question, how do you know when you have formatted your hard drive too much? Is it risky to format a hard drive frecuently?

No.  Formatting is just writing and reading to the disk.  It is normal use.

Go crazy.

---

### Post by Denn1s on 2006-10-23
thanks for the quick answers, i have been doing some formating because i was changing my OS, and i want to clean install edgy so im planning to format again.

---

