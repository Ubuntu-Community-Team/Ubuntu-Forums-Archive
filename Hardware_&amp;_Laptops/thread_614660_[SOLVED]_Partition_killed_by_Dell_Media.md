---
title: "[SOLVED] Partition killed by Dell Media"
date: 2007-11-16
forum: Hardware &amp; Laptops
---

### Post by muadnu on 2007-11-16
I made the huge mistake of pressing the Dell Media button (instead of the power buttton) in my Vostro 1400, and lost my home partition... I had pressed in before, the difference now seems to be that I had taken my /home to a different partition. So I lost now all my files and configuration.

I guess they are still there. The problem is with the partition table, running fsck gives me an error code 8 and says something like "could this be a zero length partition?" I cannot mount it obviously.

I really hope my data is still there, and I don't want to mess with it by doing something wrong, so I could really use some help from an expert...

---

### Post by muadnu on 2007-11-16
Ok, I think the problem is different... My home parition doesn't even show with fdisk.

```

dani@nemo:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       14267       14594     2620416    c  W95 FAT32 (LBA)
/dev/sda2            7650       14593    55777680    5  Extended
/dev/sda5            7650       14083    51681073+  83  Linux
/dev/sda6           14084       14593     4096543+  82  Linux swap / Solaris

Partition table entries are not in disk order

```
sda1 has the Dell Media partition which I haven't been able to remove. I've never changed it, but it seems to be overlapping now my other partitions. I'm not even sure if it's supposed to be bootable, nor if I should add the boot flag to any other partition. sda2 is an extended partition with sda5 (mount point /) and sda6 (swap). The partition that should hold /home just doesn't appear. (My HD has 120 GB and if I remember right, I left the /home partition at the end).

---

### Post by muadnu on 2007-11-16
Solved! Hitting the same button again somehow fixed it...

---

