---
title: "Another External HDD problem!"
date: 2009-04-16
forum: Hardware
---

### Post by scott1541 on 2009-04-16
ok, here is my problem: about 30 gb of my drive is ext3 the other 70 or more gb is ntfs, i want to format the ntfs partition to FAT32. command prompt only formats up to 32gb, and i CANNOT delete the other partition (well i can but i WON'T)
Also i have this fat32 formatter program but it will only format unallocated space, so i leave it unallocated but it also recognizes the ext3 partition as unallocated as well, so it would format the WHOLE DRIVE (it will not format existing file systems)

---

### Post by taurus on 2009-04-16
Make sure the ntfs partition is unmounted first before you try to reformat it to fat32.  Install gparted and use it to convert your ntfs to fat32 filesystem.

---

### Post by scott1541 on 2009-04-16
Thanks, ill try it later

---

### Post by scott1541 on 2009-04-16
i have a problem, it is the same as [this]("http://ubuntuforums.org/showthread.php?t=1126190")  gparted does not recognize any partitions on the external HDD but it recognizes them on the internal HDD

---

