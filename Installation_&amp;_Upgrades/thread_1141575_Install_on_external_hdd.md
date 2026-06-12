---
title: "Install on external hdd"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by supersound on 2009-04-28
Hi, 
I had an install of Intrepid on an external hdd, and with GRUB located on that drive I could dual boot any PC when that hdd was attached and that PC had USB boot capability.
I cant get this to work with Jaunty though...
The way I did it with Intrepid was to use the live cd to create free space on the external, then use that free space with for Ubuntu during the install. An upgrade from Intrepid broke the install (kind of half expected that) but starting from scratch doesnt seem to work either. Any help? Has something changed in the new kernel that stops this set up working or am I just being stupid?

Thanks

---

### Post by shatterblast on 2009-04-28
I think you can expect every new reinstall of Ubuntu to possibly do that.  It would probably be feasible to use KGrubEditor from Synaptic to backup your original menu.lst file to avoid the hastle of when it decides to rebuild it.

Using free space during the install might have been accidentally assigning on occasion a separate hard drive.  What you might do instead is examine your fstab file by typing "gedit /etc/fstab" from within Applications -> Accessories -> Terminal.

I think you might look for something similar to SDA0.  You can use KGrubEditor to add a line specifically for that hard drive.  After that, you might try test if the internal hard drive will boot on the next system restart.  How ever, I don't think the settings for a Windows install will boot a Linux distribution.

An alternate option might be through trying a clean reinstall of Ubuntu.  The latest 9.04 version gives the option of whether or not to overwrite the GRUB settings.  Assuming no backup of menu.lst exists, it should be safe to look for something marked with SDA for the internal hard drive.  Otherwise if it only lists Ubuntu for the GRUB settings, there would serve no purpose in proceeding further that way.

---

### Post by supersound on 2009-04-28
Thanks shatterblast, but I cant get into Ubuntu at all now- i have tried reformatting the ext3 partition on the external and trying a fresh install, GRUB seems to start to boot Ubuntu ok but the boot fails and falls back to a shell. Not sure what to do after that.

---

### Post by shatterblast on 2009-04-28
Since you seem to be focusing on reinstallation, I would suggest taking a deeper look at the GRUB settings.  A menu for it should appear I think under an Advanced button in the bottom right a few screens after selecting what to do with the partitions.  This should be available before the final option of proceeding with the install.  I think it will have a list of items for your present computer's operating systems.  It may list Ubuntu or SDB (for USB).  You may have to adjust that to make it the primary.

---

### Post by wirechief on 2009-04-29
i used grub4dos to boot a linux distro of Kanotix the boot loader was installed in windows boot.ini it gets kind of tricky but it can be done
the menu.lst shows the .iso that is used to boot up but it becomes basically a live session from the HD however you can install from it
but dont know what the use of it would be.

---

### Post by supersound on 2009-04-30
Thanks for the suggestions, but I'm still having trouble.
Everything seems to install ok and GRUB seems to work when I boot with the external connected. I select Jaunty and loading starts, but then fails and the systems reverts to Busybox, reporting missing modules and suggesting that the install device is incorrect.
Any more ideas? I have tried reinstalling a few times, with fresh unformatted areas of the drive...

---

### Post by shatterblast on 2009-05-01
I assisted someone else struggling with a similar topic.  Before I made the suggestion, the individual found a method to create a bootable USB disk through a window called USB Startup Disk Creator.  Though it might be similar under Intrepid 8.10, it can be found under Jaunty through:

System -> Administration -> USB Startup Disk Creator

That may assist in at least trying to get Jaunty onto your USB drive.  I'm sure this can be done via a Live CD as well if that option exists.  From there, you can probably edit the GRUB settings as necessary.

---

### Post by supersound on 2009-05-05
Thanks for the suggestions. Think my problem is related to lack of support for ATI cards...
[http://ubuntuforums.org/showthread.php?t=1133931&page=5](http://ubuntuforums.org/showthread.php?t=1133931&page=5)

---

### Post by shatterblast on 2009-05-05
ATI cards will work on Linux fine.  The trouble in that area relates to the kind of drivers available.  ATI cards when supported to the maximum will out-perform nVidia cards with similar specifications.  Otherwise, ATI refuses to release drivers compatible with Linux for every card.

I guess it could be explained by saying that nVidia does a blanketing style of compatibility while ATI tends to focus on individual cards.  The difference is in the amount of tweaking probably.  How ever, nVidia can match equal performance with ATI cards when it applies specific tweaks to a named card, not just a "family" of them.  All it comes down to is the need to be careful when buying ATI cards and to express greater care when choosing an nVidia card for greatest performance.  To my knowledge, PCI-Express cards for nVidia do not have the tweaking issue so I assume neither does ATI.

So it comes down to drivers.  Open source drivers should still exist.  The easiest way is to install "envyng" from Synaptic.  From a terminal screen, you can also do:

sudo apt-get install envyng-core
sudo envyng -t

I'm not sure how a partition issue relates to graphics hardware unless the graphics was your focus in the first place.  Also, open source drivers for ATI hardware will probably prevent OpenGL gaming to some extent.  The non-free drivers should be the goal.

---

