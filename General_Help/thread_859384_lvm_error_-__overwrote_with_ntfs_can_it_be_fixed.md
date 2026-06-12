---
title: "lvm error -  overwrote with ntfs can it be fixed?"
date: 2008-07-14
forum: General Help
---

### Post by immolo on 2008-07-14
Hello,

I was installing XP on a machine with a LVM setup and the first disk windows pulls up is my lvm partition on one the drives and not thinking I allowed XP to install but of course windows wants to format the first drive to install the bootloader too.

I now can't access my lvm :( when doing scans with vgscan I get this error:

```
Couldn't find device with uuid 'WdeuO9-8qVK-247L-g0cn-ZqdM-aPT3-R6DLgh'.
  Couldn't find all physical volumes for volume group vhd0.
```

I have changed the partition type back to Linux LVM but of course the pv id has changed so it can't find it.

If anyone has an ideas I would be very grateful.

Thanks

---

