---
title: "Swap not recognized, memory full"
date: 2008-08-14
forum: General Help
---

### Post by teddmeister2 on 2008-08-14
I just installed hardy heron and linux can't see my swap partition, which makes it impossible to function properly with the abysmally small amount of memory I have on my computer.  What should I do?

---

### Post by Elfy on 2008-08-14
Can you post the output of these

```
sudo fdisk -l
cat /etc/fstab
sudo blkid
free -m
```

---

### Post by sayakb on 2008-08-14
You may have to enable your swap. For example, if /dev/sda2 is your swap, do:
```
sudo swapon /dev/sda2
```
Then check by:
```
free -m
```
..that your swap is functional or not.

---

### Post by teddmeister2 on 2008-08-14
Thanks man.
I don't have to do that every time I boot, do I?

---

### Post by Too Late on 2008-08-14
No, you don't. You just have to repair your /etc/fstab file. Follow the insctructions mentioned in the first answer so we can tell you how to edit your /etc/fstab.

---

### Post by teddmeister2 on 2008-08-14
Here they are
```
Disk /dev/sda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5        1740    13944420    7  HPFS/NTFS
/dev/sda3            1741        3564    14651280   83  Linux
/dev/sda4            3565        3649      682762+  82  Linux swap / Solaris

Disk /dev/sdb: 1027 MB, 1027416576 bytes
16 heads, 63 sectors/track, 1990 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x19ae19ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1991     1003305    e  W95 FAT16 (LBA)
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=c9e0dfbd-5a20-480d-b9a2-a18ac1dd6994 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=f7ebd4bc-9b98-4d6b-a247-55bcf9a18e2b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

```
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D2-0C12" TYPE="vfat" 
/dev/sda2: UUID="EA987E36987E00FD" LABEL="Einstein" TYPE="ntfs" 
/dev/sda3: UUID="c9e0dfbd-5a20-480d-b9a2-a18ac1dd6994" TYPE="ext3" 
/dev/sda4: TYPE="swap" UUID="8f6c5166-c3de-4420-a6bc-8d0f706ce17e" 
/dev/sdb1: SEC_TYPE="msdos" UUID="5BA9-0098" TYPE="vfat" 
```

```
             total       used       free     shared    buffers     cached
Mem:           248        136        111          0          4        119
-/+ buffers/cache:         12        236
Swap:            0          0          0
```


And the swap was functional when I tried the swapon command.

Thanks so much for your help.

---

### Post by teddmeister2 on 2008-08-14
so does my fstab just have the wrong UUID?

---

### Post by Elfy on 2008-08-14
the uuiod has changed in fstab - open it to edit

```
sudo cp /etc/fstab /etc/fstab.1408
gksudo gedit /etc/fstab
```

Go to this line and replace the red line

```
# /dev/sda4
[COLOR="Red"]UUID=f7ebd4bc-9b98-4d6b-a247-55bcf9a18e2b[/COLOR] none            swap    sw
```

with > UUID=8f6c5166-c3de-4420-a6bc-8d0f706ce17esave and it should work on reboots

---

### Post by teddmeister2 on 2008-08-14
Thanks so much.  I appreciate the help.

---

### Post by Elfy on 2008-08-14
You're welcome - can you mark thread solved - use thread tolls at the top.

---

