---
title: "Remove Windows from dual-boot system"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by mclark on 2009-09-11
Greetings,
 
I am completely new to Ubuntu 9.04 (and all things *nix - but I want to learn)*.
 
I have an old Win2000 box with a small (20Gb) drive.  I created an install CD from the Ubuntu website and created a dual-boot machine (which works).  The Ubuntu installation partitioned the drive into Windows and Ubuntu partitions (unfortunately I choose a really small partition size for Ubuntu - 4Gb).  With the limited playing I've done with Ubuntu, I want to remove Win2K and it's partition and just use the machine as a linux box.
 
Since there is no data I need on this machine I would like to:
[LIST=1]
[*]remove Win2k
[*]recover the 16Gb partition Win2k was using and make the entire drive available to Ubuntu
[/LIST]I thought about uninstalling Ubuntu and removing it's partition and then reinstalling, telling it to use the Windows partition.
 
Or try to repartition the drive into a single partition which would, by default, remove Ubuntu, then uninstall Windows and install Ubuntu.
 
Before I tried any of this I thought it would be prudent to ask the experts.  Any suggestions?
 
 
* I'm a Windows / OS-neutral programmer by trade so I have general computer OS knowledge but virtually no Unix/Linux/Mac experience.  I would really like to turn my old Win2k box into a Linux learning tool and maybe become Windows free in the future.

---

### Post by creiss on 2009-09-11
Try gparted (google for it). Its an ISO (cd) based linux that you can use to resize your partitions. This is exactly what you want to do: Move space between partitions without losing data.

-Chris.

---

### Post by Ellaine on 2009-09-11
Any hard drive manufacture has a Disc Manager program available. Download any one of these and blank the entire 20GB drive. Now load Ubuntu 9.04 and use the entire drive.

---

### Post by louieb on 2009-09-11
Gparted (run from a live CD) can delete the windows partition and resize the Ubuntu partition.

But a reinstall using the whole disk option will be faster and easier.

---

### Post by mclark on 2009-09-11
Thanks for all the suggestions.
 
I'll start by checking the BIOS to make sure I can boot off of the CD. If not I'll have to create a boot floppy so the Ubuntu install CD can be read after wiping the HD - it's a really old machine and I'm not sure the BIOS offers CD-booting.
 
Then, wipe the drive and reinstall from my Ubuntu CD and let it handle all the partitioning etc.
 
Hopefully my next post will be asking **real** linux questions.
 
I'm glad to be a member of such a supportive community. Thanks again!

---

### Post by oboedad55 on 2009-09-11
> **mclark said:**
> Thanks for all the suggestions.
 
I'll start by checking the BIOS to make sure I can boot off of the CD. If not I'll have to create a boot floppy so the Ubuntu install CD can be read after wiping the HD - it's a really old machine and I'm not sure the BIOS offers CD-booting.
 
Then, wipe the drive and reinstall from my Ubuntu CD and let it handle all the partitioning etc.
 
Hopefully my next post will be asking **real** linux questions.
 
I'm glad to be a member of such a supportive community. Thanks again!

If you've just installed Ubuntu and have no customization, etc. I'd recommend just doing a clean install and using the whole hard rive. If you have stuff you want to keep them you can follow the suggestion of using gparted and resizing your partition. Then if you want you can edit the menu.lst and remove the Windows entry so you'll only have Ubuntu listed as the OS. It's easy to do and not as daunting as it may seem!

---

