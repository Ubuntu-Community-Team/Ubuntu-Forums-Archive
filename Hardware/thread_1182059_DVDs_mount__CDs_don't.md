---
title: "DVDs mount  CDs don't"
date: 2009-06-08
forum: Hardware
---

### Post by gleble on 2009-06-08
My cdrom has developed a strange problem. It will mount and play DVDs but says Unable to scan CD-RW/DVD+-RW Drive for media changes. In the text blow it suggests a possible cause might be 'message bus security policy blocked the reply'

Does anybody know what is wrong?

---

### Post by gleble on 2009-06-09
I tried $mount cdrom and got

```
***@laptop:~$ mount cdrom
mount: can't find cdrom in /etc/fstab or /etc/mtab
```

Any ideas

---

### Post by boof1988 on 2009-06-09
> **gleble said:**
> I tried $mount cdrom and got

```
***@laptop:~$ mount cdrom
mount: can't find cdrom in /etc/fstab or /etc/mtab
```

Any ideas

Maybe try...

```
mount [COLOR="Red"]/dev/[/COLOR]cdrom
```

You might have to have the "/dev/" part in front of the "cdrom".

Also, could you maybe post the output of...

```
cat /etc/fstab
```
and
```
sudo fdisk -l
```

... these may help with trouble-shooting your problem.

---

### Post by gleble on 2009-06-09
Here you go. Hope it makes sense to you.

```
*@laptop:~$ mount /dev/cdrom
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: /dev/scd0 already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/scd0 is already mounted on /media/cdrom0
*@laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=856d304d-903a-4c0d-83fc-b7585c43c09e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=671d992d-5b95-4d2d-ab53-187550277aa5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

*@nlaptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93fec8ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10240000   27  Unknown
/dev/sda2            1343       10320    72115785   83  Linux
/dev/sda4           10760       19457    69866685    5  Extended
/dev/sda5           10760       19097    66974953+  83  Linux
/dev/sda6           19098       19457     2891668+  82  Linux swap / Solaris
```

---

### Post by gleble on 2009-06-09
Sorry on the last post I had a DVD in the drive.
Now with a CD in mount /dev/cdrom0 works after mssing about for a bit. Thanks

---

### Post by gleble on 2009-06-09
One more point. What does the ISO reference mean in this line from fstab
```
/dev/scd0       /media/cdrom0   auto,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by boof1988 on 2009-06-09
> **gleble said:**
> One more point. What does the ISO reference mean in this line from fstab
```
/dev/scd0       /media/cdrom0   auto,iso9660 user,noauto,exec,utf8 0       0
```

According to [Ubuntu Community *fstab* page](https://help.ubuntu.com/community/Fstab#File System Type), it seems that *iso9660* is the file-system type used (generally) for CD/DVD media.

I'm not sure why the CDs do not mount automatically.  Hopefully someone else can help.

For reference:
[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://manpages.ubuntu.com/manpages/jaunty/man8/mount.8.html](http://manpages.ubuntu.com/manpages/jaunty/man8/mount.8.html)
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by yaroto98 on 2009-06-09
How are you unmounting the dvds? You might not be fully unmounting dvds before trying to mount the cds. Put in a cd and reboot. What happens?

---

