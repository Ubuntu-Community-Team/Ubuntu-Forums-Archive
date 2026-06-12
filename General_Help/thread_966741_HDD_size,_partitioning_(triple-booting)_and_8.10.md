---
title: "HDD size, partitioning (triple-booting) and 8.10"
date: 2008-11-01
forum: General Help
---

### Post by RequinB4 on 2008-11-01
Right now i have a box that dual boots 8.04 and Vista.  I can't remove vista because there are a few technical windows-only programs I have licenses for.  I want to install 8.10 but with a clean install - not an upgrade from 8.04.  I don't really care if I have to install a bunch of programs afterwards.

Is is possible to triple boot, and if so is there anything I need to know besides shrink to an appropriate size?

How much can I shrink vista's partition and render it usable?  I don't store data on vista.

If I triple boot, can I set it up so 8.10 and 8.04 share a /home?  Right now 8.04 doesn't have a seperate /home, so how can I do that? 

To see if I have enough space, how can I figure out how much space is on my HDD without a partitioner (or do i just have to open GParted?)

Much appreciated, as this is my main computer with all of my stuff.

---

### Post by prshah on 2008-11-01
> **RequinB4 said:**
> 
Is is possible to triple boot, and if so is there anything I need to know besides shrink to an appropriate size?

How much can I shrink vista's partition and render it usable?  I don't store data on vista.

If I triple boot, can I set it up so 8.10 and 8.04 share a /home?  Right now 8.04 doesn't have a seperate /home, so how can I do that? 

To see if I have enough space, how can I figure out how much space is on my HDD without a partitioner (or do i just have to open GParted?)


Yes you can triple boot.

I'd say 30 Gb is about enough for Vista; depends on the "technical" programs you use in Windows; all in all, I'd say 1.5* recommended HDD space for your "technical" programs.

Unfortunately, 8.04 and 8.10 cannot share a "/home"; there are fundamental changes to gvfs and dbus structures (in the home directory, .gvfs and .dbus store the settings / access points)

If your partitions are mounted, you can check the disk space with the command ```
df -h
```, or you can run ```
gnome-system-monitor
``` from the Alt+F2 command box, and click on the File Systems tab.

---

### Post by TeXtonyx on 2008-11-01
Start->Click on My Computer. Then right-click on C: under hard drives,
and choose properties. It will open a pie chart which shows how much 
used space, free space, and the capacity of the drive. Another
way if you know some of this information, is open a command prompt
and type dir, C:\dir <enter> this shows how much free space is left.
So you need to figure your used space, any Vista program growth to
the used space and then add 15% to that figure or it will be slow.

Vista is best to resize the Vista partition. I also intall grub to
the boot sector of the Ubuntu /boot partition in Step 7, Advanced.
Vista in the MBR will always boot Vista if at some point you delete
the Ubuntu install which has the grub support files. You can add
Ubuntu(s) to the Vista bootloader with Easybcd. This allows booting
independently of the other OS to each OS partition; Super Grub
disk will boot Ubuntu if the Vista bootloader fails. I put all the
bootable OS on both the Vista boot menu options and the grub menu
options for backup. I've been pounded into believing in backups.
If you install 8.10 to the MBR and 8.10 fails, how would you boot
any OS even 8.04? After panic, you could download the Super Grub
disk and burn it on another computer. An ounce of prevention is
worth a pound of cure. Do you know how to fix this potential issue
with the Ubuntu live cd? I think it is easier with Super Grub.

---

