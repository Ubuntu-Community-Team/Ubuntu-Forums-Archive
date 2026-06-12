---
title: "Set up a new partition in a LVM"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by natousayni on 2009-11-01
Hi all !

I've just installed 9.10 and tried an LVM-encrypted option. I went well but my filesystem is only of 70Go in a 250Go harddisk. 
I don't  manage to create a new partition within the LVM for all the freespace (more than 150Go). Gparted give me one single untouchable block of 230 and here is what gives me "sudo fdisk -l":

```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30370   243946993+  83  Linux
/dev/sda2           30371       30401      249007+   5  Extended
/dev/sda5           30371       30401      248976   83  Linux

```


I've read about lvcreate but i was not sure it was the right tool to use, and the way to use it...

please, if anyone could help me :)

thanks to all !

all best,

---

