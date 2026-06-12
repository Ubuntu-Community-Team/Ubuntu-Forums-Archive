---
title: "HDD Raid metadata?"
date: 2010-02-01
forum: Hardware
---

### Post by smc18 on 2010-02-01
Hey everyone,

I have a general question.  A buddy of mine told me to look at the good HDD he pulled out of a a failed Jmicron Motherboard Raid setup.  The HDD works fine but when you try to rebuild the array, that leftover good HDD is not able to be used in any other motherboard RAID.

The HDD is good, you just can't use it in another motherboard RAID solution.

I've tried using mdadm to just --zero-superblock the drive, but since the HDD was not in an md raid, it cannot perform the command.

Can I just zero out the superblock or even the whole HDD, erasing any leftover RAID metadata?

```
sudo dd if=/dev/zero of=/dev/sda
```

OR can I just zero out a small portion of the HDD instead of the whole HDD to speed things up, but still wipe out whatever RAID metadata is stored?

(Data is no longer needed)

---

### Post by smc18 on 2010-02-03
.

---

