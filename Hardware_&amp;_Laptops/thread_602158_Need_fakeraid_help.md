---
title: "Need fakeraid help"
date: 2007-11-03
forum: Hardware &amp; Laptops
---

### Post by n_lion on 2007-11-03
I followed the fakeraid debug wiki, and I have attached my outputfile from the section "dmraid -rD generates no files."  I would appreciate any help.

My fdisk output was:
Disk /dev/sda: 500.0 GB, 500028145664 bytes
255 heads, 63 sectors/track, 60791 cylinders, total 976617472 sectors
Units = sectors of 1 * 512 = 512 bytes

I am using a HighPoint RocketRAID 1720 .

Thanks.

---

### Post by n_lion on 2007-11-27
See solution by stant0n:

[http://ubuntuforums.org/showpost.php?p=3641049&postcount=8](http://ubuntuforums.org/showpost.php?p=3641049&postcount=8)


However, the partitions will not  mount after a reboot.  If I mkfs (either ext2 or ext3), the partitions will mount.  After I reboot, I must repeat the process.

---

