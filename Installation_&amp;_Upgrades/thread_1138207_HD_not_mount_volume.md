---
title: "HD not mount volume?"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by Cyborgoat on 2009-04-26
I am new to Ubuntu, but am decent with msXP I downloaded ubuntu 8.10 and booted from this disk I selected the run from disk instead of installing it. I am unable to read any of my 3 HDs. I am getting msg "CAN NOT MOUNT VOLUME" on all of the drives when i click on them to view them. 
 
I was having problems with my XP and was looking for something new which brought me back around to linux OS's, but this had nothing to do with the HD's. I just killed the Keyboard and Mouse Inputs.
Both work fine with Ubuntu running. 
 
Question: Can I install Ubuntu and keep my data (word,excel,msmoney,pictures,etc) what will happen to these during the installation? What is best for me to do? 
 
I read of people putting both msxp and Ubuntu on seperate partitions, is this an option? 
 
thanks,

---

### Post by Triptol on 2009-04-26
You say you had problems with XP... so the most common problem you might have with opening your disks is that Windows didn't properly unmount them.

The following might be your solution:
[LIST]
[*]Boot Windows
[*]Shut it down properly (without errors etc.). No Hibernation, no whatsoever, do a shutdown.
[*]Start the Ubuntu live disk and mount the drives
[/LIST]

If that doesn't work try the ntfsfix program available with ubuntu. I have good experiences with it, but it is a "use at your own risk" program.

---

### Post by Triptol on 2009-04-26
Trying to answer the other questions as well...

By default Windows is installed on an NTFS Filesystem. This filesystem cannot be used to install Ubuntu. Ubuntu install on a number of other filesystems that cannot be used to install Windows (except for vfat, but vfat does not support security, so you shouldn't be using it. Apart from that it is slow and old and...).

So if you want to stick to Windows you can install Ubuntu on a different partition and then your bootloader (Grub / Lilo) will give you the option which system you want to start.

Since Ubuntu can use NTFS partitions (for data!!) you can still use your office files. BUT: MS Office will not run under Linux (well not unless you are using Wine, but that is a different story), so your office files will be opened with Openoffice which is good, but not perfect.

Hope that helps. If not try a google and search for dual boot windows linux and you will probably find a LOT of information.

---

