---
title: "[SOLVED] fstab"
date: 2007-12-31
forum: Hardware &amp; Laptops
---

### Post by gishaust on 2007-12-31
I have two issues that I have been trying to fix for a week and it should  not be this hard I have trawled the net and tried all sorts of things. So here are the facts I am running  7.10.
I can not get my computer to recognise a dvd player that works in a window machine just fine. I can't mount. Yes my bios does see the DVD.

Before you ask

this is my fstab folder
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9fdb0e8b-6f69-4a35-821a-cb0d545f8c16 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=73a927b3-ae98-4144-a6fc-4916d926b7f7 none            swap    sw              0       0
#second harddrive
/dev/sdb        /media/data 				 ext3     defaults 0 0
#dvd
/dev/scd0     /media/DVD   udf,iso9660 user,noauto     0       0

/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


```

yes all those devices are recognised on the machine here is my  sudo lshw -C disk
```

  *-disk:0                
       description: SCSI Disk
       product: ST36424A
       vendor: ATA
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3.10
       serial: 7CN01J2C
       size: 6149MB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-disk:1
       description: SCSI Disk
       product: ST380215A
       vendor: ATA
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: 3.AA
       serial: 9QZ00FQT
       size: 74GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-cdrom
       description: SCSI CD-ROM
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio
       configuration: status=ready

```

Yes all folders exist in the media folder.

I gave up my windows server and now I beginning to ask why. All  I want this machine to do is see the eighty gig so that in can but data on it and the use the DVD to backup. 

I have tried to format the eight gig twice but every time  i use the following fdisk, cfdisk and editor partitioner. it won't work.

So does anyone want to have shot. It would be appreciated. I am out of ideas and frustrated with the whole thing.

gishaust

---

### Post by NilsE on 2007-12-31
Try this in your fstab for the DVD line

```
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
```

As far as the formatting goes try to boot with the liveCD and use the gparted partition editor to sort it out. Using the LiveCD will free up all the partitions to do whatever you want with them so be careful.

---

### Post by gishaust on 2007-12-31
thanks for the rely but the dvd still is not showing. I don't have a live cd I will have to get one. maybe

gishaust

---

### Post by Yellow Pasque on 2007-12-31
is your user in the cdrom group? Take a look at /etc/group and see if your user name is listed in the cdrom and floppy groups.

---

### Post by gishaust on 2007-12-31
I found this is the file you asked me to look at  is this what you wanted to know

cdrom:x:24:haldaemon,john,fbs
floppy:x:25:haldaemon,john,fbs

---

### Post by Yellow Pasque on 2007-12-31
yeah, it looks good, so i think we can rule out a permissions issue.

---

### Post by gishaust on 2008-01-02
anyone

---

