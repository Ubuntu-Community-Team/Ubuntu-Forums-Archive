---
title: "The story of the internal ATAPI + SCSI Zip  Mount"
date: 2004-12-10
forum: Hardware &amp; Laptops
---

### Post by ayam on 2004-12-10
Read all the other internal atapi zip drives posts but here is my story and problem.
Firstly I have tried two zip drives. 
One is a internal SCSI Zip 100
Another is a internal ATAPI Zip 250.

The internal SCSI Zip 100 automatically mounts itself when I insert a disk. There are no entries in /etc/fstab for this drive. Everything automatically appears which is good :)

My internal Zip 250 is connected as my primary slave (hdb) and dmesg shows that it is spits out hdb: IOMEGA ZIP 250 ATAPI. Also I have a TYAN S2054 Tomcat i810 motherboard and the BIOS has been set to detect the Zip 250 as a ARMD (advanced removeable media device??) and to emulate a harddisk.

I have the ide_floppy module loaded by adding 'ide-floppy' into /etc/modules.

Inititally the Gnome Device Manager did not pick up anything in hdb/primary slave but now its displays "ATAPI Zip 250".

After a bit of fiddling I figured that the right combination for the /etc/fstab entry is:

/dev/hdb /media/zip auto     auto,user,sync,rw    0  0

YUP /dev/hdb4 which is what I use on my Slackware Boot doesnt work. Now when I do the old-fashioned mount /dev/hdb I get the Zip 250 to mount. 

Now I just wnated to know how I can get Zip 250 to automagically mount like the Zip 100.  Do I need to fiddle around withh HAL/udev etc etc (which I have no clue how to)

But from expereince with the Zip 250 on Slack 10; I notice that depending if its a primary slave or secondary slave, the disk will umount BUT not eject. 

Any help would be great

---

### Post by Buran522882 on 2007-05-15
Re: The story of the internal ATAPI + SCSI Zip  Mount
[plants demonstrate Girls Ebay blood pressure](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/latin-porn.html)

---

