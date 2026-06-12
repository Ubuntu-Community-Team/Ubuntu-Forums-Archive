---
title: "How  can i reformat an ubuntu os in my hardisk"
date: 2008-08-28
forum: General Help
---

### Post by mytchmatch on 2008-08-28
Hi! I am really new with  ubuntu. i used to used windows xp. however out of curiosity, I tried to install ubuntu. Im supposed to make dual OS in my  pc  but unfortunately I erased my xp...

I wanted to reformat  my  computer  and  install xp and ubuntu so that i could  have both. I tried to install xp but i found out that the setup.exe is not working in ubuntu and  gnome...
anyway  what  should  i do?
what are the steps i need to do?
how  can i clear/reformat my harddisk using ubuntu so that i could have dual OS?
hope  you can help me...[http://ubuntuforums.org/images/icons/icon8.gif](http://ubuntuforums.org/images/icons/icon8.gif)
[http://ubuntuforums.org/images/icons/icon4.gif](http://ubuntuforums.org/images/icons/icon4.gif)

---

### Post by winbutu on 2008-08-28
> **mytchmatch said:**
> Hi! I am really new with  ubuntu. i used to used windows xp. however out of curiosity, I tried to install ubuntu. Im supposed to make dual OS in my  pc  but unfortunately I erased my xp...

I wanted to reformat  my  computer  and  install xp and ubuntu so that i could  have both. I tried to install xp but i found out that the setup.exe is not working in ubuntu and  gnome...
anyway  what  should  i do?
what are the steps i need to do?
how  can i clear/reformat my harddisk using ubuntu so that i could have dual OS?
hope  you can help me...[http://ubuntuforums.org/images/icons/icon8.gif](http://ubuntuforums.org/images/icons/icon8.gif)
[http://ubuntuforums.org/images/icons/icon4.gif](http://ubuntuforums.org/images/icons/icon4.gif)

Hello, im new as well and i asked a very similar question, check it out;
[http://ubuntuforums.org/showthread.php?p=5679005#post5679005](http://ubuntuforums.org/showthread.php?p=5679005#post5679005)

---

### Post by ladr0n on 2008-08-28
What you want to do is first boot from the Ubuntu live cd.  Go to System -> Administration -> Partition Editor and select your hard drive from the drop-down list at the top right.  Delete all of the partitions on the disk (make sure you have any important data backed up before you do this) and then create two new partitions, one of which should be type FAT32.
Put in your Windows XP install disk (this won't work with a restore disk; you need the actual install disk) and install Windows on the FAT32 partition (use windows to change it to NTFS if you like).
Now that Windows has been sucessfully installed, put in the Ubuntu live cd and reboot.  Select "install Ubuntu" from the menu, and when you get to the partitioning part, create your /, /home, and swap partitions in the non-windows section.  Proceed with the install, and on reboot you should be able to choose which OS you want to boot.

---

### Post by ajgreeny on 2008-08-28
Just to reiterate what ladrOn said, when you get to the partitioning part of the Ubuntu install, having first reinstalled winXP, choose Manual.  Assuming winXP has gone onto the first fat32 or NTFS partition (sda1) you will want to install Ubuntu into the second partition (sda2).  Here is where you can choose to make the separate /, /home and swap partitions, or just let Ubuntu set the system up by itself, but make sure that sda1 is left untouched and is not formatted again, and that you use only sda2, or you will lose your winXP a second time.

---

