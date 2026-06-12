---
title: "Installing 9.10 (laptop remix) over ibex problem"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by mefistofeles666 on 2009-10-30
Hello everyone,

I was trying to install the new distribution of ubuntu but i ran into a problem. I installed ibex a couple of weeks ago but the internet is not working and so I decided to simply upgrade to 9.10. I downloaded the new distribution and burned it into a cd. Now, when I boot into vista and try to install the ubuntu from the live cd I only see the two partitions that vista is using (one for the os and the other one for the recovery file). But i wanted to do and was told is possible, is just install the new ubuntu over ibex in the partition where ibex is. But I don't see the partition where ubuntu is. 
I was wondering if there's anything I can do to just install over ibex, or will I have to use a partition manager to be able to see the partition and wiped it clean and reformat it?

Also, a very bizarre thing is that when I go to the install/revome software in vista, it shows ibex as a software I can uninstall  from windows  and it says the size of it is exactly the amount I allocated when I installed ibe, which I installed using daemon and the iso file from a usb drive.


thank you for your help

---

### Post by zalberico on 2009-10-30
Boot from the ubuntu disk, don't do it inside of windows.  To do this throw the disk in your computer and reboot.  On most computers the default is to boot off of the disk (you may have to set this in the bios but probably not).

If you're installing from the disk you'll be able to install over ibex.

When you get to the partition table part you're going to have to select manual configuration(advanced)

Once here find the partition that is 8.10 (it'll be formatted ext3) and delete it. (Don't touch the SWAP partition)

Next you'll just need to create one partition(set mount point to /) and use the ext3 file system.


Note: (It can be a good idea to have a separate partition for /home so that later updates keep your settings.  This is optional, but if you're interested give 15GB to / (root) and the rest to /home)

---

### Post by mefistofeles666 on 2009-10-30
I actually did what you suggested and when I get to the partition part, it only shows sda1 and sda2 which is the two windows partition.

---

