---
title: "Data Recovery on a Failing Harddisc"
date: 2009-12-04
forum: Hardware
---

### Post by beastrace91 on 2009-12-04
Howdy All -

So a friend of mine whos laptop is terribly old has a failing hard disc on & the ext3 filesystem it contains is no longer mountable - and of course being the smart person that she is my friend does not have backups of the data on the disc... 

Anyone suggest any software I can install on Ubuntu to try and scan the hard disc to maybe try to salvage at least some of the data before I pitch the drive?

Regards,
~Jeff

---

### Post by Norami on 2009-12-04
This might be a long shot, but it's worked for me. Try freezing the drive and then trying to access it. There's even been cases of running the drive from the freezer and it working.

I had a failed external, and freezing it actually worked. I froze it, then mounted it, and it lasted long enough to back up the data.

---

### Post by bdalzell on 2009-12-04
When trying to get data off a failing harddrive (after you have given it the freezer treatment ) you will want to mount it on a different computer. Don't try to run the computer it was attached to. 

This type of IDE to USB drive hook up kit is very useful when trying to do these sorts of things with failing harddrives:

SATA/PATA/IDE Drive to USB 2.0 Adapter Converter Cable for 2.5 / 3.5 / 5.25 Inch Hard Drive / Optical Drive with External AC Power Adapter

[http://www.amazon.com/Drive-Adapter-Converter-Optical-External/dp/B002OV1VJW](http://www.amazon.com/Drive-Adapter-Converter-Optical-External/dp/B002OV1VJW)

Make sure you have enough space on the system that you are backing up to for the harddrive data you are recovering because you may only get one chance.

Generally it is not too difficult to remove the harddrive from a laptop but if you have not done it before you may want to have someone who has help you.

In linux you can make a clone of the partition of a harddrive using  the command "dd".

Here is a tutorial for using "dd".

Linux Backup: Hard Disk Clone with "dd"

[http://www.backuphowto.info/linux-backup-hard-disk-clone-dd:](http://www.backuphowto.info/linux-backup-hard-disk-clone-dd:)

---

### Post by beastrace91 on 2009-12-04
Thanks for the link to DD, I'm fair comfterble ripping apart hardware :D and I actually already have one of those fancy IDE/Sata/SataMini to USB cables I need to read the drive, going to try the freezer tip and see if that gets the filesystem to mount properly for me.

Regards,
~Jeff

---

