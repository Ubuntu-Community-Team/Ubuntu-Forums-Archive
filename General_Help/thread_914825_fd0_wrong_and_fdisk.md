---
title: "fd0 wrong and fdisk"
date: 2008-09-09
forum: General Help
---

### Post by ellgor on 2008-09-09
Hi all,

I get this error message when I run fdisk:

Warning: Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0 has been opened read-only.


which is all very well if the floppy was even connected, which it isn't?

Also from fdisk the output here:

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908   83  Linux
/dev/sda2            9353        9729     3020220    5  Extended
/dev/sda5            9353        9729     3020220   82  Linux swap

is that right, and finally, fdisk shows devices as sda, sdb etc. but if I run "sudo grub" that returns (hd0,0), which is the correct way for mounting purposes.

Thanks.

Regards, Ellgor.

---

