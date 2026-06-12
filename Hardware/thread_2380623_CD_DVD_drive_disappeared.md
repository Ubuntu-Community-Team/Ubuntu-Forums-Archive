---
title: "CD DVD drive disappeared"
date: 2017-12-19
forum: Hardware
---

### Post by raequin on 2017-12-19
Two days ago I was using abcde to rip CDs on a laptop running 16.04.  After a few discs I selected the system setting to "Do nothing" when a music CD is inserted.  Yesterday when I went to rip some more I got

```
matt@BESTLenovo:~$abcde
[ERROR] abcde: CDROM has not been defined or cannot be found

```

A little investigating led me to wodim and that yields

```
matt@BESTLenovo:~$wodim --devices
wodim: No such file or directory.
Cannot open SCSI driver!

```

The sense I got from reading about this is that it likely indicates a hardware failure but when I boot the laptop into Windows the optical drive works fine.  Here's what fstab shows:

```
matt@BESTLenovo:~$cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=eff291d7-9ebb-4fee-a0ae-97904de97133 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=283c5008-a90a-4f52-a2b1-7128e93a9ae5 none            swap    sw              0       0

```

The only change I've made in an effort to regain use of the optical drive has been to change the system setting back to having it ask me what to do when inserting an audio CD.

Thanks for reading this.  Hopefully you can offer a suggestion on how to get the drive back working.

---

### Post by sccman on 2017-12-20
Hmm can your computer detect the CD drive?

```
sudo lshw -C disk
```

---

### Post by raequin on 2017-12-20
As suddenly as this problem started, it has gone away.  Here's the output you requested.

```

matt@BESTLenovo:~$ sudo lshw -C disk
  *-disk                  
       description: ATA Disk
       product: HITACHI HTS54755
       vendor: Hitachi
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: D60D
       serial: J2160051CTXDGC
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=9b85a005
  *-cdrom
       description: DVD-RAM writer
       product: DVD-RAM UJ8B1AS
       vendor: MATSHITA
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: 8.21
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

```

The drive is working fine today.  Two days ago when I ran lshw, the only result was for the ATA Disk.  Seems mysterious to me.

---

### Post by sccman on 2018-01-05
For whatever reason, it seems as though the CD drive doesn't get detected by the computer at all when it happens.

Have you opened your laptop recently? It can sometimes mean it's a physical connection in the computer that isn't securely connected and the connection jiggles in and out.

If that doesn't work, try mounting the drive:

```
sudo mkdir /media/cdrom  # Create a mount point directory
sudo mount /dev/sr0 /media/cdrom # Mount your CD drive to the new directory
```

I can't rule out yet if it's a hardware-related issue yet, but there wouldn't be much we could do to fix hardware issues.

---

