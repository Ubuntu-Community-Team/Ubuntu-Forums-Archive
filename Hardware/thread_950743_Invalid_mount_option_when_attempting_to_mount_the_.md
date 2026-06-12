---
title: "Invalid mount option when attempting to mount the volume."
date: 2008-10-17
forum: Hardware
---

### Post by nickcboi on 2008-10-17
I am rather new to Linux/ubuntu so I was meddling with things that I may should not have been meddling with. I noticed that once a volume (such as my partitioned) hard drive does not remain mounted once the computer is restarted or shut down. I tried to make it permanently mounted by adding a mount point. I just named it  Windows if I remember. Also I set the mount settings to "automatic" by just typing in automatic there. and now I receive this error message when I try to mount the hard drive again:

Cannot mount volume

Invalid mount option when attempting to mount the volume.

Any help?

---

### Post by nickcboi on 2008-10-17
Please help?

---

### Post by amp711 on 2008-10-17
I am guessing that you need to add an entry into your fstab.  

If you open a terminal window and 

**cd /etc **

then do a 
[B]
more fstab
[/B]
do you have just your root partition and swap?

---

### Post by nickcboi on 2008-10-18
Should I post what is in my fstab?

---

### Post by nickcboi on 2008-10-18
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=6f09d7b3-30d9-4323-b2c7-fedfae904e7a /               ext3    relatime,error
s=remount-ro 0       0
# /dev/sda6
UUID=88b3aaab-9e22-4c7a-bafd-726702c776ff none            swap    sw            
  0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

That is what I see when I did the commands you instructed me to do.

---

