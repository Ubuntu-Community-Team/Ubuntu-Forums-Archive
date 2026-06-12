---
title: "cannot boot after upgrading to 8.04"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by art vandelay on 2009-04-28
Hi, I had Ubuntu 7.04 installed, and I downloaded an image CD of 8.04. I've run the installation but the following message appeared after rebooting:

```
check root = bootarg cat /proc/cmdline....
ALERT! /dev/disk/by-uuid/e21..... does not exist. Dropping to a shell!

*(initframs)

```

During the installation I've noticed that my hard drive appeared as a SCSI drive instead of an IDE one. Now if I use the new live CD, fdisk -l lists all my partitions as /dev/sdaX instead of /dev/hdaX.

I managed to edit menu.lst using an old Ubuntu live CD(6.04, wich lists my partitions as /dev/hdaX), and I replaced the following:

```

root=/dev/disk/by-uuid/310147a9........ ro quiet splash

for

root=/dev/sda3 ro quiet splash


```

And all I have now is the same old message but with a different drive:

```
check root ) bootarg ca /proc/cmdline....
ALERT! /dev/sda3 does not exist. Dropping to a shell!

*(initframs)

```

Any ideas will be appreciated.

Thanks in advance.

---

### Post by art vandelay on 2009-04-29
bump

---

### Post by art vandelay on 2009-04-29
I fixed it by adding all_generic_ide to /boot/grub/menu.lst.

---

