---
title: "A bash question: why can't I dd to a USB?"
date: 2009-08-08
forum: Hardware
---

### Post by pofadda on 2009-08-08
I am attempting to make an install USB for Ubuntu on a 4GB Kingston Data Traveller USB stick.

Following the instructions for doing this on:
[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)
using Mac OS X - DON'T GO AWAY! It's a command-line question!! - 
I get no files written to the stick (apart from the inevitable Mac dot-files, e.g. .fseventsd, etc.)  

Why no installation files?
[LIST]
[*]The stick is partitioned into two 2GB partitions
[*]they are FAT-32.  Safe, I think, and the only non-HFS option on the Mac.
[*]I have tried giving the dd 'of=' as the partition '/dev/disk1s1' and as just the 'disk' '/dev/disk1'.  Both fail.
[*]The dd starts and completes with
[/LIST]
```
...$ sudo dd if=/Users/cxxxm/Downloads/ubuntu-9.04-netbook-remix-i386.img of=/dev/disk1 bs=1m
Password:
1454+1 records in
1454+1 records out
1525657600 bytes transferred in 1213.238270 secs (1257509 bytes/sec)
```
[LIST]
[*]The download passed the MD5 test.
[*]The stick takes writes and reads fine.
[/LIST]

What *should* I have done?:confused:

---

### Post by wannadumpwindows on 2009-08-08
I think you're using the wrong path. Shouldn't it be: ```
/media/disk1
```

---

### Post by pofadda on 2009-08-08
> **wannadumpwindows said:**
> I think you're using the wrong path. Shouldn't it be: ```
/media/disk1
```

No, I'm not.  Underlying a Mac is BSD and it has slightly different naming conventions.  I get confused with these too, so I ran diskutil which confirmed this nomenclature.  

Something else is going wrong...

...and this what it is: a dodgy USB stick.  WHY it's dodgy I have still to find out.  I got another stick - also Kingston but a different model - and it installed on the first go.  Hardware can fail, too!
I tried the Windows route and it failed as well.  That's when the nagging doubt set in.

---

### Post by wannadumpwindows on 2009-08-09
I looked right past the part where you said you were using Mac OS X. 

My fault.

Glad you got it figured out though.

---

