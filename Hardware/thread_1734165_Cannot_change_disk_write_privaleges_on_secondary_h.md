---
title: "Cannot change disk write privaleges on secondary hard drive"
date: 2011-04-19
forum: Hardware
---

### Post by Ninja duck on 2011-04-19
I have a home built computer with 2 sort-of old hard drives (PATA). I have ubuntu installed on the small hard drive (40g) and keep and install large files on the larger, second hard drive (Storage, 250g). I've had several problems associated with a lack of write permissions on the secondary hard drive. It's formatted as fat32 and I've used it with windows xp and 7 as well as with ubuntu. I've had the same problem with files created in ubuntu as well as files from when I was in Windows.

I've tried right clicking on the hard drive, selecting Properties-->Permissions. Anything I change in that menu switches back immediately and no changes are made. I've tried chmod -R +w /media/Storage but it doesn't change anything either. It just takes a while for terminal to finish the command, but it doesn't fix the problem.

And yes, I've tried all of these things both with the drive mounted and without it being mounted.


etc/fstab if it helps. Anything else you need let me know.
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a347b264-a10c-4dd6-85e7-21310cf5c024 none            swap    sw              0       0
```

sudo lshw -c disk (EARTH is a dvd i have inserted, SATA)
```
  *-disk:0                
       description: ATA Disk
       product: ST340014A
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 8.01
       serial: 5JXDCQSA
       size: 37GiB (40GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000eb2fa
  *-disk:1
       description: ATA Disk
       product: ST3250623A
       vendor: Seagate
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: 3.04
       serial: 5ND2WCH4
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=971bf9fd
  *-cdrom
       description: DVD-RAM writer
       product: DVD Writer 1260d
       vendor: HP
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/EARTH
       version: KH25
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/EARTH
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted

```

---

### Post by ashickur.noor on 2011-04-20
first mount your drivs.Then from terminal use this command
```
sudo chmod 777 -Rf /media/your_drive_name
```
hope it helps.

---

### Post by Ninja duck on 2011-04-20
No Change.

---

