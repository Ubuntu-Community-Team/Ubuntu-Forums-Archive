---
title: "ACK! New Ubuntu Server install formatted my drives!"
date: 2009-10-05
forum: Installation &amp; Upgrades
---

### Post by oshman on 2009-10-05
Ok, I have a fairly new box and had debian 5.0 running as my server.  The basic drives were an internal 80 GB drive formatted and partitioned as swap, /, /boot and /tmp.  Then I had a second internal 500 GB drive partitioned and mounted as /home and /var/www.  A third external drive was mounted as /var/backup.

I kept having problems just getting debian configured and someone mentioned that I should try ubuntu server edition instead.  Sure, no prob.  I downloaded and burned the 64-bit version to CD and started the install.  During the install, I blew away the existing 80 GB drive partitions (only) and manually set up the partitions the same way, including activating the /home, /var/www and /var/backup partitions on the other drives, and specifically told it to *NOT* format those.  I even double checked before I hit go and verified that it was set to do not format.

Yet, when the install was finished, I jumped to another box to check my intranet and got the basic new install apache web page.  Wait a minute, maybe it didn't mount the /var/www and just went with what is standard.  Nope, mount shows /dev/sdb2 is mounted there.  Further inspection revealed that /home (/dev/sdb1) was ok.  /var/www (/dev/sdb2) was blown away and /var/backup (dev/sdc1) was also gone.

Questions:

[LIST=1]
[*]Is there anything I can do to recover from this?  It was my web site and over 1000 CDs (thank God I didn't take them all down and sell them like I planned to last week...)
[*]The backup is gone too.  I'd like to recover either sdb2 or sdc1, I can go back and rebuild the backup from one, or the web site and library from the other.
[*]Is this a bug?  It was set to not format, and yet it did.
[/LIST]

HELP!!!!  :(

---

### Post by cariboo on 2009-10-05
Give testdisk a try, it is in the repositories. I've never had the problem of the install formatting drives that weren't marked for formatting. I install newer version fairly often with out the problem you had.

---

### Post by oshman on 2009-10-05
Could the formatting drives have something to do with me entering the mount point manually as opposed to selecting one of the predefined mountpoints?  I.e. my /home partition is still whole and has no problems.  But anything I added as a manually entered mount point (i.e. /var/backup and /var/www) got formatted...

anyway.... testdisk doesn't let me recover deleted files from an ext3 partition.  There's another utility that's part of that called PhotoRec that looked promising, but (after running for over three hours) only recovered mostly partial files, and those had filenames like f12387634.mp3 and didn't recover any web-related files (i.e. html).  So the partial files aren't worth much, and the rest, without the original names and file structures, are easier deleted than trying to figure out each file, one by one...

Any other ideas?

Help?

Bueller?  Bueller?  Bueller?

---

