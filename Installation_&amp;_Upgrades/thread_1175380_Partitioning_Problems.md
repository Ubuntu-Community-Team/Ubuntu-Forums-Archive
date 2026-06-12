---
title: "Partitioning Problems"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by russ1982ny on 2009-06-01
I have tried from several different means to partition a new hard drive; all have failed.  My data hard drive is sitting, intact and uncorrupted, so hurray for that.  It's completely unplugged.

My new hd on the other hand will not partition/format for the life of me, and I can't figure out why.  The installer sees the drive, a 320GB Western Digital EIDE drive, but cannot touch it to partition or format it when using either the guided or manual methods.  Gparted doesn't see it, either.

When running fdisk -l as suggested to others in the forum here, I get the following: 
Disk /dev/sdb: 1003 MB, 1003487232 bytes
255 heads, 63 sectors/track, 122 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000eacd4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         122      979933+   c  W95 FAT32 (LBA)

/dev/sdb1 is not the drive I wish to partition and format.  That one is on /dev/sda1.  I'm not even sure that what's appearing at /dev/sdb1 isn't the USB drive I'm currently running a live environment off of.  A bit of an fdisk newb.

Any suggestions besides return the new drive to the store and cry myself to sleep?  Thanks.

---

### Post by dandnsmith on 2009-06-01
I'd hazard a guess that the sdb is really a 1GB (pseudo) HDD which is your usb stick.

The fact that the 320GB HDD doesn't get listed is a problem.

1. Does the initial BIOS display show the 320GB disk as connected?
2. have you looked to see if any error messages are thrown up by the live system when it boots (relating to sda)?

Pending further detail, I'd be wondering:
- is the new HDD viable?
- is the BIOS/motherboard old enough that the size of HDD connected matters?
(for the latter, I assume that the older HDD, when connected via the port you're trying to use the new one on, still operates correctly)

---

### Post by theozzlives on 2009-06-01
What are you booting up on? Normally it's sda. Also don't rule out that it may be a bad drive, even though it's new.

---

### Post by Mark Phelps on 2009-06-01
If the Ubuntu installer sees the 320GB drive but just won't format it, try downloading, burning, and using the GParted LiveCD from distrowatch.com to do the partitioning. It's newer than the version bundled with the installer and can often work around installer-based problems.

---

### Post by AE000 on 2009-06-01
Russ, just curious as what HD model do you have, I'm also having problems partitioning a 320Gb Western Digital HD, mine is model WD3200AAKS.

Alex.

---

### Post by russ1982ny on 2009-06-01
I'm at work right now, and lucky enough to be able to burn a Gparted live cd from here to use at home.  Love my workplace. :-)

I'll be using that when I get home and reporting results here.

Alex, I'll let you know the model number when I get the results, I'm not sure offhand that mine is a match to your's.  Did your's come with some funky CD-ROM that you didn't run first like me, because it was looking a little too "Windows"-ish?  Yeah.  Meh.

Report more info when I get it guys and gals.  Thanks so much for all the replies so far!

---

### Post by Bartender on 2009-06-01
You shouldn't have to do anything with the CD if you don't want to.  The CD probably includes some handy utilities for copying Windows from an old drive to a new one, but the HDD should work out of the box without the CD.
+1 on using the stand-alone GParted partitioner.

---

### Post by raymondh on 2009-06-01
Hello Russ1982ny,

Remember that gparted will not partition anything that is mounted ... hence MarkPhelps' suggestion to use a standalone gparted disk; that or use the liveCD.

When you get a chance,  post us a screenshot of what gparted outputs.  That'll help the visualization aside from the fdisk output you already gave.

regards,

---

### Post by AE000 on 2009-06-01
> **russ1982ny said:**
> I'm at work right now, and lucky enough to be able to burn a Gparted live cd from here to use at home. Love my workplace. :-)
 
I'll be using that when I get home and reporting results here.
 
Alex, I'll let you know the model number when I get the results, I'm not sure offhand that mine is a match to your's. Did your's come with some funky CD-ROM that you didn't run first like me, because it was looking a little too "Windows"-ish? Yeah. Meh.
 
Report more info when I get it guys and gals. Thanks so much for all the replies so far!
 
Actually mine came with nothing, no CD-ROM, no cables, no screws, just a tiny silica bag :(

---

### Post by russ1982ny on 2009-06-01
Ok, so when looking through my bios, the hard drive is seen as "WDC WD3200AAJB-00J3A0".

Below are screen shots of GParted and Install in action on my system:

[IMG]http://testbed.echod.net/russ/Screenshot.png[/IMG]

There are no other available hard drives besides the USB drive in GParted.

---------------------------------------
[IMG]http://testbed.echod.net/russ/Screenshot-1.png[/IMG]
----------------------------------------
[IMG]http://testbed.echod.net/russ/Screenshot-2.png[/IMG]

The installer sees my hard drive as WDC WD3200AAJB-0.

Can anyone shed any further light on this subject?  Thank you!

---

