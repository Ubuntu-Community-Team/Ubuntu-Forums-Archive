---
title: "I suspect that my disks are dying !!!"
date: 2007-01-17
forum: Hardware &amp; Laptops
---

### Post by afftrash on 2007-01-17
Hi all, 
Is there any application under ubuntu that can run hardware test on my IDE drives ?
I suspect that one of them is dying, I just wanna know who that is , and if I'm correct.
Thanks.

---

### Post by frodon on 2007-01-17
It's the purpose of the fsck command, type "man fsck" for details. To get the name of your partition you can run a "sudo fdisk -l" which will list all your partitions.
The fsck command must be used only on umounted partitions, so you need to unmount the partition you want to check before using the fsck command on it.

---

### Post by ianmac on 2007-01-18
> **frodon said:**
> It's the purpose of the fsck command, type "man fsck" for details. To get the name of your partition you can run a "sudo fdisk -l" which will list all your partitions.
The fsck command must be used only on umounted partitions, so you need to unmount the partition you want to check before using the fsck command on it.

Is this correct?  I was under the impression that fsck was for checking partitions and file systems, not necessarily the physical disk...

Ian

---

### Post by frodon on 2007-01-19
If you want to test the physical disk no other way than to go on the site of the disk maker then download a bootable CD made by them for this purpose. In general most of them provide this kind of CD.

---

### Post by Titus A Duxass on 2007-01-19
Try googling for the Ultimate Boot CD, that has many HDD tools and checkers and it's well worth having a copy to hand.

---

