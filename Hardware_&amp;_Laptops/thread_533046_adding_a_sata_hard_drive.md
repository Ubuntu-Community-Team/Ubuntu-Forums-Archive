---
title: "adding a sata hard drive"
date: 2007-08-23
forum: Hardware &amp; Laptops
---

### Post by stephenjbarr on 2007-08-23
Greetings,

I have a question regarding adding a SATA hard drive as a replacement for the home directory. I have been following the instructions here:

[http://wiki.linuxquestions.org/wiki/Adding_Another_Hard_Drive](http://wiki.linuxquestions.org/wiki/Adding_Another_Hard_Drive)

To summarize, I have physically added the disk, used fdisk to create a partition, ran mkfs.ext3 to create the filesystem, mounted the drive, copied my /home to that drive, unmounted the drive. I have modified my fstab so that it reads:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b204a1a9-ad75-4e6f-bb3c-69c289e04b1e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb1
UUID=c0a975ab-b979-4e60-8e28-1d2cf9b81990 /home           ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=dfe9162d-7302-4e2c-806c-9c53223d880f none            swap    sw              0       0
#/dev/sdb1 /home ext3 defaults,errors-remount-ro 0 1

/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


However, running mount -a produces this message:

mount: special device /dev/disk/by-uuid/c0a975ab-b979-4e60-8e28-1d2cf9b81990 does not exist

I am worried that if I reboot, it will not mount and I will be left without a /home. Any help in resolving this issue would be much appreciated.

Thank you,

-Stephen

---

### Post by ajgreeny on 2007-08-23
Have you checked the uuid of the disk?  There doesn't seem to be any other reason for it not to mount.  How about using just the /dev/sda5 instead of the uuid in the fstab as it always used to be?  OK It may not work either but I'm just trying to think of anything that may help out.

---

### Post by stephenjbarr on 2007-08-23
well, I am fairly certain that the UUID is right. Running blkid gives:

/dev/sda1: UUID="b204a1a9-ad75-4e6f-bb3c-69c289e04b1e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="dfe9162d-7302-4e2c-806c-9c53223d880f" 
/dev/sdb1: UUID="c0a975ab-b979-4e60-8e28-1d2cf9b81990" SEC_TYPE="ext2" TYPE="ext3" 

I tried your suggestion about putting it in fstab as /dev/sdb1 and that seemed to work. I will reboot and hope for the best. Thanks.

-Stephen

---

### Post by ajgreeny on 2007-08-23
I hope it worked on boot-up.  I see no reason why it shouldn't as I have added lines to my fstab using just the /dev/hdXX naming in a new install of linux mint (based on ubuntu) and that certainly worked.  OK, it was only a test to check it out with a windows partition, but that did work, no problem.

I am a bit baffled as to the advantages of the uuid in something like the fstab, no doubt there are some, but if so, I'd love to know what they are;  it just seems to make things more difficult to me if you get things slightly wrong.  Also I note that the uuid is different for the same partition in each of the OSs I have installed, which makes things even more difficult.

---

### Post by stephenjbarr on 2007-08-23
Well, it worked, so I'm glad. I read somewhere that UUID is easier to manage in larger environments, but it is nice that the old system works too.

Thanks again for all your help.
-Stephen

---

