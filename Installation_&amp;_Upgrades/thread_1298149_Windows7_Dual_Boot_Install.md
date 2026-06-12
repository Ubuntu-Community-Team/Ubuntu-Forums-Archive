---
title: "Windows7 Dual Boot Install"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by adamjazz1 on 2009-10-22
Hi. I recently tried to upgrade my Vista->Windows7. I am dualbooting Vista and Ubuntu and I was using EasyBCD to modify my boot setup, rather than GRUB. 

I got an error with windows7 saying that it could not modify the boot order/setup. And didnt finish installing. So I have been trying to remove Ubuntu from the boot options so I can boot Windows7. 
Here is my fdisk -lu output.
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00638cbf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2           81920    30801919    15360000    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3   *    30801920   436164695   202681388    7  HPFS/NTFS
/dev/sda4       436164750   488392064    26113657+   5  Extended
/dev/sda5       436164813   486142964    24989076   83  Linux
/dev/sda6       486143028   488392064     1124518+  82  Linux swap / Solaris

Disk /dev/sdc: 2030 MB, 2030043136 bytes
243 heads, 32 sectors/track, 509 cylinders, total 3964928 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          32     3964927     1982448    c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(249, 242, 32) logical=(509, 216, 32)
```

If anyone has some ideas I would appreciate it!

---

