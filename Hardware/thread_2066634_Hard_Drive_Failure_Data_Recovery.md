---
title: "Hard Drive Failure Data Recovery"
date: 2012-10-05
forum: Hardware
---

### Post by Kittysong on 2012-10-05
So my hard drive's been threatening to fail for several months now, and it finally seems to have happened. Earlier programs started crashing, starting with Firefox each time, and after the first crash, programs wouldn't run anymore. If I tried to in terminal, it said something like "can't find stuff/var/sudo: Input/output error". After a couple of times it wouldn't boot at all anymore.

Even though it's been threatening to fail, the computer's been so problematic that I have lots of important files that aren't backed up! So I'm trying to do that from a live boot of Ubuntu.

I've been searching for help for hours and hours, but everything turns up a dead end. Most of the guides are old and so I can't follow the instructions.

Gparted does this:
> Inhibit all polling failed: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.Gddrescue doesn't exist (same with testdisk):
> E: Unable to locate package gddrescueVariants on the mount command don't work since I have no idea what to mount. The guides say to just look at the "Devices" on the side in Nautilus, but that doesn't exist, even if I plug in my external hard drive (the light on it glows, but I can't seem to find it anywhere on the computer).

Fsck from booting into recovery mode just made a blank line, hung for a minute, and then quit.

More errors:

> ubuntu@ubuntu:~$ mount /dev/sda
mount: can't find /dev/sda in /etc/fstab or /etc/mtab> root@ubuntu:/etc# mount -t ntfs-3g /dev/sda1 /media/disk -o force
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?> [ 1324.933282] FAT-fs (sda3): bogus number of reserved sectors
[ 1324.933291] FAT-fs (sda3): Can't find a valid FAT filesystemAnd here's fdisk -l.

```
root@ubuntu:/etc# fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007d531

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    51202047    25600000   83  Linux
/dev/sda2        51202048    61442047     5120000   82  Linux swap / Solaris
/dev/sda3        61442048   488396799   213477376   83  Linux

Disk /dev/sdb: 4124 MB, 4124049408 bytes
127 heads, 62 sectors/track, 1022 cylinders, total 8054784 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000e832

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     8047227     4023583    b  W95 FAT32
```

---

