---
title: "How to uninstall  Ubuntu 8.10?"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by dubika on 2009-03-09
I have started playing with Ubuntu few days ago.:D

I have installed Ubuntu 8.10 on the same disk with Win XP Pro (both boot OK. This HD is 250GB). Later decided to add new HD (1TB) to my PC, and installed again there. Works OK, just having some problems with printing.

I'd like to clean first installation to have more space for my Win XP. Couldn't find anything usable in manual how to do that.

PC: HP xw4600 Workstation, 4GB RAM

Thanks for any help,
dubika

---

### Post by lindsay7 on 2009-03-09
Did you install under window or a dual boot. If you did the dual boot, during the install it should have given you the option to set up the partition size for windows and Ubuntu, If you set it up with the dual boot it will be messy to try and change the partition size now and there is a chance you could mess up windows and or Ubuntu.

---

### Post by Neo_The_User on 2009-03-09
Open up a terminal and type in sudo fdisk /dev/sda (or whatever your hard drive is)

type "p" without quotes and then hit enter. It will list all the partitions on your hard disk. press "d" without quotes and hit enter and hit the numbered partition you would like to delete.

Option 2:

Open up terminal and type in sudo cfdisk

Delete your partition(s) you would like to have removed. Now hit the right directional arrow on your keyboard and select write. It will ask yes or no. type yes and then press enter.

Option 3: use gparted:

sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install gparted

gksudo gparted

delete your partition(s) you would like to have removed. beware any of those 3 options will result in your linux data to be completley removed and if you select the wrong partition, your windows partition(s) will be messed up.

---

### Post by lindsay7 on 2009-03-09
Neo, I am learning Ubuntu form reading so I always have question,
If he deletes the partition, will not the grub file still be on this machine.  Will that present a problem if he reinstalls Ubuntu with a different partition size or if he were to put in on the 1T drive.

---

### Post by lindsay7 on 2009-03-09
This is what I am talking about. I found this on another thread, remember this is for a true dual boot. If you installed under windows you can uninstall it from the control panel, add/remove programs.

 April 26th, 2008 	  #2 
tamoneya 
Iced Blended Vanilla Crème Ubuntu

 
 
 
Join Date: Jan 2008
Location: US
Posts: 2,817 
Ubuntu 8.04 Hardy Heron 
 	Re: How to uninstall? 
first you should over write the linux partition and resize the vista partition to take up the unused space. This can all be done through the linux liveCD. 
Code:
sudo gparted
Remove the ext3 partition and make the ntfs partition take up all the unused space. Then put the vista install disk in and tell it to repair your windows installation. This will replace GRUB with the linux bootloader and make it so that you boot directly into windows.
__________________
Desktop: Q6600 OC: 343 x 9, 4 GB RAM, 8600 GTS Twinview (22",17"), 1.5 TB RAID 5
Laptop: Lenovo T61 T7300 @ 2 GHz, 2GB RAM, Nvidia 140M Quadro, 160 GB harddrive
Remember to mark posts as [SOLVED] when your problem is resolved

---

### Post by dubika on 2009-03-09
Thanks to all for your time and advice.  Your answers prompted me to dig a bit deeper.  I am an Ubuntu novice and have tried (and messed up) different things, and didn't even know for sure if I had installed in a separate partition, or through Windows ...  
Anyway, it was a Windows installation, so I just went to Control Panel > Add/Remove Programs and removed this Ubuntu installation.  Now Windows works fine on one HD, and Ubuntu on the  other  HD.:D

---

