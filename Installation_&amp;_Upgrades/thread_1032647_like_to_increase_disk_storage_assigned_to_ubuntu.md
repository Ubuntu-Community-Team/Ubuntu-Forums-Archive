---
title: "like to increase disk storage assigned to ubuntu"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by terry@softreq.com on 2009-01-06
I currently have Ubuntu installed "dual boot" configuration with Windows XP.

When I first set up Ubuntu I only allocated 5gb's. 

However, I've since upgraded my laptop hard drive and would like to allocate 20gb's to Ubuntu.

Any way I can do this without having to uninstall / reinstall Ubuntu?

Thanks, Terry

---

### Post by theinnercityhippy on 2009-01-06
Do you still have a live CD kicking around? If so, boot your computer from it and run gparted;

System > Administration > Partition Editor

This will allow you to resize and move your partitions in a graphical environment. Be aware that this may take a while to complete so make sure your laptop is plugged in to the wall before you start as any power outage may irrepairably damage your partition table. 

Hope this helps, send me a message if you need any more help

-JimDog*-

---

### Post by terry@softreq.com on 2009-01-06
I used Wubi to install Ubuntu. 

The CD drive doesn't work on this laptop unfortunately.

Any way I can run Gparted other than via CD?

---

### Post by theinnercityhippy on 2009-01-06
> **terry@softreq.com said:**
> I used Wubi to install Ubuntu. 

The CD drive doesn't work on this laptop unfortunately.

Any way I can run Gparted other than via CD?

Ah. Oh dear, I'm not a fan of Wubi for this reason but not to worry, its still possible as stated in this guide

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

In the troubleshooting section, near the bottom is instructions for doing this using a program called LVPM (Logical Volume Partition Manager) which can be found here

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

It also gives instructions for moving the entire installation to its own dedicated partition which i would definately recommend doing as you will be able to use a more linux compatible filesystem, thus avoiding problems when the drive needs to be defragmented. If you are looking to resize, you may find that now is a good time to consider it.

Additional support regarding Wubi can be found here

[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)


Good luck and I hope this helps

-JimDog*-

---

