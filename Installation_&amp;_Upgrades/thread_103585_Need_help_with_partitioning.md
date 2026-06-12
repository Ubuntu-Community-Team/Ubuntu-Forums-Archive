---
title: "Need help with partitioning"
date: 2005-12-14
forum: Installation &amp; Upgrades
---

### Post by Nancy on 2005-12-14
Hi.

I am installing Breezy on a hard drive that briefly had Redhat release 4 on it.  I do NOT want to keep anything that is on the drive (in fact, I need to ensure that RH is completely off), and do not need to dual boot.  It is all for Linux.

During install, there is a Partition Disks screen that looks like this:

IDE1 master (hda) - 160.0 GB WD1600JB-00GVA0
       pri/log 160.0 GB   FREE SPACE
LVM VG Ubuntu, LV root -153.4 GB Unknown
       pri/log 153.4 GB   FREE SPACE
LVM VG Ubuntu, LV swap_1 -6.4 GB Unknown
       pri/log 6.4 GB   FREE SPACE

What do I do from here?  If someone could provide an example of what this screen will look like after configuring the partitions, that might help a lot.  

As for swap, this is an engineering workstation with 2GB memory, and it could run computations that fill memory.  How to configure swap?

All help appreciated, thank you very much.

Nancy

---

### Post by Zelut on 2005-12-14
It looks like you're at the first option in the partitioning screen.  It gives you options to partition in the default or the LVM options.  I have always done the default option & then it should have an option of 'auto partition free space' (or something similar).  That will create your / & swap partitions for you, which can be manually edited to extend the size of each.

Poke around a little and try some settings.  It sounds like you don't care about losing information so it can't hurt to tinker around until you find the method.  If you're still stuck come on back &/or try live help on IRC @ #ubuntu (irc.freenode.net)

---

### Post by Nancy on 2005-12-14
Thanks for your reply.  I've done a lot of tinkering already and have gotten errors every time I select "Finish partitioning and write changes to disk."  And no default was offered, at least not anymore.  But your answer made me think to reboot (duh) and then it offered a default:

IDE1 master (hda) - 160.0 GB WD1600JB-00GVA0
       #1 primary 255.0 MB ext3 /boot 
       #5 logical 159.8 GB lvm
LVM VG Ubuntu, LV root -153.4 GB Unknown
       #1 153.4 GB ext3
LVM VG Ubuntu, LV swap_1 -6.4 GB Unknown
       #1 6.4 GB swap swap

So far this is working, thank you so much.  Base system is installing as we speak.  

I did try to change the swap from:
LVM VG Ubuntu, LV swap_1 -6.4 GB Unknown
       #1 6.4 GB swap swap

to this:
LVM VG Ubuntu, LV swap_1 -6.4 GB Unknown
       #1 2 GB swap swap
       #2 2 GB swap swap
       #3 2 GB swap swap

but ended up with 
LVM VG Ubuntu, LV swap_1 -6.4 GB Unknown
       #1 2 GB swap swap
         4.2 GB unusable
so went back to the default.

Isn't 6.2 GB of swap in one chunk a bad thing?  How can I change it later?

Nancy

---

### Post by Zelut on 2005-12-14
...as far as your swap 'being in one chunk' I don't know how else to do it.  As far as I know the /swap has always been one continuous partition..

Hope things install well for you.  The partitioning is always the confusing/difficult part but everything else should be a 'Breeze' :)

---

### Post by roelofs on 2005-12-28
> Isn't 6.2 GB of swap in one chunk a bad thing? How can I change it later?

It's probably too late now, but you could always create one 2 GB swap partition and a pair of 2 GB ext3 partitions (e.g., "/future1" and "/future2"), then go back and convert them to additional swap partitions later (umount, remove from fstab, mkswap -c /dev/hdXY, add to fstab [i.e., copy/modify existing swap line], reboot or swapon, done).

---

### Post by Nancy on 2006-01-09
Thank you all for the replies.  I restarted the installation and that got me back to a list of defaults.  Accepted those and all went smoothly then.  Thanks again.

---

