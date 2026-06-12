---
title: "autoFS strange behavior?"
date: 2007-02-03
forum: Hardware &amp; Laptops
---

### Post by drs305 on 2007-02-03
I am a Linux newbie. I installed autofs per the instructions at [http://greenfly.org/tips/autofs.html](http://greenfly.org/tips/autofs.html) and got it to work with my USB flash/thumb drive. I could enter "ls /var/autofs/removable/usbdrive" and watch the drive appear for 5 seconds and then disappear.

I've noticed several things that I have me questioning whether I have autofs working correctly.  The usb drive is /dev/sda1. I have removed all mention of it in fstab, but when I boot it still auto-mounts from somewhere. I thought that autofs would have prevented that. If I "sudo umount /dev/sda1" autofs mounting again seems to work properly. If I put a /dev/sda1 line in fstab with a "noauto" remark then I start having problems getting autofs to work.

Also even when I have autofs working, if I remove the usb device after 10 seconds or longer I still get the warning about the potential for losing data. I thought was one of the things autofs was supposed to prevent. Is the message still there because it's true or should I be able to ignore it?


Thanks.

The auto.master entry is: 
/var/autofs/removable   /etc/auto.removable     --timeout=2

The auto.removable entry is: 
usbdrive    -fstype=vfat,uid=1000,gid=1000,umask=002        :/dev/sda1

---

