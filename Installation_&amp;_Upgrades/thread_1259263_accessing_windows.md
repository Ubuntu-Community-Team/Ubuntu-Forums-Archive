---
title: "accessing windows"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by mirana on 2009-09-06
I've been dual-booting ubuntu with windows 7 (rc) for a month now, and have fallen so in love that i convinced my friend to install it as well (ubuntu). 
Yesterday i went to his house to install jaunty jackalope (9.04). he has two harddrives, one main and one for storage (storage one is 1TB). to avoid any risks, we unplugged his harddrive with the windows (xp) partition. We then installed windows on his 20 GB partition on his storage drive. Late yesterday he called me and told me how he could not access his partition, that when trying to boot from it, he got a message saying that the partition was not a windows partition but a "media partition" or something of the like.
He sais that he has tried unplugging the ubuntu harddrive, putting the windows partition on a higher booting priority etc. but that nothing works.
He also claims that he has configured grub, but that this did not work either.
He has tried a windows recovery disk, but says that did not work either...
Does grub change your BIOS in any way?
I mean, i don't see how ubuntu can have changed anything during the installation; if having only the main harddrive plugged in then i thought it should boot like before the ubuntu installation...
I feel responsible for the outcome as it was i who convinced him to install it, and since i didn't do enough research about grub before the installation. 
Please help me!

---

### Post by darco on 2009-09-06
Check out this thread....[http://ubuntuforums.org/showthread.php?t=1244343](http://ubuntuforums.org/showthread.php?t=1244343)
it has good info. Also check under the User "Presence1960", he has a boot up script. Run that and post for someone to help w/your issue.

darco

---

### Post by mirana on 2009-09-08
bump, that's not it.
can someone explain exactly what grub does, btw?
i thought it only changed the harddrive...
will run script though

---

### Post by presence1960 on 2009-09-08
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

P.S. the credit for the boot info script belongs to meierfra, one of our community members.

---

### Post by dstew on 2009-09-08
> can someone explain exactly what grub does, btw?Grub is a suite of programs that is used to boot operating systems. When you install grub properly, there is a small stage1 file that goes into the Master Boot Record (MBR) of the first disk (really whatever disk you install it to, hopefully the first disk because this is the one that the BIOS will boot). The (properly installed) stage1 file has a block link to stage2 file that is somewhere in a partition. The stage2 file is a big program that actually boots the operating system.

The reason Ubuntu uses grub is that it can "dual boot" Windows and Ubuntu. The Windows boot loader can be used to dual boot, but it is more difficult to set up.

I think you should look at the suggestion of presence1960. The original installation probably failed because you removed one hard drive before you installed. In that case, the Ubuntu installer would mis-configure the boot loader, and lead to boot problems. Other problems may have been created during attempts to fix the boot problem. The boot info script will give a full picture of what the system looks like at present.

---

