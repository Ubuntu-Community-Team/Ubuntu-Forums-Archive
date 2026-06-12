---
title: "Cannot perform any tasks to/from external hard drive"
date: 2008-11-09
forum: Hardware
---

### Post by catchagato on 2008-11-09
I am running 8.10 on a Thinkpad T61 with an external hard drive. Whenever I try to drag a file from my desktop to the external, it won't let me. When I attempt to rename a file, create a new folder in the external hard drive, it won't let me do that either. I did not have this problem in 8.04, only when I upgraded to 8.10. It gives me an "input/output error." Any help please? Thanks in advance!

---

### Post by catchagato on 2008-11-15
Bump. Can anyone please help? My external hard drive is in NTFS, and it worked fine in 8.04. But now in 8.10, it is acting weird. I cannot add a new file or create a new folder in my external hard drive. The error message I get is this: "Error creating directory: Input/output error"

---

### Post by lswb on 2008-11-16
Post your /etc/fstab file here, and the output of the command "sudo fdisk -l", and someone will probably be able to help.

Or, if you want to try and figure it out yourself, have a look at the man pages for mount and fstab, you probably just need to change some options in the fstab line that mounts the ntfs partition.

---

### Post by catchagato on 2008-11-16
This is what I get:


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dca83

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe3e794d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

---

