---
title: "hdparm -Z"
date: 2008-01-15
forum: Hardware &amp; Laptops
---

### Post by rauko113 on 2008-01-15
hey guys,
i have an external hardrive FreeAgent Seagate connected to my laptop.  It always spinsdown after it sits idle for some time.  i want to use the hdparm -Z command in my terminal to disable spindown (after reading through man hdparm, this seemed the best option) but im not sure exactly what pathname to specify for the device parameter in the command (/media/FreeAgent Drive  is not recognized as a file/folder name)  any advice would be great. thnx much

---

### Post by rauko113 on 2008-01-15
ive tried these commands:
   ```

Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30401   244196001    7  HPFS/NTFS
kenny@kenny-laptop:~$ hdparm -S0 /dev/sdd1

/dev/sdd1:
 setting standby to 0 (off)
 HDIO_DRIVE_CMD(setidle1) failed: Invalid argument
kenny@kenny-laptop:~$ hdparm -Z /dev/sdd1

/dev/sdd1:
 disabling Seagate auto powersaving mode
 HDIO_DRIVE_CMD(seagatepwrsave) failed: Invalid argument

```
i dont get it, invalid argument?

---

