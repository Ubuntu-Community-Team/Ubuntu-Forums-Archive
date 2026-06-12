---
title: "Windows crash on dual boot machine.. need to recover"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by terrordrone on 2009-05-30
Hello,

    I have a dual boot machine. My kubuntu 8.10 is on a separate ext3 partition and i have a separate partition for swap as well. 

    ```

>sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x85ab85ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1305    10482381    7  HPFS/NTFS
/dev/sda2            1306       12597    90702990    f  W95 Ext'd (LBA)
/dev/sda3           12598       14593    16032870   83  Linux
/dev/sda5            1306        4569    26218048+   7  HPFS/NTFS
/dev/sda6            4570        8485    31455238+   7  HPFS/NTFS
/dev/sda7            8486       12401    31455238+   7  HPFS/NTFS
/dev/sda8           12402       12597     1574338+  82  Linux swap / Solaris
    
```

my windows xp installed on c drive crashed today. I am unable to boot into windows but my linux is intact. If i re-install windows, i will lose my installed kubuntu. 

1. Is there a way i can recover linux without re-installing it after installing windows ?

2. Will try and share more information about the bsod i get during boot, but any way i can recover windows and i need not do anything

---

