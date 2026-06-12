---
title: "DVD/CD-RW Drive not Mounting"
date: 2008-03-21
forum: Hardware &amp; Laptops
---

### Post by CrimsoniteX on 2008-03-21
Hello everyone,

I recently installed Ubuntu 7.10 and on my IBM T42 and have been very impressed. However, my DVD/CD-RW drive is not ready any media. I have tried burned dvd's cd's and movie dvd's. When i try to mount it, it gives the following error:

```
Unable to Mount Media
There is probably no media in the drive.
```

I have searched all over the forum, and have found similar issues, but no resolutions have helped me. My fstab is as follows:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0802d2cc-34ca-48ca-8d27-05a2feb47b41 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=ad4d44ea-df2a-4605-b393-175a88606209 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

Please help me if you have any ideas. Thanks in advance!

---

### Post by logos34 on 2008-03-21
Post output of

sudo lshw -C disk

---

### Post by CrimsoniteX on 2008-03-21
> **logos34 said:**
> Post output of

sudo lshw -C disk

Here it is:

```
  *-disk                  
       description: SCSI Disk
       product: FUJITSU MHT2040A
       vendor: ATA
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 006C
       serial: NP0GT4329TPA
       size: 37GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-cdrom
       description: DVD reader
       product: UJDA755yDVD/CDRW
       vendor: MATSHITA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.72
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=open
```

---

### Post by logos34 on 2008-03-21
try replacing /dev/scd0 in fstab with /dev/cdrom

---

### Post by CrimsoniteX on 2008-03-22
My apologies, seems its a hardware problem, my drive seemed to be loose. A good thrust inwards seems to make all media readable :)

---

