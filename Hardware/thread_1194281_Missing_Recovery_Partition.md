---
title: "Missing Recovery Partition"
date: 2009-06-22
forum: Hardware
---

### Post by uss on 2009-06-22
Hi

I have a laptop first with 2 partitions C and D (Recovery partition). I divided C into 3 partitions; one for Windows and the remaining for Ubuntu. I don't have any problem in Ubuntu 8.10 but when I migrate to Ubuntu 9.04 I can't see the recovery partition in Ubuntu (I can see it in Windows Vista). I use live cd but recovery partition is still invisible but I can see it through partition editor in system/administration. The output of sudo fdisk -l is:

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2              11        1316    10485760    7  HPFS/NTFS
/dev/sda3   *        1317        7052    46074420    7  HPFS/NTFS
/dev/sda4            7053       19458    99643772    f  W95 Ext'd (LBA)
/dev/sda5           19131       19458     2620416   dd  Unknown
/dev/sda6            7053        8876    14651217   83  Linux
/dev/sda7            8877        9362     3903763+  82  Linux swap / Solaris
/dev/sda8            9363       19130    78461428+  83  Linux

Partition table entries are not in disk order


```

sda2 is Recovery partition.  Unfortunately I can't remember when I installed ubuntu 9.04 recovery partition was visible or not. C and D are ntfs. I can see C but not D, Any suggestion?

---

### Post by soorie on 2009-07-03
Give a try with Stellar Phoenix Linux Data Recovery Software i am sure it will help you out i have a good experience with this tool.Gud luck

---

### Post by Zack McCool on 2009-07-03
It's there, just not mounted.

If, for some strange reason, you want to mount the partition under Ubuntu, you could use

```

sudo mkdir /mnt/recovery
sudo mount /dev/sda2 /mnt/recovery -t ntfs-3g

```

And the partition will be there.  You could add the proper info to /etc/fstab instead, to have it always mount on boot.

As this partition is not meant for use, I'm not sure why you'd want to do that, but to each his own...   ;)

---

