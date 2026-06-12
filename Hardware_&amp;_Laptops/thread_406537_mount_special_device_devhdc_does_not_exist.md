---
title: "mount: special device /dev/hdc does not exist"
date: 2007-04-11
forum: Hardware &amp; Laptops
---

### Post by Cloudy on 2007-04-11
So just tonight I popped a CD in my laptop (Dell Latitude C640)'s CD-ROM drive and got this error whenever trying to mount it. It's worked fine in the past; it worked fine just last week even. What's the deal?

Here's some output for ya:


dmesg | grep sd
```

[    6.556000] SCSI device sda: 39070080 512-byte hdwr sectors (20004 MB)
[    6.556000] sda: Write Protect is off
[    6.556000] sda: Mode Sense: 00 3a 00 00
[    6.556000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.556000] SCSI device sda: 39070080 512-byte hdwr sectors (20004 MB)
[    6.556000] sda: Write Protect is off
[    6.556000] sda: Mode Sense: 00 3a 00 00
[    6.556000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.556000]  sda: sda1 sda2 < sda5 >
[    6.600000] sd 0:0:0:0: Attached scsi disk sda
[    6.604000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   27.520000] EXT3 FS on sda1, internal journal

```


cat /etc/fstab/
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=00419d4e-5701-4baf-8b5e-c3f3463b3f5c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=6b42c017-8ef9-4288-ad1a-07a276581257 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

The only things I've done in the past week are download and use localepurge, do sudo apt-get autoclean, etc.. just cleaning out some old files. 

So, help? :D

---

