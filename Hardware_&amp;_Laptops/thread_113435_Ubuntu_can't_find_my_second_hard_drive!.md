---
title: "Ubuntu can't find my second hard drive!"
date: 2006-01-06
forum: Hardware &amp; Laptops
---

### Post by linus_torvalds_2006 on 2006-01-06
I have recently installed a second hard drive on my Ubuntu system.  Unfortunately, when I get ready to use Ubuntu, Ubuntu gives me no hint that there are two hard drives on my system -- the only drive Ubuntu sees is the one on which the operating system was installed.

This might sound stupid -- the answer might be a simple "mount" command as "root" -- but if the "mount" command is not the answer, then can someone tell me what the answer to this problem is?

I would greatly appreciate any help that can be provided for me.  Thank you.

Brandon Taylor

---

### Post by handy on 2006-01-06
You need to modify you /etc/fstab file  appropriately.  Here's mine below:

+++++++++++++++++++++++++++++++++

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc1	/media/winxp	ntfs	umask=0222	0	0
/dev/hdc5	/media/winwork	ntfs	umask=0222	0	0
/dev/hdc6	/media/winlin	vfat	umask=0000	0	0
/dev/sda1	/media/winbfast	ntfs	umask=0222	0	0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto     0       0
# /dev/dvd        /media/cdrom0   udf,iso9660 ro,user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

++++++++++++++++++++++++++++++++

& then make a directory the same name as you call your drive fstab in the /media/ directory

Then type $ sudo mount -a

All going well you'll see new icons on your desktop :p 

Sorry it's a bit cryptic on the fstab, it's time to go to bed I think.  :-) 

handy

---

### Post by zahidism on 2006-01-06
im a beginner...so...huh?  how do i go about modifying my fstab??

---

### Post by zahidism on 2006-01-06
im a beginner...so...huh?  how do i go about modifying my fstab??

---

### Post by heftigrat on 2006-01-06
[QUOTE=zahidism]im a beginner...so...huh?  how do i go about modifying my fstab??[/QUOTE]

In a terminal type:
vi /etc/fstab

You'll see something like **handy** posted below.  Your storage devices are all identified by "/dev/hd*", your primary master usually being "/dev/hda".  The different partitions are then identified as "/dev/hd*#", where # is the number of the partition, so the mbr on your primary master is "/dev/hda1".

The next thing you'll notice is the mount point, which you must specify - this is to associate the device identifier with an object Linux can treat as a file structure.  I believe the path must exist beforehand, so do a "mkdir" if it's not there (I like to use "/media/mymount").

Next is the options, which I cannot help you with.  Just follow what's there for your other HDD's and you should be fine.  The following line of the file gives you some pretty good clues, which I've attempted to define (in part) above:

# <file system> <mount point> <type> <options> <dump> <pass>

Take it for what it's worth, I hope it helps.  :D

---

### Post by heftigrat on 2006-01-06
Oh, and **linus_torvalds_2006**, not to be rude or anything, but don't you think you should save such a sn for a time when you know everything there is to know about Linux?  I must stress I'm not trying to start a fight, it just kinda gets under my skin that you're using the name of the creator when you don't know how to mount a hdd.  Peace, bro.

---

### Post by zahidism on 2006-01-06
hah @ the handle.  anyway, thanks a lot i got my partition mounted and ready to go

---

