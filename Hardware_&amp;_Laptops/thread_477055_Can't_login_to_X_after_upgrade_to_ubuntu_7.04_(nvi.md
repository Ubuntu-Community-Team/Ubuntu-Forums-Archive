---
title: "Can't login to X after upgrade to ubuntu 7.04 (nvidia 7400)"
date: 2007-06-17
forum: Hardware &amp; Laptops
---

### Post by jutirain on 2007-06-17
i've upgraded my ubuntu from 6.10 to 7.04 last night.

my machine is vaio sz 92, which has nvidia 7400 grahpics card on it.


after the upgrade,

i got the following message and can't login to X,

i have to use normal login

error message:
===================================

Starting up ...

[ 0.310614] PCI: Failed to allocate mem resource #6: 20000@d0000000 for 0000:\
01:00.0

Loading, please wait...

kinit: name_to_dev_t(/dev/disk/by-uuidf65cf65d-3f7b-4905-a67f-81a953cdf35) = s\
da5(8,5)

kinit: trying to resume from /dev/disk/by-uuidf65cf65d-3f7b-4905-a67f-81a953cd\
f35

kinit: No resume image, doing normal login

===================================

so, is there any problem with "resume image"?


i've installed nvidia-glx-new,

when i "sudo startx"

i got only a terminal on the left-top corner, and nothing else...


somebody knows how to solve it?

or there any method to "downgrade" to my original version...

thanks a lot!

---

### Post by Gagle on 2007-06-17
>  /dev/disk/by-uuidf65cf65d-3f7b-4905-a67f-81a953cdf35) = s\
da5(8,5) 

I think this is a hard-drive problem rather than a graphics card driver problem.  Maybe try to un-mount un-necessary drives.  Could you post your /etc/fstab file.  If ithis is impossible, try to compare the uuid of the error message and those of the drives mentionned in the fstab file.

Hope it helps,

Gagle

---

### Post by jutirain on 2007-06-18
Thanks for replying, this is my /etc/fstab:

======================================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3954ae44-2744-4437-a0e9-c0530bb45952 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=f65cf65d-3f7b-4905-a67f-81a953c4df35 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

======================================

so, should i unamount /dev/sda5?

---

### Post by jutirain on 2007-06-18
It seems like a bug for 7.04.

I reference
[https://bugs.launchpad.net/ubuntu/+bug/103148](https://bugs.launchpad.net/ubuntu/+bug/103148)

And sudo apt-get install ubuntu-desktop

Now every thing is just OK.

Thanks a lot. :)

---

### Post by Gagle on 2007-06-18
No need to thank me.  You did all the work !

Happy it worked out.  You will be more than pleased with your new Desktop.  :KS

regards,

Gagle

---

