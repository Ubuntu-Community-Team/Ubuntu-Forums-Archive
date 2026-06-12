---
title: "Uninstalling 64-bit Ubuntu while leaving other OS's intact"
date: 2006-01-18
forum: Installation &amp; Upgrades
---

### Post by pharmdad2007 on 2006-01-18
Hi,
I've searched through other topics about uninstalling, but I haven't found the answer to my question yet.  I have Windows XP, Ubuntu 5.10 32-bit, and Ubuntu 5.10 64-bit installed on my laptop.  I want to remove the 64-bit installation only, and leave the other two intact.  Can I do this simply by removing the 64-bit partition, or do I need to do something to Grub or the MBR as well?  I'm afraid to do anything without knowing first if it is going to work.  Any help would be greatly appreciated.

Thanks in advance,
Jesse

---

### Post by Herman on 2006-01-19
I don't actually have a 64-bit computer, but I'll have a guess for you since no-one experienced with 64-bit has happened along yet...
More than likely, if the 64-bit version was the last one installed, you will need to re-install GRUB. Your MBR will be pointing to GRUB on whichever Ubuntu Partition was installed last. So when that partition is gone, the MBR will be pointing nowhere useful. Re-installing GRUB will refresh your MBR to make it point to the right partition, which will now be your 32-bit version of Ubuntu.
Here are a couple of links on re-installing GRUB.
[http://www.ubuntuforums.org/showthread.php?t=114332]("http://www.ubuntuforums.org/showthread.php?t=114332")
[http://www.ubuntuforums.org/showthread.php?t=24113]("http://www.ubuntuforums.org/showthread.php?t=24113")
If the 32-bit version was the last one you installed, you will not need to re-install GRUB, but you will be left with a redundant entry in your GRUB menu for the 64-bit version which you can either just ignore, or edit your GRUB menu.lst to erase that entry.
The best partitioning software you can get is the new GParted livecd-0.1 which was just released on the 12th Jan. I have tried it out and it can easily resize even reiserfs partitions, you can use that for doing whatever you need to your partitions, I think it's great! My second 'siglink' will lead you to the .iso download site for GParted livecd-0.1. Just burn that to a CD and give it a spin, you will be impressed like I am. :D (Herman)

---

### Post by pharmdad2007 on 2006-01-21
Herman,
Thanks for your reply.  It actually turned out to be easier than either one of those possible solutions.  I simply deleted the 64-bit partition and resized the 32-bit Ubuntu partition to occupy all the empty space.  I then rebooted, thinking I would need to use the Ubuntu install disk to reinstall GRUB, but it just booted right up and GRUB started right up and correctly listed my 32-bit Ubuntu install and my Windows XP install, just as if nothing had ever happened.  Just one more reason to be impressed with Ubuntu, I guess!
Jesse

---

