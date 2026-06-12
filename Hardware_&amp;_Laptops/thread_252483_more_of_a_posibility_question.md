---
title: "more of a posibility question"
date: 2006-09-06
forum: Hardware &amp; Laptops
---

### Post by Erg on 2006-09-06
I am bugeting to build a new computer.  What is the maximum ammount of ram that will be supported by sarge or better on a athalon x2 64?  I am looking to set up a computer in the range of 4 to 8 gigs of ram.

Is there a limit to the maximum size of hard drive I can get away with eg 500gb?  If so what is it?

are SATA raids compatable with LVM? 

I have found little data on this and what I did get was conflicting (one site says yes, the other says no).

Thank you for your time
Erg

---

### Post by hw-tph on 2006-09-08
I don't know about how much RAM an AMD X2 can allocate and use. That's really a hardware question and not a Linux one. A stock Linux kernel will happily let you use 64GB RAM if you have it - and if the kernel is configured to allow it: There are two levels of high memory support in vanilla (kernel.org mainstream sources), 4GB and 64GB. I believe the Ubuntu kernel ships with the 4GB option set. If this is the case you will want to recompile the kernel with the 64GB option instead.

No, there are no hard limits for disk size. Most Linux file systems will allow for very large partitions. ext2fs, the old standard file system without journaling, has a hard partition (file system) size limit of 16TB if you use 4KB blocks. Other filesystems, like ext3fs and reiserfs, allow for larger partitions.

SATA and LVM: As long as your disk controller is supported by the kernel, LVM will be able to use the disks connected to it. LVM is not really low level - hardware support is provided by the kernel, not the logical volume manager.


Håkan

---

### Post by Erg on 2006-09-15
thank you very much.  That clears up things dramaticly.

---

