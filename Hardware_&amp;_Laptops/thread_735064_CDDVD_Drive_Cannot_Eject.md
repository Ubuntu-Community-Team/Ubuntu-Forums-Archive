---
title: "CD/DVD Drive Cannot Eject"
date: 2008-03-25
forum: Hardware &amp; Laptops
---

### Post by testic on 2008-03-25
I cannot eject my CD/DVD drive.

uname:
```
Linux desktop 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux
```
All packages are up-to-date.

The CD/DVD drive is a Philips unknown model CD and DVD rewriter. It is operational, I can eject during bootup and when I am booted in Windows.

I have tried pressing the eject button: no response.

I have tried right-clicking the device in Gnome and choosing "eject": no response, no error.

I have tried the eject command: No response, no error.

eject -v:
```
$ eject -v
eject: using default device `cdrom'
eject: device name is `cdrom'
eject: expanded name is `/dev/cdrom'
eject: `/dev/cdrom' is a link to `/dev/hdb'
eject: `/dev/hdb' is not mounted
eject: `/dev/hdb' is not a mount point
eject: `/dev/hdb' is a multipartition device
eject: trying to eject `/dev/hdb' using CD-ROM eject command
eject: CD-ROM eject command succeeded

```

fstab:
```
$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=e38ceebc-5ef3-41b9-af8c-33bf08e19bdf /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=0b563dd3-a8e5-4dda-9d67-cf562623dc67 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

```

lsof | grep /dev/hdb
lsof | grep /media/cdrom
lsof | grep /media/cdrom0

```
all return nothing

There is no disc currently in the drive, as far as I can determine no processes are using the drive.

```
$ umount /dev/hdb
umount: /dev/hdb is not mounted (according to mtab)

```

I have tried the following also:
```
$ sudo sysctl dev.cdrom.lock=0
dev.cdrom.lock = 0

```
But that makes no difference.

Am I doing something wrong? Am I missing something? Is there anything else I can try?

I have had this problem more or less since I installed Ubuntu, I am fairly sure I could eject the drive at some point in the past, perhaps it ceased working after some system update, I don't know.

I can't reboot the machine every time I wish to insert a disc in the drive, that would be silly.

Any ideas or advice?

Edit: I should have said, this is a desktop machine, AMD64 processor, everything else works fine, even in Ubuntu.

---

