---
title: "ok install to existing partition or do i need to delete and start again?"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by baddt on 2009-08-09
Hello and Thankyou!

I am setting up ubuntu 9.04 as a dual boot system on my laptop following the guide at [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2)

My machine already has an existing partition on the hard drive which is mapped as D: which has 50 gig and is empty

Is it ok to install ubuntu into this drive or do i delete this drive so there is only one drive (c: ) and shrink as per the instructions?

I've had a hunt around on this site and a few others but not found any answers that i'm confident enough to try out.

Thanks in Advance

Baddt

---

### Post by wojox on 2009-08-09
I would recommend this guide instead:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by baddt on 2009-08-09
thankyou very much, I've md5checksumed the disk and ready to go so will read through it and have a go! 

Thankyou for your help

---

### Post by raymondh on 2009-08-09
> **baddt said:**
> thankyou very much, I've md5checksumed the disk and ready to go so will read through it and have a go! 

Thankyou for your help

Just a few more tips as you get ready...

-Ubuntu will not install to a NTFS partition.  That said, as you install, you may point the installation to the D: partition and format to ext3 (or ext4, if you wish) which will erase/reformat NTFS to Ext.
-Back-up your files.  There are no guarantees.
-Defrag windows first.  If time-permitting, defrag 2x.

Some more sites of interest:

[http://members.iinet.net/%7Eherman546/index.html](http://members.iinet.net/%7Eherman546/index.html)
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Good luck.

---

### Post by baddt on 2009-08-09
Thanks for all your help - I'm writing this post on my newly created dual boot vista/ubuntu 9.04 machine - thanks again! :)

---

### Post by raymondh on 2009-08-10
> **baddt said:**
> Thanks for all your help - I'm writing this post on my newly created dual boot vista/ubuntu 9.04 machine - thanks again! :)

Congratulations and happy Ubuntu-ing :)

---

