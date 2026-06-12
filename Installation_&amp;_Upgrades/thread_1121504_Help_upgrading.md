---
title: "Help upgrading??"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by Judeth on 2009-04-10
Currently i have a dual boot of ubuntu 8.10 and windows vista ultimate. The Windows is a 64-bit version and my ubuntu is a 32-bit version.  When i ordered my ubuntu cd from [www.ubuntu.com/www.launchpad.net](www.ubuntu.com/www.launchpad.net), I thought i have ordered a 64-bit version but they sent me a 32-bit version and i didn't know it until i installed it on my system.  I want to upgrade from ubuntu 8.10 to ubuntu 9.04 when it comes available. I can't upgrade from a 32-bit to a 64-bit can I?  If i have to reinstall ubuntu from scratch i will, but i dont want to reinstall my windows installation.  I have 2 hard drives one with Windows and the other ubuntu.  How can i install ubuntu 9.04 without missing up my windows install?

---

### Post by RedSingularity on 2009-04-10
You cant upgrade to 64 bit but you can easily upgrade to 9.04 when it becomes available in a few days.  It will not mess with your windows in any way.

---

### Post by zoldiel on 2009-04-10
Though you can't upgrade from 32 bit to 64 bit Ubuntu, you can reinstall without affecting your Windows install fairly easily. 

You will need to do manual partition during the install. When it asks where to install it you will need to use manual partition to remove/format the current Ubuntu partition and then install it there. 

For a typical dual boot with guided partitioning you should have something similar to this setup:

1 ntfs partition for windows
1 swap area
1 ext3 partition for ubuntu

Simply delete the ext3, create a new ext3 (or ext4) partition using the free space, and select / as the mount point.

Edit: Thats assuming you're using a single hard drive for both Operating systems, if using separate disks just format the one that Ubuntu is on and install as you did originally.

---

### Post by Judeth on 2009-04-10
If i delete the ext3 and make a new one, will i have to reconfigure GRUB bootloader?

---

### Post by RedSingularity on 2009-04-10
Well it will erase the bootloader but if you are reinstalling the whole OS from the disk then the bootloader will be replaced with your fresh installation.

---

