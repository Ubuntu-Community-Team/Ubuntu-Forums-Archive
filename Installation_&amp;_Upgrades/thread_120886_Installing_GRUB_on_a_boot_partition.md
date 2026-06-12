---
title: "Installing GRUB on a /boot partition"
date: 2006-01-23
forum: Installation &amp; Upgrades
---

### Post by xeraph on 2006-01-23
I have a Thinkpad T43 with an 80 GB hd. I want to dual boot xp and Ubuntu and  not wipe out the Access IBM button functionality so that I can still access the recovery menu at startup. My desired partition setup is:
[HTML]
#1   primary   25.0 GB   ntfs   /media/sda1
#4   primary   98.7 MB   ext3   /boot
#6   logical   24.4 GB   ext3   /
#7   logical   1.1 GB    swap   swap
#5   logical   25.0 GB   fat32  /shared
#2   primary   4.3 GB    fat32  /media/sda2  (the IBM recovery partition)
[/HTML]
I decided to just make a separate /boot partition and install GRUB on its boot sector rather than in the MBR so that I do not overwrite the Access IBM startup menu. I'm not familiar with GRUB, or even how bootloaders exactly work in general, but since the Ubuntu installer only allows one partition to have its bootable flag set to ON, in my case I assumed that that one partition should be my /boot partition. When i opted to not install GRUB on the MBR, it then asked where I wanted to install it. With my given partition setup, what address would I type in?

---

### Post by lha on 2006-01-24
If your computer isn't old, you shouldn't need a separate boot partition. (Older bioses cannot boot from partition that is beyond ~8 GB boundary. In this case youd need to put /boot partition in the beginning of your disk.) You can install Grub to the boot sector of Ubuntu's root partition. If you decide to go without dedicated /boot, make Ubuntu's root a primary partition. If you have some other reason to have separate boot, then do it. Usually it's easier to have /boot on root partition.

[QUOTE=xeraph]#1   primary   25.0 GB   ntfs   /media/sda1
#4   primary   98.7 MB   ext3   /boot
#6   logical   24.4 GB   ext3   /
#7   logical   1.1 GB    swap   swap
#5   logical   25.0 GB   fat32  /shared
#2   primary   4.3 GB    fat32  /media/sda2  (the IBM recovery partition)[/QUOTE]

If those numbers are linux.style partition numbers, you'd want to install grub to /dev/hda4 or (hd0,3). You'll have to find right partition from partitioner.

---

