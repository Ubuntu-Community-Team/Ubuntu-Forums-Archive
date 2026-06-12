---
title: "[SOLVED] Jumping CD drive"
date: 2008-07-29
forum: Hardware
---

### Post by The Dragon Master on 2008-07-29
I recently upgraded from Dapper to Edgy to Feisty to Gutsy to Hardy all in about a week. Everything seemed to go OK, but now with Hardy the CD/DVD drive is behaving strange. With no disk inside it clicks every five seconds (which after a while is like chinese water torture) as if it is always looking to mount a disk. If I use the "eject" command it does open but shuts again immediately, if Iam super quick Ican get a disk in there, but each time I risk getting the disk jammed in the angry drive so I hardly want to put my most valued disks in there. If a disk is in there it does calm down and stop the constant clicking, but getting the disk safely is even trickier than getting it in.

With no disk in the drive the system log viewer prints out the following every click of the drive

dave@daves-desktop:~$ tail -n 17 /var/log/syslog
Jul 29 10:02:41 daves-desktop kernel: [ 707.373208] sr0: CDROM not ready. Make sure there is a disc in the drive.
Jul 29 10:02:41 daves-desktop kernel: [ 707.477067] device-mapper: table: 254:3: linear: dm-linear: Device lookup failed
Jul 29 10:02:41 daves-desktop kernel: [ 707.477413] device-mapper: ioctl: error adding target to table
Jul 29 10:02:41 daves-desktop kernel: [ 707.481262] device-mapper: table: 254:3: linear: dm-linear: Device lookup failed
Jul 29 10:02:41 daves-desktop kernel: [ 707.481656] device-mapper: ioctl: error adding target to table
Jul 29 10:02:41 daves-desktop kernel: [ 707.485207] device-mapper: table: 254:3: linear: dm-linear: Device lookup failed
Jul 29 10:02:41 daves-desktop kernel: [ 707.485578] device-mapper: ioctl: error adding target to table
Jul 29 10:02:41 daves-desktop kernel: [ 707.489040] device-mapper: table: 254:3: linear: dm-linear: Device lookup failed
Jul 29 10:02:41 daves-desktop kernel: [ 707.489383] device-mapper: ioctl: error adding target to table
Jul 29 10:02:41 daves-desktop kernel: [ 707.493445] device-mapper: table: 254:3: linear: dm-linear: Device lookup failed
Jul 29 10:02:41 daves-desktop kernel: [ 707.493821] device-mapper: ioctl: error adding target to table
Jul 29 10:02:41 daves-desktop kernel: [ 707.497370] device-mapper: table: 254:3: linear: dm-linear: Device lookup failed
Jul 29 10:02:41 daves-desktop kernel: [ 707.497749] device-mapper: ioctl: error adding target to table
Jul 29 10:02:41 daves-desktop kernel: [ 707.501241] device-mapper: table: 254:3: linear: dm-linear: Device lookup failed
Jul 29 10:02:41 daves-desktop kernel: [ 707.501740] device-mapper: ioctl: error adding target to table
Jul 29 10:02:41 daves-desktop kernel: [ 707.505210] device-mapper: table: 254:3: linear: dm-linear: Device lookup failed
Jul 29 10:02:41 daves-desktop kernel: [ 707.505592] device-mapper: ioctl: error adding target to table

dave@daves-desktop:~$ tail -n 9 /var/log/messages
Jul 29 10:28:48 daves-desktop kernel: [ 2274.587329] sr0: CDROM not ready. Make sure there is a disc in the drive.
Jul 29 10:28:48 daves-desktop kernel: [ 2274.678824] device-mapper: ioctl: error adding target to table
Jul 29 10:28:48 daves-desktop kernel: [ 2274.687251] device-mapper: ioctl: error adding target to table
Jul 29 10:28:48 daves-desktop kernel: [ 2274.695985] device-mapper: ioctl: error adding target to table
Jul 29 10:28:48 daves-desktop kernel: [ 2274.705581] device-mapper: ioctl: error adding target to table
Jul 29 10:28:49 daves-desktop kernel: [ 2274.714315] device-mapper: ioctl: error adding target to table
Jul 29 10:28:49 daves-desktop kernel: [ 2274.722886] device-mapper: ioctl: error adding target to table
Jul 29 10:28:49 daves-desktop kernel: [ 2274.731401] device-mapper: ioctl: error adding target to table
Jul 29 10:28:49 daves-desktop kernel: [ 2274.739837] device-mapper: ioctl: error adding target to table


dave@daves-desktop:~$ tail -n 2 /var/log/kern.log
Jul 29 10:29:09 daves-desktop kernel: [ 2295.343760] device-mapper: table: 254:3: linear: dm-linear: Device lookup failed
Jul 29 10:29:09 daves-desktop kernel: [ 2295.351563] device-mapper: ioctl: error adding target to table

If anyone could come up with an appropriate sedative for my crazy CD drive I'd buy you the biggest ice-cream in town :biggrin:

---

### Post by The Dragon Master on 2008-07-30
Bump.

---

### Post by The Dragon Master on 2008-08-02
I found the answer on a french forum. Very simple. Here.
[http://forum.ubuntu-fr.org/viewtopic.php?pid=1970790#p1970790](http://forum.ubuntu-fr.org/viewtopic.php?pid=1970790#p1970790)

merci mes amis
:guitar:

---

