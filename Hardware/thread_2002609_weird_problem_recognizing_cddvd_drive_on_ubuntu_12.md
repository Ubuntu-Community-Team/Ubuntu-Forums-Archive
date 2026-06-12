---
title: "weird problem recognizing cd/dvd drive on ubuntu 12.04"
date: 2012-06-12
forum: Hardware
---

### Post by jhnmlkvch9 on 2012-06-12
Hi,

I am running Ubuntu 12.04 on my Dell XPS M1530. My cd/dvd combo drive is not being recognized. When I insert a dvd, the drive spins up and then stops.

The weird thing is if I then suspend the computer and wake it up, the drive is recognized (as /dev/sr0) and the dvd is mounted.

This is the output from lshw before and after the suspend/resume operation:

```

  *-disk
       description: ATA Disk
       product: TOSHIBA MK2556GS
       vendor: Toshiba
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: LJ00
       serial: 11FHT3U2T
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=d0000000

``````

*-cdrom                 
       description: DVD-RAM writer
       product: DVD+-RW UJ-875S
       vendor: MATSHITA
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/DVD Project
       version: D200
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/DVD Project
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted
  *-disk
       description: ATA Disk
       product: TOSHIBA MK2556GS
       vendor: Toshiba
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: LJ00
       serial: 11FHT3U2T
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=d0000000

```This is a dual-boot system and the drive works flawlessly on Windows 7.

For now I can make do with the workaround of suspending and waking the computer, but it would be nice to make it work without having to do this.

thx,
jhn

PS: I've searched the forums and spent the last week trying all the fixes suggested in various bug reports even remotely sounding like this issue, without any success. I'm at my wits end, and finally decided to ask you guys before finally giving up.

---

