---
title: "I/O-Errors with luks and SATA"
date: 2007-07-20
forum: Hardware &amp; Laptops
---

### Post by jsteidl on 2007-07-20
Hi there,

i've got a rather serious problem with my HDD.

First my setup:

1 x 80 GB SATA2 (encrypted Home-partition with luks) = sda
1 x 300 GB SATA2 (Encrypted Media-Partition with luks) =  sdb

i initialize this partitions by hand with

```

crypsetup luksOpen /dev/DEVICE /dev/mapper/MAPPER_NAME
mount -t reiserfs /dev/mapper/MAPPER_NAME /mnt/MOUNT_POINT

```

then it all works pretty well. But ... yes there is a but, sometimes the data-transfer (like music, movies, downloads) freeze on the 300GB-drive and dmesg gives me a heap of output :-(

i had this problem under Gentoo and was unable to solve it, believing it was my own dumbness with the kernel-config. It seems like this is happening with ubuntu too.

Normally it works like this: transfer freezes, needs some time, partition comes back in write-protected mode, WTH?)
Sometimes it does not come back at all, and sometimes the files MIME-Types are not recognized which shows me that there is something messing with my data.

after a reboot everthing is back to normal, until ... yeah, i try to transfer data (normally when i run azureus with a big upstream), but it happened also when i just listenend to music.

so here they come. three times dmesg output.

[http://johannes.schokokeks.org/misc/dmesg.log](http://johannes.schokokeks.org/misc/dmesg.log)
[http://johannes.schokokeks.org/misc/dmesg2.log](http://johannes.schokokeks.org/misc/dmesg2.log)
[http://johannes.schokokeks.org/misc/dmesg3.log](http://johannes.schokokeks.org/misc/dmesg3.log)

i hope somebody is able to help me with this, i am starting to freak out here :-(

Anybody that helps me will get a big box of :popcorn: (if you are from around hamburg!)

---

