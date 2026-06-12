---
title: "Help with mounting options"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by ronbrooks on 2008-01-10
I have three partitions on one drive.  After mounting the three of them only the first two show up on the desktop.  The third one will mount and can be used and shows up on the Places drop down menu but not on the desktop. 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=8db64489-2a24-44cb-9714-88eaccdc2bb7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=c91225d7-d997-4771-be9c-a19619e48b2f none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

# Mount hard drive

# /dev/hdb1
UUID=3865-15E0 /media/first vfat auto,utf8,user,uid=1000,gid=100,umask=007 0 0 
# /dev/hdb5
UUID=44AA-3544 /media/second vfat auto,utf8,user,uid=1000,gid=100,umask=007 0 0 
# /dev/hdb6
UUID=19EA-5882 /media/third vfat auto,utf8,user,uid=1000,gid=100,umask=007 0 0 

Now when I go into computer under Places I see all three drives.  In the screen shot you will see that the mounting options are different.  The one on the left works fine and is on the desktop.  The one on the right will not show up on the desktop.  I want to make the mounting option on the right to be the same as the one on the left. Could someone tell me how to do this.

---

### Post by ronbrooks on 2008-01-10
This just came to me and if anyone knows if it will work let me know.  What if I turn off the computer and disconnected the hard drive and rebooted it again.  Then turn it off again and pluged in the drive and booted it up.  Will that reread the drive and put in the right code to get all drives to load and be seen on the desktop.

Not sure if that will help it or not.  I wanted to check with someone before I did it as I don't want to mess up the drive.

---

### Post by ronbrooks on 2008-01-12
Has anyone got an answer to this. If so please make a post.  

Thank You

---

