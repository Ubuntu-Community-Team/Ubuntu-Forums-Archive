---
title: "Boot problem"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by yodakohl on 2009-06-08
Hi 

On my notebook i had Ubuntu and Win XP installed on two different partitions.
An error occured after updating ubuntu to version 9.04. Since i wasn't able to fix it and my cd drive is death i installed ubuntu wubi directly under windows. I deleted the old ubuntu partition ,  and thats my problem.

Grub now has an error while booting: error 22

Has anybody an idea how to fix the Master boot record?

thx for help ;)

---

### Post by torgrot on 2009-06-08
You will need to restore the windows boot record.  I believe if you have the windows CD you can use that to restore the MBR by selecting R to recover and then at the command prompt type fixmbr.  When you deleted the Ubuntu partition you removed part of GRUB that is why you get that error.  You can also try SUPERGRUB CD to do essentially the same thing.

After you get Windows to boot normally uninstall the wubi and reinstall it, as you will lose wubi after you recover.
 
I see now that you don't have a working CD, that is going to make things quite difficult.  There used to be a supergrub that ran from a floppy disk, do you have a floppy disk on your notebook?
 
 
torgrot

---

### Post by yodakohl on 2009-06-08
I just connected my notebook hard disk to my tower pc, and running it with a  ubuntu live cd. the notebook has no floppy disc.  I'm thinking about formating the whole hard disc, as i don't know if windows recovery works, if hardware changed.  Does Ubuntu has a problem if it's installed by the tower pc, and the hard disc is replaced to the notebook after the installation?

---

### Post by torgrot on 2009-06-08
Do you have a recovery CD for your laptop?  I would use the tower to repartition and format the drive using the Windows disk management software.  Then I would reinstall the drive in the laptop and reinstall windows there.  I don't think it would be a good idea to try installing UBUNTU to the drive while it is connected to the tower PC.  The drive letters would be different not to mention most of the rest of the hardware.  Do you know any one with an external USB CD-ROM drive that you could borrow?  That would be my next avenue of attack?
 
torgrot

---

