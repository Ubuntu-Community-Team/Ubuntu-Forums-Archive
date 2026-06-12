---
title: "Ubuntu 9.10 doesn't mount all my partitions"
date: 2009-12-16
forum: Hardware
---

### Post by rpz79 on 2009-12-16
Hello,

Every time when I boot Ububtu I get call that 2 partitions cannot be mounted and I have to press escape to enter recovery shell when I press escape it brings me to the login screen and 2 partitions are not mounted (picture added):

1. XP partition which is NTFS
2. Ubuntu Swap partition which is ex2

I can mount the XP partition manually after every log but this is not a solution.

THNX ALOT
:KS

---

### Post by ATG_Redneck on 2009-12-16
Try playing with the /etc/fstab file, add the row with the partition the same way the ones already mounted are presented there. The swap partition - im afraid you wont be able to create a mount point for it since its your linux swap partition.

---

