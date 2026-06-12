---
title: "Creative partitions or force drivers early on boot 500MB HD+FlashDrive"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by volkswagner on 2009-04-08
Hi and thanks for looking.

I am trying to perform an install on a WebDT 366.  It has and internal flash drive /dev/hda which is 512MB.  I also have a 4Gig CF card installed.  Problem is BIOS limitations don't permit booting directly to the flash drive.  I have the GX533 Model mentioned [here]("http://www.windowsfordevices.com/articles/AT8663689368.html").

I have tried to partition the internal drive with /boot and /swap and put / on the CF.

The problem is I get to the boot splash an than it just hangs.

My theory is I either need to force the drivers required to see the CF slot early in boot process, or I need a better partition scheme.

Perhaps if I put / on the internal drive and add several partitions to the CF to contain things like /etc, /var, /usr, /home, etc.  I did not want to dice up the CF too much.

As it is now The Mythbuntu install I tried is occupying about 1.5Gig of disk space.

The unit has 256Meg ram.  Where is the best place to put /swap?  I am guessing the CF would be better because it is easier and probably cheaper to replace.

What do you think would be the best way to setup for such a small boot device?

---

### Post by volkswagner on 2009-04-09
Anyone have an Idea?

What folders need access right off for boot?

I am not sure if I have just a botched install or bad grub setup.  I have tried the various methods to install grub.  I manually edited the menu.lst file, after manually copying grub folder contents from the /i386 on the cd.

I now get the grub menu list on boot, but still get file not found.

My partitions are as follows:

        Internal Flash drive IDE hd0,0
/    523MB


        Compact Flash Card
/swap     512MB
/usr     1500MB
/var      400MB
/home    remainder of 4GB disk

I had to make my own menu.lst, because all my attempts to install grub manually, reported writing to menu.lst, but the file was never there.  So I copied a menu.lst from another machine, and edited supplementing kernel information from my /boot folder.

I tried editing menu.lst with the UUID found in /etc/fstab on my / partition.  Still got error 15 file not found.

I then edited /etc/fstab and changed UUID to /dev/hda, which still give me file not found.

---

