---
title: "Cloning a remastered XUbuntu easily?"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by rocdoc on 2009-07-28
I volunteer for a small charity which donates refurbished computers to citizens of our small city who normally cannot afford their own computer. On the vast majority of these machines we install Linux. 

We normally install from CD-ROM, but want to now try cloning a remastered version of XUbuntu from a pen drive onto hard drives on various machines.  But it is not quite as easy as I originally had thought. The problem apparently lies with my attempting to  use "dd" to get a small partition (3.5GB) of an XUbuntu system from the pen drive onto larger hard drive partitions. What I am attempting to do is to make the process really simple, with as few Linux terminal commands as possible, because we have a couple of volunteers who do this work who are not yet that up on Linux and we want this process to be easier than just installing XUbuntu from a CDROM drive.

Once the system is cloned onto a 3.5GB pen drive partition the steps to  
get a cloned working copy seem to be thus:

1) using GParted Live CD create a 3.5GB "/" partition, ext3 on the target  
drive
2) insert pen drive then: dd if=/dev/sda1 of=/dev/hda1 bs=32256
3) rerun GParted to increase size of hda1 to make it as large as possible  
and also make a 500MB-1GB swap partition
4) run "grub-install /dev/hda1" to install the boot loader

The other way to do it seems to be:

1) using GParted Live CD create a very large "/" partition, ext3 and a  
typical sized swap partition on the target drive.
2) insert pen drive then mount both the pen drive partition and the hard  
drive / partition
3) rsync -avH --exclude=targetpart penpart/* targetpart
4) unmount both partitions
5) run "grub-install /dev/hda1" to install the boot loader

The way I see it is that because the master partition on the pen drive is  
smaller than what is needed on the target drive there are a couple of  
extra steps involved. Also, it seems grub-install must be run either way  
as I could not find a way to actually get the MBR copied across using dd  
successfully.

If any of you out there have any suggestions on how to make this process  
more streamlined (other than writing a script - which I might have to do)  
I would really appreciate your assistance.

cheers....Larry

---

