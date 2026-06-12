---
title: "Cannot access CDROM"
date: 2008-11-24
forum: General Help
---

### Post by dsvick on 2008-11-24
I have seen several similar posts here but none of them have solved my problem, in fact it looks like most have been unresolved.

I recently upgraded to Intrepid using a CD, everything went well and everything was/is running fine except I cannot access any CD (data or music) I put in the drive. 

The CD line in my fstab looks like:
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

When I put a CD in nothing happens, there is no desktop icon, I cannot access it through places either, when I right click and select open or double click it nothing happens. I cannot access them through any media players either.

 When  I try to manually mount them using:  sudo mount /dev/scd0 /media/cdrom
I get:
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: you must specify the filesystem type

There are some log entries that may be related:
Nov 24 09:25:06 dsvick-laptop kernel: [ 1568.948668] sr0: CDROM (ioctl) error, command: Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 00
Nov 24 09:25:06 dsvick-laptop kernel: [ 1568.948697] sr: Sense Key : Medium Error [current] 
Nov 24 09:25:06 dsvick-laptop kernel: [ 1568.948703] sr: Add. Sense: Unable to recover table-of-contents

any help would be great, if more info is required let me know and I can post it.

thanks 

Dave

---

### Post by dsvick on 2008-11-25
Does anyone have any input on this? It is really pretty frustrating, everything worked fine with Hardy, and without a usable CD drive I wont be able to use Ubuntu.

---

### Post by leprasmurf on 2009-01-01
I am having an identical problem with a compaq presario running 8.10.  

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/media$ sudo mount cdrom; dmesg|tail
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

[ 4562.261688] sr: Sense Key : Medium Error [current] 
[ 4562.261693] sr: Add. Sense: Unable to recover table-of-contents
[ 4562.272578] sr0: CDROM (ioctl) error, command: Read TOC/PMA/ATIP 43 02 00 00 00 00 aa 00 0c 00
[ 4562.272614] sr: Sense Key : Medium Error [current] 
[ 4562.272620] sr: Add. Sense: Unable to recover table-of-contents
[ 4562.273919] UDF-fs: No partition found (1)
[ 4562.280819] sr0: CDROM (ioctl) error, command: Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 00
[ 4562.280848] sr: Sense Key : Medium Error [current] 
[ 4562.280853] sr: Add. Sense: Unable to recover table-of-contents
[ 4562.286474] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=32

---

### Post by dsvick on 2009-01-02
I should have posted this earlier, it was probably embarrassment that prevented me from doing so. The problem with my CD  drive was that it needed to be cleaned. :oops:

Since it was a laptop all it took was a cotton swap and some rubbing alcohol and it works fine now.

---

### Post by pavan532 on 2013-02-23
please help me ,I am also got same problem......... my LG dvd writer is clean and works fine... yesterday i bought a sony rw dvd.just i try to format my disc it shows unable to recover table of contents.....

---

### Post by beholderrk on 2014-01-27
> **dsvick said:**
> I should have posted this earlier, it was probably embarrassment that prevented me from doing so. The problem with my CD  drive was that it needed to be cleaned. :oops:

Since it was a laptop all it took was a cotton swap and some rubbing alcohol and it works fine now.

I had the same problem. Dsvick, thank you very much for your advice :)

---

### Post by oldos2er on 2014-01-27
Old thread closed.

---

