---
title: "External Optical Drive doesn't work"
date: 2010-07-12
forum: Hardware
---

### Post by BrunoSilva on 2010-07-12
I'm trying to use a recent acquired external optical drive from LG (LG GP08NU6B), but it just doesn't work.

When I plug it to the laptop, and put in a CD/DVD, nothing happens.

I'm thinking that that is no driver avaiable so far. How could I confirm that?

I made a search on the web, and found nothing about it.

Any help is apreciated.

---------
$ lsusb
Bus 008 Device 009: ID 152e:2571 LG (HLDS)
---------

Bruno

---

### Post by BrunoSilva on 2010-07-13
$ ls -l /dev/sr*
brw-rw---- 1 root cdrom 11, 0 2010-06-29 08:23 /dev/sr0
brw-rw---- 1 root cdrom 11, 1 2010-07-13 10:44 /dev/sr1
$ eject -v /dev/sr1 
eject: device name is `/dev/sr1'
eject: expanded name is `/dev/sr1'
eject: `/dev/sr1' is not mounted
eject: `/dev/sr1' is not a mount point
eject: `/dev/sr1' is not a multipartition device
eject: trying to eject `/dev/sr1' using CD-ROM eject command
eject: CD-ROM eject command succeeded
$

This is the output of the command "eject". It works in this case.

But the drive still doesn't work as it should.

I believe that the driver is not yet avaiable for this model. But I don't know where to inform/request that.

Any help?

---

