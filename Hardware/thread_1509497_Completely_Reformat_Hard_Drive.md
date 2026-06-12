---
title: "Completely Reformat Hard Drive"
date: 2010-06-14
forum: Hardware
---

### Post by Infinitas on 2010-06-14
I've recently tried to do a fresh install of 10.04 on my home server. I've run into a problem on the boot drives of not being able to format them. I was running LVM on top of mdadm before, and am under the impression that some residual information is hanging around and giving me problems. I'm very frustrated and have considered just buying new drives, as this would make life easier. However, there should be a way to make my drives as clean as new ones. I would like to know a way of removing any information the drive has about partitions, LVM and mdadm so that the drives appear as brand new drives. I'm not interested in wiping all bits from the drives, just the LVM, mdadm and partition information. How do I do this?

-Infinitas

---

### Post by psusi on 2010-06-14
To get rid of md information run mdadm --zero-superblocks /dev/xxx.  To get rid of the partitions, fire up your favorite partition editor ( fdisk, parted, gparted ) and delete them.

---

