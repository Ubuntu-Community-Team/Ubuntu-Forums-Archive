---
title: "[SOLVED] Change default swap partition"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by Mitlik on 2009-01-04
When I upgraded to a new kernel it switched all my drives from /dev/hd?? to /dev/sd??. I have made the appropriate changes to the /etc/fstab file, but I still get a blank screen when I start up the new Kernel. When I hit ctrl+alt+F1 it says it can't find somefile and calls out /dev/hda3 my swap partition. All I do is enter /dev/sda3 and kubuntu finishes booting up just dandy.

So how if fstab doesn't fix this, how do I change the default swap partition?


Thanks,
Mitlik

---

### Post by taurus on 2009-01-04
Instead of using the device like /dev/sda3, use the UUID.

```
sudo fdisk -l
sudo blkid
```

---

### Post by Mitlik on 2009-01-04
huginn@Brunhilde:~$ sudo fdisk -l && sudo blkid
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612        2624      104422+  83  Linux
/dev/sda3            2625        3146     4192965   82  Linux swap / Solaris
/dev/sda4            3147       30401   218925787+   5  Extended
/dev/sda5            3147        5757    20972826   83  Linux
/dev/sda6            5758        8367    20964793+  83  Linux
/dev/sda7            8368       10978    20972826   83  Linux
/dev/sda8           10979       30401   156015216   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x213b0fb2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    b  W95 FAT32
/dev/sda1: UUID="2814AEB42C03AA4C" TYPE="ntfs"
/dev/sda2: UUID="fe689ca3-494b-41a4-8061-c9eed9fcc15b" TYPE="ext2"
/dev/sda3: TYPE="swap" UUID="fdf30c83-6955-4216-b0f0-a09cc45fbbce"
/dev/sda5: UUID="74bd3c39-402b-47a2-bc9f-6bf4f422966f" TYPE="ext3"
/dev/sda6: UUID="23224a8e-8301-4ba0-ac82-84d608938708" TYPE="ext3"
/dev/sda7: UUID="bb0e48d8-2ef0-4885-8452-9d68f5655187" TYPE="ext3"
/dev/sda8: UUID="d7927bec-26fd-47ff-8c30-b209a422ef7f" TYPE="ext3"
/dev/sdb1: LABEL="vanaheim" UUID="46E1-C0EC" TYPE="vfat"
huginn@Brunhilde:~$    

```

So I changed my fstab an rebooted

```

huginn@Brunhilde:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda2       /boot           ext2    defaults        0       2
/dev/sda8       /home           ext3    defaults        0       2
UUID=fdf30c83-6955-4216-b0f0-a09cc45fbbce       none            swap     sw             0       0
/dev/sdb1       /media/vanaheim vfat    defaults,utf8,umask=000,dmask=000,uid=huginn    0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto 0       0
/dev/sda1       /media/Windows  ntfs    defaults        0       2
/dev/sda6       /media/Gentoo   ext3    defaults        0       2
/dev/sda7       /media/hda7     ext3    defaults        0       2

```

It still gave me a blank screen and on Ctrl-alt-F1 said "resume: Could not stat the resume decive file '/dev/hda3'..."


Edit: Could this be caused by an out of date package to try to enable suspend2ram/disk?

Edit2: dpkg - l | grep susp showed that I had uswsusp installed, so I tried purging that, and lo and behold it worked fine. Sorry for the post, it didn't occur to me until just now.

---

### Post by taurus on 2009-01-04
What happens when you run these commands?

```
sudo mkswap /dev/sda3
sudo swapon /dev/sda3
free -m
```
Now, make sure the UUID for /dev/sda3 (swap partition) is the same one that you have in /etc/fstab.

```

sudo blkid
cat /etc/fstab
```

---

### Post by Irony on 2009-01-04
The swap entry should be this;

```
/dev/sda3 swap swap sw,pri=1 0 0
```

Also do;

```
sudo swapon /dev/sda3
```

Also check gparted to see that the partitions correspond to that shown in;

```
sudo fdisk -l
```

---

