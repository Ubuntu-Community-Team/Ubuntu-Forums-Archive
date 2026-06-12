---
title: "CD will auto-mount, DVD will not"
date: 2006-11-04
forum: Hardware &amp; Laptops
---

### Post by Jedigorf on 2006-11-04
I am trying to auto-mount a DVD, but it will not work. Using the same drive, however, I am able to auto-mount music and data CDs.

The fstab says:

/dev/hdc /media/cdrom0 auto user,noauto

I have also tried:

/dev/hdc /media/cdrom0 udf,iso9660 user,noauto

I can mount the DVD myself using:

sudo mount /dev/hdc /media/cdrom0

Any ideas about how to get this thing to auto-mount the DVD?

Thanks.

---

### Post by daveguy on 2006-11-05
I am having the exact same problem! It worked fine for me under Dapper, but does exactly what yours does after I upgraded to Edgy. Hey, solve one problem, make (at least) two people happy! Thanks!

Dave

---

### Post by ujmyhn on 2007-01-11
Same problem here.  I have tried the System->Preferences settings, and I can mount dvds just fine from the terminal.  CDs automount fine.

Ubuntu 6.10
Dell Inspiron 2650
Matshita CDRW/DVD drive (UJDA740 1.03)

Please, someone post a solution!

---

### Post by mbmccormick on 2007-01-18
I am also havign this issue!!! SOMEONE HELP US!!!!

---

### Post by onlybui on 2007-01-26
Bump I'm also having this problem where DVD's are not being auto mounting and I tried to manually mount it and still no go... says there is no medium found... But the same drive that I'm trying to mount can also mount CD-ROM. Trying to mount a DVD game.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=b76a7765-80d5-4b1f-bc98-0e952b137fb9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=498892ad-3bee-4e3a-b7f6-2fbc70f0624c /boot           ext3    defaults        0       2
# /dev/sda5
UUID=21f360f3-d035-4be5-b9b7-18805a2eb739 /home           ext3    defaults        0       2
# /dev/sdb5
UUID=cfade1a7-af9f-49d4-9c53-ef759d2e8ccc /media/300GB    ext3    defaults        0       2
# /dev/sda1
UUID=28D003A7D00379F8 /media/ntfs     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=7692ef48-791d-486b-88a5-1b19afe79e59 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```

---

### Post by whistlerspa on 2007-01-29
Same here with my Toshiba laptop (my desktop works fine). I also notice that data CDs and DVDs don't automount either - and they do on the desktop.

---

### Post by whistlerspa on 2007-01-29
I believe that I've fixed the problem with my laptop. 

In my /etc/fstab my DVD/CD drive was named 

**/dev/scd0**  so I tried changing  this to **/dev/scd** and it now works.

Could something like this be your problem as well perhaps?

---

### Post by cloud1494 on 2007-09-05
Hey, my install does the same thing. I need to be able to play DVDs so it'd be nice to get this working.

EDIT:  I may have found the problem. I went googling around a little and stumbled upon this: [http://www.burnworld.com/dvd/primer/filesystem.htm](http://www.burnworld.com/dvd/primer/filesystem.htm)

Apparently for DVD-ROMs (which I assume Video DVDs are) there's a UDF Bridge filesystem used. Does this filesystem need to be included in fstab in order to get Video DVDs to automount?

---

