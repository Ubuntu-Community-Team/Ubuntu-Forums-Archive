---
title: "How to remove a partition containing Ubuntu"
date: 2009-10-03
forum: Installation &amp; Upgrades
---

### Post by michaelpanderson on 2009-10-03
I have a laptop with Vista. I bought a bigger, faster hard drive, created two partitions, followed some instructions to create dual boot capability, installed Ubuntu and restored Vista. (I don't remember which order.) So now I have two partitions, one with Vista; one with Ubuntu. I apparently have TWO boot managers. The first one to appear defaults to booting Ubuntu, so I have to scroll down to select a boot of Vista. Then I get the second boot manager, which defaults to Vista. I have to go through this every time I restart my laptop.
 
Since then, I have installed Ubuntu on my old hard drive. So I would like to remove Ubuntu and the boot managers and the second partition from my new hard drive. 
 
Is there some way, could "delete" the 2nd (Ubuntu) partition and merge it into the first (Vista) partition? If eliminating that partition is very difficult, can I at least remove or disable the first boot manager. What alternatives do I have?
 
Thanks a lot

---

### Post by Gmr Leon on 2009-10-03
You said you didn't have the Vista installation disc in the other thread, correct? In that matter, I'm unsure of how you would deal with the boot manager issue, as at least in XP you have to run the installation disc and run some commands to restore the original XP boot manager. 

As to merging the Ubuntu partition into the Vista partition, I'm not sure what file system Vista uses, but it should be a matter of running the Ubuntu Live disc, using Gparted (should be under System>Administration>Partition Editor), selecting the hard drive, or, partition in question, and then formatting it into whatever file system Vista recognizes. I imagine it would be NTFS, but that's only from my experience with XP.

---

### Post by river226 on 2009-10-03
The best thing to do is to go into Disk management in vista, cause windows in general doesn't like a sudden change in HD space... 
here is a basic guide:
[http://www.bleepingcomputer.com/tutorials/tutorial116.html](http://www.bleepingcomputer.com/tutorials/tutorial116.html)

---

### Post by presence1960 on 2009-10-03
Two things. 

1) exactly what is it you want to do? Do you want to fix the boot problem or do you want to uninstall Ubuntu? Please be more specific.

2) Before you go messing with partitions, if you want to try to fix what you have now do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

