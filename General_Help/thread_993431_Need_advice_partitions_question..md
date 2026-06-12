---
title: "Need advice partitions question."
date: 2008-11-25
forum: General Help
---

### Post by TimboUK on 2008-11-25
Hello all!

Just a quickie (ISH) its in regards to partitions

I am currently dual booting XP and Ubuntu 8.10.

My hardrive has 3 partitions one for Ubuntu one for XP and one for just data.

I would like to reformat the two partitions (XP and data) and merge them into one (I have no need of XP)

My question is:  What software/command would I use to do this?

and would it "break" my GRUB that currently has the option to boot to XP?

Thanks in advance.

---

### Post by taurus on 2008-11-25
Is Ubuntu partition between XP and data?  Can you post the layout of your harddrive?

```
sudo fdisk -l
```
Otherwise, you can use gparted to merge those two partitions to one if they are right next to each other and both are primaries.

---

### Post by TimboUK on 2008-11-25
Thanks for helping!

Here you go:

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbe08d558

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         764     6136798+  12  Compaq diagnostics
/dev/sda2   *         765        4137    27093622+   7  HPFS/NTFS
/dev/sda3            5216        9729    36258705    c  W95 FAT32 (LBA)
/dev/sda4            4138        5215     8659035    5  Extended
/dev/sda5            4138        5162     8233281   83  Linux
/dev/sda6            5163        5215      425691   82  Linux swap / Solaris

Partition table entries are not in disk order

---

