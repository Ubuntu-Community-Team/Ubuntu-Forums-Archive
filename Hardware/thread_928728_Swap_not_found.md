---
title: "Swap not found"
date: 2008-09-24
forum: Hardware
---

### Post by LieToPurify3 on 2008-09-24
I have a laptop with one partition set to boot ubuntu, one to switch between other distros, and one for swap.  Last night I installed antiX on sda1.  It led me through the install process and I told it to just install on sda1.  Later on, it asked if I wanted to use sda6 as swap, but it would have to reformat it.  I wasn't sure if that would mess up my beloved ubuntu, so I said no, and figured I'd just mount it as swap later.  But now when I boot into ubuntu, my conky info says that there is no swap found.  I'm sure the partition is still there.  How can I mount it again?  It's still in the fstab set to be my swap disk, so I dont know if its a problem with the swap, or just a problem with conky.

---

### Post by uidb4056 on 2008-09-24
> **LieToPurify3 said:**
> I have a laptop with one partition set to boot ubuntu, one to switch between other distros, and one for swap.  Last night I installed antiX on sda1.  It led me through the install process and I told it to just install on sda1.  Later on, it asked if I wanted to use sda6 as swap, but it would have to reformat it.  I wasn't sure if that would mess up my beloved ubuntu, so I said no, and figured I'd just mount it as swap later.  But now when I boot into ubuntu, my conky info says that there is no swap found.  I'm sure the partition is still there.  How can I mount it again?  It's still in the fstab set to be my swap disk, so I dont know if its a problem with the swap, or just a problem with conky.

Check the /etc/fstab file for an entry of swap, if not here try to add it, also check that UUID matches with the output of blkid command for your swap partition, the UUID in fstab must match with the output of blkid.

---

