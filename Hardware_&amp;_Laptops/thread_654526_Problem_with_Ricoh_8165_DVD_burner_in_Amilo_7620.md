---
title: "Problem with Ricoh 8165 DVD burner in Amilo 7620"
date: 2007-12-31
forum: Hardware &amp; Laptops
---

### Post by jojogunne on 2007-12-31
Hello,
I installed gutsy on my Fujitsu-Siemens Amilo 7620 notebook. Everything works fine so far. The only trouble comes from the internal Ricoh 8165 DVD-burner (IDE):
```
hdc: lost interrupt
hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
```
The solution which is described **_[here]("http://www.ee.oulu.fi/~iiska/articles/ubuntu_in_a7620.html")_** may work for the given problems with dapper, edgy or breezy but not with gutsy :confused:
I tried the following and added these parameters to the kernel -line in file: /boot/grub/menu.lst
```
hdc=noprobe hdc=cdrom
```
This does not solce the problem :(
This is my /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=67d9b2b2-8bb8-464a-a9f5-e140ddd71325 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=b6938ee7-fbf3-4c22-b5e2-51ec3d9435d6 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```
The DVD is master on IDE1 (second IDE channel)

Does someone know a modification for gutsy?

Thank you
Jo

---

### Post by notnowson on 2007-12-31
hi,

I've got the same machine as you and have had the same problem since upgrading to Gutsy.  Taking a suggestion from another thread (sorry I can't remember which one), I replaced "udf" in the line below with "auto" and it seems to work.  

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

I have no idea why and don't know if there may be any drawbacks but I've rebooted a few times since and everything seems to be stable.

good luck

---

### Post by jojogunne on 2008-01-02
Hi,
thanks for your reply.
Your hint showed me some new things. I tried to modify my /etc/fstab in some different ways. Some things are better now (the boot process is much shorter :) ) but I have not managed to get the writer to work correctly up to now.
I tried the following (and some more combinations):
```
/dev/hdc        /media/cdrom0   auto     user,noauto     0       0
/dev/hdc        /media/cdrom0   udf     user,noauto     0       0
/dev/hdc        /media/cdrom0   udf     user,noauto,exec     0       0
/dev/hdc        /media/cdrom0   udf     user,noauto,rw     0       0
...
```
Can someone tell me the correct syntax (maybe other options) for a DVD-burner (especially a Ricoh 8165 :) )?

thanks
Jo

---

