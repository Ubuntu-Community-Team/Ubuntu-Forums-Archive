---
title: "Ubuntu 12.04 - CD rom not mounting"
date: 2012-12-31
forum: Hardware
---

### Post by Danilo11 on 2012-12-31
After I installed Ubuntu 12.04 on my computer, my CDrom stopped working.
I can see it in Nautilus, I can make it eject from the Terminal, but it doesn't read anything.

This is what I'm getting

wodim --devices

```
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/sg1'    rwrw-- : 'HL-DT-ST' 'RW/DVD GCC-H10N'
-------------------------------------------------------------------------

```


df

```
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda5       73626864 3353056  66533752   5% /
udev             1525316       4   1525312   1% /dev
tmpfs             613084     884    612200   1% /run
none                5120      16      5104   1% /run/lock
none             1532700     372   1532328   1% /run/shm

```


dmesg | grep CD

```
[    2.001069] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-H10N  1.03 PQ: 0 ANSI: 5
[    2.002400] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.002602] sr 1:0:0:0: Attached scsi CD-ROM sr0
```


dmesg | grep sr0

```
[    2.002348] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    2.002602] sr 1:0:0:0: Attached scsi CD-ROM sr0
```


ls -al /dev/cd*
```

lrwxrwxrwx 1 root root 3 Dec 31 09:41 /dev/cdrom1 -> sr0
lrwxrwxrwx 1 root root 3 Dec 31 09:41 /dev/cdrw1 -> sr0
```


sudo mount /dev/sr0 /cdrom

```
mount: no medium found on /dev/sr0

```


sudo hwinfo --cdrom

```
> hal.1: read hal dataprocess 3109: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
19: SCSI 100.0: 10602 CD-ROM (DVD)                              
  [Created at block.247]
  Unique ID: KD9E.zdtrmaEFnW5
  Parent ID: w7Y8.s5hovUCJzsA
  SysFS ID: /class/block/sr0
  SysFS BusID: 1:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0
  Hardware Class: cdrom
  Model: "HL-DT-ST RW/DVD GCC-H10N"
  Vendor: "HL-DT-ST"
  Device: "RW/DVD GCC-H10N"
  Revision: "1.03"
  Driver: "ata_piix", "sr"
  Driver Modules: "ata_piix"
  Device File: /dev/sr0 (/dev/sg1)
  Device Files: /dev/sr0, /dev/cdrom1, /dev/cdrw1, /dev/disk/by-id/ata-HL-DT-ST_RW_DVD_GCC-H10N, /dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0, /dev/dvd1
  Device Number: block 11:0 (char 21:1)
  Features: DVD
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #15 (IDE interface)
  Drive Speed: 48
```


sudo lshw -C disk

```
  *-disk                  
       description: ATA Disk
       product: ST3160813AS
       vendor: Seagate
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: CC2J
       serial: 9SY2T8WS
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=f5104a35
  *-cdrom
       description: DVD reader
       product: RW/DVD GCC-H10N
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/sr0
       version: 1.03
       serial: [
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=nodisc
```


sudo nano /etc/fstab

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=a0ed1a2e-ba20-4f5d-b77d-93e894046e0a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9d4e79e1-0f88-45b2-95bd-fda20108b0fe none            swap    sw              0       0


```

---

### Post by john thumb on 2013-02-23
im new the 12.04 . im having the same issues . i came buy you post and did the same as you and came back the same . 

any luck?

---

### Post by jase2 on 2013-08-10
Hey [COLOR=#000000]Danilo11 & [/COLOR][COLOR=#000000]john thumb have you had any luck in solving this problem? So far my short experience with Ubuntu is exactly the same as yours Dan...
[/COLOR]

---

