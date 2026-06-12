---
title: "dual boot issues"
date: 2009-08-08
forum: Installation &amp; Upgrades
---

### Post by audichris on 2009-08-08
I am currently running a dual boot with Ubuntu 9.04 and windows vista sp1. A while ago my roomie tried to recover data off an old hard drive with a second running copy of vista already on it. and of course grub loader gets wiped out. so i take the hard drive out run supergrub to get back into ubuntu. reinstall grub thru terminal and all is well with ubuntu but now vista bootmgr is wiped out. so i bust out the good ol vista dvd and restore bootmgr. Buh bye grub. soooooooooooooooooooo........... What the F@#% do i do?

---

### Post by Herman on 2009-08-08
If that was happening to me I would re-install GRUB with my Super Grub Disk and boot Ubuntu
Then I would run a command like 'sudo blkid' or 'sudo fdisk -lu' in a terminal, or open Gnome Partition Editor to see what disk and partition Windows is in. 
Usually, Windows is in /dev/sda1, but if there's a recovery partition there, it could be /dev/sda2 or it could even be some other /dev/ number altogether.
Armed with that information, I would open my /boot/grub/menu.lst file in Ubuntu and edit it with an entry for booting my Windows installation.

A typical Windows booting entry might look something like this, 
```
[title]("http://members.iinet.net.au/%7Eherman546/p15.html#windowstitle")        Microsoft Windows XP Home Edition
[root]("http://members.iinet.net.au/%7Eherman546/p15.html#root_or_rootnoverify_")        (hd0,0)
[savedefault]("http://members.iinet.net.au/%7Eherman546/p15.html#savedefault_")
[makeactive]("http://members.iinet.net.au/%7Eherman546/p15.html#makeactive")
[chainloader    +1]("http://members.iinet.net.au/%7Eherman546/p15.html#chainloader_1_")
```Where: '(hd0,0)' is the GRUB equivalent of the /dev/sdx,y disk and partition number for my Windows installation, for a conversion table, refer to [A Quick Guide to GRUB's Numbering System]("http://members.iinet.net.au/%7Eherman546/p15.html#A_Quick_Guide_to_Grubs_Numbering_System").

If you need help, please post your 'sudo blkid' or 'sudo fdisk -lu' output and I or someone else here will help you.

Regards, Herman :)

EDIT: You can replace the words 'Microsoft Windows XP Home Edition' with 'Microsoft Windows Vista SP1' or whatever you like after the 'title' command.

---

