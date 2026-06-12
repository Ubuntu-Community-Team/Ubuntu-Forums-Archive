---
title: "Problem Automounting Areca ARC1224 Raid Partion on Reboot"
date: 2014-12-20
forum: Hardware
---

### Post by resman75 on 2014-12-20
[SIZE=2][FONT=arial][/FONT][FONT=arial]Hello all and let me thank everyone in advance for any advise/suggestions with my problem. 

So let me explain from the beginning, I'm transitioning from FreeNAS 9.2.1.8 to Linux ubuntu flavored distros for management of my media server so that I can do other various things with my PC besides just hosting Plex Media Server. I have an Areca ARC-1224-8i Raid Controller that I've mounted onto mobo Gigabyte GA-*970A*-*D3P, 16gb ECC ram and AMD 8320 CPU. *At this very moment I'm running Mint 14.1 that upgraded to release 17 with kernel 3.5.0-51-generic. I've also run this entire procedure on both the latest versions of Xubuntu 64bit and Mint 17.1 with the same exact issues.
[/FONT]
[FONT=arial]I followed the following guide I found here on ubuntu forums[http://ubuntuforums.org/showthread.php?t=1882611&highlight=areca](http://ubuntuforums.org/showthread.php?t=1882611&highlight=areca) in order to build the drivers for the raid controller. This worked exceptionally well and the card is now listed when I run "blkid and parted -l." I created a share folder located under my home directory /home/plex/NAS and then I run sudo mount -a to test out the share. All works well when manually mounting the 22tb partion, I can create sub folders that are then accessible from the latest Plex build I installed. My only problem with all this is when I modify "/etc/fstab" to automount the share upon reboot. I added the following entries to fstab: **UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxx /share/plex/NAS ext4 defaults 0 0** and then removed the line and used **/dev/sdb1 /share/plex/NAS ext4 defaults 0 0** with the same exact (excuse my french) f*&%ing results. So this is what happens after saving the fstab and rebooting, [COLOR=#222222]***The disk drive for /home/plex is not ready yet or not present. Continue to wait, or press S to skip mounting or M for manual recovery**!!!!!!!!. *I press S to get back to the desktop and then remove the line from fstab, save and exit. I manually remount the partion with "sudo mount -a" and everything is back to normal.[/COLOR] What am I doing wrong, this is driving me insane and if I cant fix it I will resort to deleting the raid array and moving back to FreeNAS 9.3 ZFS even though I want to stay with Linux. Anyone have an answer or suggestions please let me know. If you require additonal information from me please ask. My experience level with Linux is so-so probably step after noob...:( [/FONT]


[/SIZE]

---

### Post by resman75 on 2014-12-30
So I take it no one has ever run into this issue before, no words of advice anyone......

---

