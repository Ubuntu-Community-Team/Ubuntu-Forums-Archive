---
title: "HDD vanished after restart"
date: 2008-10-10
forum: Hardware
---

### Post by slinkey1981 on 2008-10-10
So I had a random restart, and when trying to access content on my Ubuntu PC, none of it was visible.

I lost my HDD, which is plugged into both the IDE cable and power.

It shows up in fdisk -l, but when I try to mount it, it says it doesn't exist. I am stumped.

> 
shifty@MediaBox:~$ sudo mount /dev/sbd1 /mnt/MediaShare/
mount: special device /dev/sbd1 does not exist
shifty@MediaBox:~$ sudo fdisk -l

Disk /dev/sda: 8004 MB, 8004132864 bytes
255 heads, 63 sectors/track, 973 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d290f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         973     7815591   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x47057d04

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdc: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         984     7897056+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(982, 254, 63) logical=(983, 36, 13)
shifty@MediaBox:~$ sudo mount /dev/sbd /mnt/MediaShare/
mount: special device /dev/sbd does not exist


Ok, I noticed my silly basic mistake. And feel a lot of shame.

But I now have something slightly stranger happening.

> 

shifty@MediaBox:~$ sudo mount /dev/sdb1 /mnt/MediaShare/
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /mnt/MediaShare/ -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /mnt/MediaShare/ ntfs-3g force 0 0


I have not had Windows on this PC for quite a while, is there any other reason that could cause this to happen? I don't have any way to "Exit Windows Cleanly" because... I only have Ubuntu....

How likely is it that something bad (loss of data, corruption) can happen using the "mount -t ntfs-3g /dev/sdb1 /mnt/MediaShare/ -o force" command?

---

