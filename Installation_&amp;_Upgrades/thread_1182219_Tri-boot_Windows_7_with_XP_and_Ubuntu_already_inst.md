---
title: "Tri-boot Windows 7 with XP and Ubuntu already installed"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by homestar92 on 2009-06-08
OK, so I know how to shrink a partition, that isn't an issue.

Basically, I've got Windows XP on SDA and Ubuntu 8.10 on SDB
I am planning on shrinking XP's partition and tri-booting, but what's the safest way without killing either of the other 2?

---

### Post by Mark Phelps on 2009-06-09
The "safest" way (IMHO), if you have the room, would be to shrink the Ubuntu partition, create a new NTFS partition in the unallocated space, and install Seven there.  You could also shrink the XP partition, but if you're using GParted or the Ubuntu partitioner, there is some risk of data corruption doing that.

Realize that installing Seven will overwrite GRUB if you have that loaded to the MBR.

Finally, understand that Seven will write its boot files to the XP partition, so if you remove XP later, you will not be able to boot into Seven.

---

### Post by dtechlogic on 2009-06-09
Hey how you got that working. I have Windows Vista 64 bit installed and then i installed Ubuntu 8.10 and then Windows 7 few days ago. I lot Grup and try to bring it back which is no luck. Well i said i will install ubuntu again. From installing now i am getting a

GRUB Loading Stage 1.5

GRUB Loading, Please wait...
ERROR 22

I left the Swap partition alone i did not reformated when I installed ubuntu gain.

---

