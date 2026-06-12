---
title: "A note about SCSI cdroms"
date: 2004-10-22
forum: Hardware &amp; Laptops
---

### Post by dare2dreamer on 2004-10-22
Hi all,

Recently installed Ubuntu, and am seriously impressed. Major kudos to the guys at Canonical for making a very slick distro. 

I did spot a problem regarding SCSI CD-ROMs though. Apparently, by default Ubuntu's install detects them as /dev/scd# and writes them as such to the /etc/fstab.

Problem is, according to my system they are listed in /dev as /dev/sr#

If you can't mount your cdroms automagically, change your /etc/fstab as follows:

#/dev/scd0       /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/sr0       /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
#/dev/scd1       /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/sr1       /media/cdrom1   udf,iso9660 ro,user,noauto  0       0

and everything should start working as intended.

A note to the dev's...This would be a show-stopper bug for a newbie. If I couldn't get the same cd I installed from to read anything, I'd probably cry broken and go back to that *other* operating system.  :)

---

