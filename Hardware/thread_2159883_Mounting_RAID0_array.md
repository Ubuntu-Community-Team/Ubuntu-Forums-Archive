---
title: "Mounting RAID0 array"
date: 2013-07-04
forum: Hardware
---

### Post by streamholder on 2013-07-04
Hello everyone!
Recently, my mobo (ASUS Sabertooth P67) broke down.
I had an hardware RAID0 array consisting of 2x 2TB volumes, making a total of 4TB of space, which was than divided in 2 virtual disks.
The question is: can I recreate the RAID0 array via software with md or something else and then mount the two virtual disks?

Thank you in advance!

---

### Post by nemilar on 2013-07-05
My understanding of this is no, you cannot.  I don't know how the motherboard's RAID works, so I could be wrong; but generally, a compatible controller is required in order to read the metadata associated with the RAID array, in order to recreate it.  (For example, if you use a Dell PERC card to RAID a disk, you need a Dell PERC to be able to "see" that RAID, because only the PERC controller will look for the PERC metadata.)

---

