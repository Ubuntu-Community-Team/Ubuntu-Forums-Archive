---
title: "Hard Drive Mount Problem"
date: 2006-01-04
forum: Hardware &amp; Laptops
---

### Post by dk_pa on 2006-01-04
I am having problems with the automounting of my additional hard drives.  At boot it says "device not found."  If I open a terminal after the desktop is loaded and type "mount -a" then the drives mount without a problem.  Could this be becasue they are on my RAID/ATA card and it doesn't load before the mounting?  That is just a quick guess I really am not sure if that is true tho.  I would think a runabout solution would be to write a script that runs at startup to do the "mount -a" command.  Can anyone help me with this?  I assume the script would have to be run as root?

Below is my fstab file.  HDF1 and HDE1 are the drives that are not mounting.  Thanks

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdf1	/media/storage  ext3    defaults	0	0
/dev/hde1	/media/secondary ext3	defaults	0	0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom2   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

---

### Post by dk_pa on 2006-01-05
Bumpity Bump :)

---

### Post by FLeiXiuS on 2006-01-05
No need to bump after only 20 hours.  Give users some time and be patient!

Answers come to you, don't be forceful and demand them.  

Are you able to mount them in the command line?

---

### Post by Amon_Re on 2006-01-05
[QUOTE=dk_pa]I am having problems with the automounting of my additional hard drives.  At boot it says "device not found."  If I open a terminal after the desktop is loaded and type "mount -a" then the drives mount without a problem.  Could this be becasue they are on my RAID/ATA card and it doesn't load before the mounting?  That is just a quick guess I really am not sure if that is true tho.  I would think a runabout solution would be to write a script that runs at startup to do the "mount -a" command.  Can anyone help me with this?  I assume the script would have to be run as root?

Below is my fstab file.  HDF1 and HDE1 are the drives that are not mounting.  Thanks

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdf1	/media/storage  ext3    defaults	0	0
/dev/hde1	/media/secondary ext3	defaults	0	0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom2   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```[/QUOTE]

My first guess would be that the filesystems are being mounted prior to the loading of the modules required for your controller, hence the devices aren't there yet.

What controller is it?

---

### Post by dk_pa on 2006-01-06
> No need to bump after only 20 hours. Give users some time and be patient!

Answers come to you, don't be forceful and demand them. 


Calm down there skipper!  I wasn't demanding anything and the only reason I bumped it was because there are like a million posts on this board in 20 hours.  I will wait longer next time to bump not a big deal but I'm certainly not demanding anything.

Yes, I can mount from the command line.  All I even have to do is mount -a after the desktop is loaded.

> My first guess would be that the filesystems are being mounted prior to the loading of the modules required for your controller, hence the devices aren't there yet.

That was what I was thinking.  It's the ITE8212 card.  Would a script be the easiest way around this?

---

### Post by dk_pa on 2006-01-12
Bueller Bueller?! :p   Seriously tho, any help is appreciated...I'm just not sure how to make a script to become root and mount the drives.  Also, does it hurt anything to always do the mount -a command after startup.  I know it refreshes the fstab (right? hehe) but could that possibly be bothersome at all to my devices.  Thanks again.

---

