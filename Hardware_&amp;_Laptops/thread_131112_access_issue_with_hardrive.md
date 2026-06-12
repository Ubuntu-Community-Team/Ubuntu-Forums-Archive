---
title: "access issue with hardrive"
date: 2006-02-15
forum: Hardware &amp; Laptops
---

### Post by otetiani on 2006-02-15
I am trying to find info on permanently allowing access to my second HD partitions.  Right now I have to give access each time I boot using the Disc-Admin.

I assume it is already mounted, but don't know how to change the permissions and access points.  I looked for about 40 minutes at many posts and couldn't find something that is similar to what I need.

Also, other than browsing the forum, and my Linux Cookbook, is there anything out there I can read/browse that will help me learn more about manipulating Linux as a beginner?

I am very new to Ubuntu (and Linux) so any pointers would be great.

---

### Post by john_spiral on 2006-02-15
check out:

[http://ubuntuguide.squarecows.com/doku.php](http://ubuntuguide.squarecows.com/doku.php)

have a look at the windows section, How to mount Windows partitions (NTFS) on boot-up....

caio

John

---

### Post by otetiani on 2006-02-15
Thanks, that worked for my vFat partition, but what about my ext3 partitions?

here is what I have in fstab:

[SIZE="2"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/sda1       /media/sda1     ntfs    defaults        0       0
/dev/sda5       /home/otetiani/ext3sd5            ext3    defaults 0       0
/dev/sda7       /home/otetiani/ext3sd7            ext3    defaults 0       0
/dev/sda6       /home/otetiani/vFatsda6            vfat    iocharset=utf8,umask=000              0       0
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0[/SIZE]

---

### Post by otetiani on 2006-02-15
Oops, found my own mistake.  I had typos in both of the ext3 partition mount points.  I had /ext3sd5 instead of /ext3/sd**a**5.

Thanks for the guidance and the help guide.

---

