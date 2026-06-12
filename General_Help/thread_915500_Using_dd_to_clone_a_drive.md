---
title: "Using dd to clone a drive"
date: 2008-09-09
forum: General Help
---

### Post by jeepers on 2008-09-09
I want to clone my drive that ubuntu is on..i'm not entirely sure how to use dd to do this.

I will be (hopefully) cloning my pata 80Gb drive onto a 160Gb sata drive,

My fstab file

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=5da5bc25-127c-4cd2-ba6d-553533320186 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=b64f0e02-6cbe-4895-ae9c-4dbb4942107a none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
```


my present ubuntu drive:

```
Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7b89488

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        9327    74919096   83  Linux
/dev/sdd2            9328        9729     3229065    5  Extended
/dev/sdd5            9328        9729     3229033+  82  Linux swap / Solaris

```

The Drive i want to put the clone image on:

```
Disk /dev/sdb: 160.0 GB, 160041885696 bytes
81 heads, 62 sectors/track, 62242 cylinders
Units = cylinders of 5022 * 512 = 2571264 bytes
Disk identifier: 0x2a098965

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       62243   156290872   83  Linux

```


So what commands do i need to achieve the clone of the disk, keeping in mind i need to keep the UUID's in order from the menus.lst, I will be removing the pata drive and putting the sata drive in its place.

---

### Post by Vivaldi Gloria on 2008-09-10
> **jeepers said:**
> I want to clone my drive that ubuntu is on..i'm not entirely sure how to use dd to do this.

I will be (hopefully) cloning my pata 80Gb drive onto a 160Gb sata drive,

My fstab file

...

So what commands do i need to achieve the clone of the disk, keeping in mind i need to keep the UUID's in order from the menus.lst, I will be removing the pata drive and putting the sata drive in its place.

You should use either ubuntu live cd or clonezilla live cd to clone your root system. I suggest you first give clozilla a try:

[http://www.clonezilla.org/download/sourceforge/](http://www.clonezilla.org/download/sourceforge/)

It's about 80MB live cd.

However you clone the disk you'll need to change the uuid lines in fstab to the uuids of the new disk. You can do this using ubuntu live cd.

---

### Post by HermanAB on 2008-09-10
Boot off a live CD.  Then make sure you know which drive is which and do something like:
# dd bs=100K if=/dev/sda of=/dev/sdb

If you get the if and of the wrong way around then the result will be rather disappointing...

Cheers,

Herman

---

