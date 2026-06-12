---
title: "Optical Drive No Longer Recognizes Writable DVDs"
date: 2009-09-19
forum: Hardware
---

### Post by satwatcher23 on 2009-09-19
Hi,

I have 9.04 Jaunty installed by itself (kernal 2.6.28-15-generic) on an Everex PC.  Several upgrades back (7? 8?) the DVD-ROM drive used to work with burning disks (CDs and DVDs).  Now it no longer recognizes writable DVDs.  I just used this drive to load Jaunty from scratch, hoping a fresh install would fix the problem, so the drive is at least partially functioning.  I've searched this forum, reading all the other problems folks have had with drives not automounting but haven't been able to figure this out.  

The drive shows up in /etc/fstab:

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

When I insert a DVD recorded on another drive I get it automounted:

/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=ken)

When I insert a new recordable CD-R it opens the "Blank CD-R Disc" window, allowing it to be burned to although I don't see it show up on the mount list.

However, when I insert any new recordable DVD (-R, -RW) nothing happens.  When I try to burn a disk in Brasero it tells me to "Please insert a recordable CD or DVD if you don't want to write to an image file".  

This used to work in previous Ubuntu builds but failed a couple of upgrades back (sorry, can't remember which one).  Any ideas on what I can try to further diagnose this?  It's getting annoying to keep building ISO's and then moving them to another machine via thumb drive or my network just to burn the disks.

Thanks much!


Ken

---

