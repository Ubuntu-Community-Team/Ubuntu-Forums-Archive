---
title: "mount: special device /dev/hdc does not exist"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by moisessalum on 2007-10-21
Hi, today I upgraded Ubuntu to 7.10 and my CD drive doesn't mount.

> 
moises@moises-desklap:~$ dmesg | grep sd
[ 4.664000] SCSI device sda: 117231408 512-byte hdwr sectors (60022 MB)
[ 4.664000] sda: Write Protect is off
[ 4.664000] sda: Mode Sense: 00 3a 00 00
[ 4.664000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 4.664000] SCSI device sda: 117231408 512-byte hdwr sectors (60022 MB)
[ 4.664000] sda: Write Protect is off
[ 4.664000] sda: Mode Sense: 00 3a 00 00
[ 4.664000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 4.664000] sda: sda1 sda2 < sda5 sda6 > sda3
[ 4.740000] sd 0:0:0:0: Attached scsi disk sda
[ 4.744000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 21.064000] sdhci: Secure Digital Host Controller Interface driver
[ 21.064000] sdhci: Copyright(c) Pierre Ossman
[ 21.064000] sdhci: SDHCI controller found at 0000:03:09.1 [1180:0822] (rev 19)
[ 32.880000] Adding 1317288k swap on /dev/sda5. Priority:-1 extents:1 across:1317288k
[ 33.276000] EXT3 FS on sda1, internal journal
[ 42.236000] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).


> moises@moises-desklap:~$ sudo mount /dev/cdrom
mount: can't find /dev/cdrom in /etc/fstab or /etc/mtab

This is what appears in /etc/fstab

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a02a8ca2-b59c-4f30-b6f4-44250da1a5d5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=f1dcfd4b-36ef-498d-89f8-5ecb4dc16ef5 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

And this is what appears in /etc/mtab

> /dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0

I've checked like 5 posts and no one can solve my problem.

Help Please!!!

---

### Post by jimwhitend on 2007-11-17
I have the identical problem with my CDROM/DVD unable to mount, although I am not sure it happened immediately after I upgraded to Gutsy.  Did you ever find a solution?  Thanks.

Jim

---

