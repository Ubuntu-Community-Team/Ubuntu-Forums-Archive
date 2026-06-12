---
title: "Recognise DVD drive after replacement"
date: 2012-02-01
forum: Hardware
---

### Post by Roemer on 2012-02-01
Hi,

Today a technician from Dell replaced the dvd drive in my Dell XPS M1530 because of a jammed dvd.

The disk drive is recognized in the BIOS and when inserting a (windows) boot disk it is able to read and boot from it.

When hitting the eject button while booting, the cd will eject.

Once booted in Ubuntu 11.10, the inserted cd does not appear. Neither does the drive respond to the eject button anymore.

How can I let Ubuntu recognise the drive (in a correct way) again?

Kind regards,

-Edit:

Some extra info:
> sudo lshw -class disk
  *-cdrom                 
       description: DVD-RAM writer
       product: DVD+-RW AD-7640A
       vendor: Optiarc
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: JD07
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
  *-disk
       description: ATA Disk
       product: FUJITSU MHY2120B
       vendor: Fujitsu
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 0081
       serial: K439T7A2600P
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0007c382


> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=672fd6fa-6168-4cb6-a58e-6b80e6a82783 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=4e43499b-472b-4af9-befd-41a7b7c98fef none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0


---

