---
title: "Need help in Formatting my external HDD"
date: 2008-10-03
forum: General Help
---

### Post by mn_goutham on 2008-10-03
Hello,
I have an external USB Hard disk (filesystem EXT3).
Its getting detected in ubuntu. but i am not able to format it to FAT32. I tried using gparted ,but here it displays "Lock" symbol  near corresponding HDD partition. Hence the "format to" menu option is disabled when i click on this partition.
Can you please let me know if there are any other way to format my HDD from EXT3 to FAT32?

Thanks in Advance.

---

### Post by drs305 on 2008-10-03
You can use the mkfs.vfat command. It's part of the mkfs command, which include mkfs.ext3, mkfs.ntfs, etc  Read about it here:
```
man mkfs.vfat
```

The command can be as simple as mkfs.vfat /dev/sdb1

---

### Post by vanadium on 2008-10-03
Your external disk was probably mounted. A mounted volume cannot be manipulated. You can use the right-click menu in gparted to unmount the volume before doing anything else with it.

---

### Post by mn_goutham on 2008-10-03
Thanks a lot everyone.
Format to FAT32 was successful using gparted.

---

