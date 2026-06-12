---
title: "External Harddrive problems."
date: 2008-05-07
forum: Hardware
---

### Post by nehoc92 on 2008-05-07
Hi all,

I recently formatted my laptop and loaded Ubuntu 8.04.  I have a westerndigital passport 160gb external harddrive that i have been using with Linux.  The harddrive is formatted in ntfs and I was able to access and read its contents without ever manually mounting the drive as I dont know how to do that.  This afternoon i turned on my computer and could no longer access the external harddrive.  I recieve the following error:

"$LogFile indicates unclean shutdown(0,1) Failed to mount '/dev/sdb1': Operation not supported Mount is denied because NTFS is marked to be in use.  Choose one action... Choice 2:If you don't have Windows then you can use the 'force' option for     your own responsibility.  For example type on the command line:  mount -tntfs-3g/dev/sdb1/media/WDEX160 -o force  Or add the option to the relevant row in the /etc/fstab file:    /dev/sdb1/media/WDEX160 ntfs-3g force 0 0"

I do not know what this error message means.  I did no make any changes to the system between the times when the harddrive mounted itself automatically to when it failed. 

Some side notes:  WDEX160 is the volume name of the external that I gave it.  Also in my folder etc there is no folder named fstab?  Lastly when I type dmesg into the terminal the external drive is recognized giving the following lines:

 47.050536] usb-storage: device scan complete
[   47.051006] scsi 2:0:0:0: Direct-Access     WD       1600BEV External 1.04 PQ: 0 ANSI: 4
[   47.052470] sd 2:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   47.053360] sd 2:0:0:0: [sdb] Write Protect is off
[   47.053362] sd 2:0:0:0: [sdb] Mode Sense: 21 00 00 00


sorry post is so long but it seemed that this info is relavent.  Thanks in advance for any help.

last thing,  I'm running linux on my 15.4 inch alienware laptop. 2.16 ghz intel, 7600 go, 2 gig ram for whatever its worth.

---

