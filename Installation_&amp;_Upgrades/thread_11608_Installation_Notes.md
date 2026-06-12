---
title: "Installation Notes"
date: 2005-01-18
forum: Installation &amp; Upgrades
---

### Post by Chas on 2005-01-18
Problem: the floppy doesn't work.

/etc/fstab
/dev/fd0	/media/floppy0	auto	rw,user,auto	0	0

mount: /dev/fd0 is not a valid block device

Is there something wrong in fstab?

---

### Post by nocturn on 2005-01-18
[QUOTE=Chas]Problem: the floppy doesn't work.

/etc/fstab
/dev/fd0	/media/floppy0	auto	rw,user,auto	0	0

mount: /dev/fd0 is not a valid block device

Is there something wrong in fstab?[/QUOTE]

Is the floppy formatted?

---

### Post by Chas on 2005-01-18
I started over with a new floppy diskette.  It worked.  Thanks and sorry for the oversight.

Now I cannot copy a simple file onto the floppy.  Message:  "You do not have permission to write to this folder."  The diskette is not write protected.  I want the floppy drive to be able to RW for all users on start up.  I think I have the correct line in the fstab file:

/dev/fd0 /media/floppy0 auto rw,user,auto 0 0

Where can I learn all about devices, fstab, and whatever else i need to know to get all my other devices working, including the modem.

---

### Post by fjordlander on 2005-01-20
Hi Chas,

I suspect  (might be wrong) that a change from "user" to "users" in the fstab line will help because user means only the user who mounted the drive has access whereas users means any user can mount or unmount the drive.   I am guessing the current version of your fstab means that only the account (root?) that the drive is automounted by would have write access.   If I am wrong I would love to know the correct explanation.   

Cheers!


PS -  if the floppy is not being automatically mounted, ie you are going to a command line and typing "mount /media/floppy0" then the above would not apply as you would automatically have write access as the user doing the mounting.

---

### Post by wallijonn on 2005-01-21
[http://www.ubuntuforums.org/showthread.php?t=3687&highlight=floppy](http://www.ubuntuforums.org/showthread.php?t=3687&highlight=floppy)

---

### Post by Chas on 2005-02-04
Thanks for the help.  I am moving rather slow.  I almost have everything recognized and working.  I have 2 CDR drives: an internal RO and an external HP 8200 Cd-Writer.  I can burn data disks with Nautilus to the external, and play MP's on a second physical drive with Rythymbox.

Here are the problems: when I put an audio CD in internal CDR drive, the CD Player panel comes up and everything works okay.  When I put and audio CD in the external CD player, sometimes the CD Player panel comes up and it appears to be playing, but no sound.  Sound Juicer works for the internal CDR drive but the external CDR drive is not recognized.  any comments?

Under Volume Control  for some strange reason I have four devices:
Analog Devices AD1881 [OSS Mixer] - the volume control functions
SigmaTel STAC9708/11 [OSS Mixer] - does not appear to function.
Intel 82801AA-ICH [Alsa Mixer] - appears to function
Ensoniq AudioPCI [Also Mixer] - does not appear to function

here is /etc/fstab

proc     /proc           proc    	defaults        		0 0
/dev/hda1      /               ext3    	defaults,errors=remount-ro 	0 1
/dev/hda5      none            swap    	sw              		0 0
/dev/hdc        /media/cdrom0   udf,iso9660 	ro,user,noauto  		0 0
/dev/sr0        /media/cdrom1   udf,iso9660 	rw,user		  		0 0
/dev/fd0        /media/floppy0  auto    	rw,user  			0 0
/dev/hdb1     /media/Kahuina  vfat    	user,umask=000 			0 0

---

