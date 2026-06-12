---
title: "Installation and dualboot help"
date: 2008-11-15
forum: General Help
---

### Post by Dr.Suse on 2008-11-15
im still somewhat new to ubuntu. i tried to install winxp and ubuntu on my laptop. i installed winxp on a 20gig partition and it booted fine and everything. then i tried to install ubuntu and use the "use the rest of the free space available" option when installing. it installed, but when i boot ubuntu up from the grub menu, it hangs on the pinkish-orange screen, or sometimes it will just be white letters on a black screen all going crazy and then it wants me to login as if at a dos shell. so i figured i fcked up somewhere.

can i reinstall ubuntu OVER the existing ubuntu or do i have to fix my MBR, erase the two partitions created by ubuntu and start all over?

---

### Post by ub007 on 2008-11-15
When you install ubuntu after the XP installation,the Ubuntu grub overwrites the MBR & to make things easier it automatically adds the boot stanza for the XP boot up in /boot/grub/menu.lst......

So if you have windows XP on the first primary partition (hd0,0) and then as you say ubuntu on the next partition,it should be set up for dual boot without much hassles and no fixing of MBR is needed.

> use the rest of the free space available" option 

Personally,i wouldnt use that option,rather would manually set the required partions..

Cheers
david

---

### Post by ajgreeny on 2008-11-15
Can you still boot into windows, you don't say?
You could just overwrite the install but lets see if we can get you up and running first.  What hardware do you have, particularly your graphics card, as it sounds as if there is a problem with that, or at least with its ability to give you a proper GUI.  It may also be worth looking at the output of the command ```
sudo fdisk -l
```(that's a lower case L at the end, not a 1) after logging in at the command line, if that's all you can get.  It will give us more detail of your partition layout on the disk, though it sounds as if the install went OK.

Lastly, and perhaps I should have started here, is the CD OK?  Do a check on that before you try installing a second time.  Check the iso file you downloaded has the correct md5sum by booting the live CD, mounting the partition where the iso file is and then navigating to the folder containing the file and running ```
md5sum ubuntu-8.10-desktop-i386.iso
```changing the file name to whatever the full name is. Also choose Check CD at the menu that appears when you boot the live CD to see if that is OK.

---

### Post by Dr.Suse on 2008-11-15
thank you both for your responses and your suggestions, im away from my problem computer at the time, and i will get back to you tonight after work.
notice; the livecd seems to work without problem and i have checked the hash of the iso before burning it, also burned at 1x and my hardware is compaq presario v5305wm with some ati gcard, it has the standard hardware: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00783092&lc=en&cc=py&product=3231960](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00783092&lc=en&cc=py&product=3231960)

edit:
i CAN boot windows at the grub menu, i figured if i *WAS* to start the installation all over again, i would have to fix the MBR of the windows partition so that the ubuntu installer would write a correct grub where windows would be able to boot again. my essential goal is to get rid of windows entirely where i would use wine if i couldnt find an alright linux alternative or use virtualbox with a winxp VM if i *had* to... but getting ubuntu is my first step, lol

---

