---
title: "USB pendrive woes"
date: 2009-06-02
forum: Hardware
---

### Post by John M on 2009-06-02
I have a 4Gb pendrive with 'vfat' file system that I have used for a couple of years. After transferring files to a WindowsXP PC, and back again, the drive would no longer permit writing to existing files and gave error message "file system is read only". I tried various methods to restore functionality, including sledgehammers like "dd" and "mkfs" and now have an additional problem (or perhaps this is the problem that prevented "dd" etc. from working). It is seen in the report from 'fdisk -l', which says the single partition on the drive has different physical and logical ends.

phys=(500, 254, 63)  logical=(501, 196, 14)   Id c  W95 FAT32 (LBA)

Any ideas much appreciated.

---

