---
title: "How to mount an encrypted partition that contains Logical Volumes through udev?"
date: 2010-03-28
forum: Hardware
---

### Post by count28 on 2010-03-28
Hi, I have an external hard disk (120 GB) which I would like to use for making backups of my personal files and system images. I would like to keep these files in two seperate locations (partitions): data and sysimg. Since it's hard to say in advance what would be the optimal partition sizes I decided to use LVM2 so that I can grow the partitions (or to be more accurate: Logical Volumes) to my needs. On top of that I would like to encrypt the (one) partition which contains the Volume Group. I have found several websites that contain very useful information which I have used to work out this plan.

I have succeeded to partition the disk (just one large partition), encrypt it with LUKS and setup two Logical Volumes (in one Volume Group). Unfortunately, the automatic mounting process didn't work the way I would like it to work, so I decided to do this myself. I have found that udev could help me with this. So I have written a udev rule which creates a symlink (/dev/backup_drive) to the device node which is created when I connect the disk. This works just fine. The next steps would be to unlock the one partition, activate the two LVs inside and mount these LVs to their mount points (/media/backup_drive/data and /media/backup_drive/sysimg respectively). I have found that it is possible to run a script upon execution of a udev rule (through RUN+="/path/to/my/script"). So far I have written a one-line script (apart from a shebang and comments) which is supposed to unlock the encrypted partition: /sbin/cryptsetup luksOpen /dev/backup_drive backup_drive. When I enter this command manually (as root) I'm prompted for my passphrase after which it unlocks the partition. However when I try to run this script through a udev rule it simply doesn't work (.i.e. it doesn't prompt me for my passphrase and consequently also doesn't unlock the encrypted partition). To make sure that the script is being executed when I connect the drive I have substituted the command by a command which creates one of my mount points (/bin/mkdir -p /media/backup_drive/data). This works as expected.

So I hope that someone can explain to me why I cannot run cryptsetup from a script launched by a udev rule and how I can solve this problem. Any idea, hint or suggestion is greatly appreciated.

---

