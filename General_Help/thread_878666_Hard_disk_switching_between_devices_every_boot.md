---
title: "Hard disk switching between devices every boot"
date: 2008-08-03
forum: General Help
---

### Post by mbolo on 2008-08-03
Hi,
I have two hard disk on my computer. It happens a strange thing, the hard disk switch between two devices every boot:

root@serverone:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003bbe6

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf90df90d

 Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9682    77770633+  83  Linux
/dev/sdb2            9683        9964     2265165    5  Extended
/dev/sdb5            9683        9964     2265133+  82  Linux swap / Solaris

root@serverone:~# shutdown -r now


After the reboot:

login as:
Linux serverone 2.6.24-19-server #1 SMP Sat Jul 12 00:40:01 UTC 2008 i686

Last login: Sun Aug  3 11:49:27 2008 from 192.168.1.2
serverone:~$ sudo fdisk -l

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf90df90d

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9682    77770633+  83  Linux
/dev/sda2            9683        9964     2265165    5  Extended
/dev/sda5            9683        9964     2265133+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003bbe6

 Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

As you can see, sdb has now become the 500GB hard disk.
The OS is Ubuntu 8.04.

Any ideas?
Thanks

---

### Post by CatKiller on 2008-08-03
That is peculiar. Does it cause problems? If it does, you can use UUIDs to refer to the hard drives instead in fstab and menu.lst so that the assignments don't matter - they are identified by the actual partitions rather than how they are represented as being connected.

---

