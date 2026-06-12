---
title: "Installation Questions"
date: 2006-02-08
forum: Installation &amp; Upgrades
---

### Post by lbenn on 2006-02-08
I am currently using the live CD version of ubuntu.  I would like to install it on my hard drive but I am concerned as to how I can install ubuntu and also keep windows xp in it's entirety.  Does the expert installation allow you to do this.  Right now I have one large partition using the ntfs.

---

### Post by dcast on 2006-02-08
you can do this with the standard installation it will ask you which drive (or partitions) you want to use. After the install grub should auto-detect windows and you can use either and have a choice on startup.

---

### Post by Koybe on 2006-02-08
AS you only have one partition it's a bit more difficult.
You'll need some free space to install ubuntu. The only way to do this is to resize your current partition. Don't forget defragmenting your Hard disk before. Ans save your data before. We never know ;-) To resize partition you can get GParted and the [LiveCD](http://gparted.sourceforge.net/livecd.php) for it.

Then donwload the install version of ubuntu and you can go for a standart installation... no need for the expert one.

Good luck ;)

---

### Post by Bartender on 2006-02-09
lbenn -
Take a look at this 

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

I just did a W2K/Ubuntu dual-boot a week ago using the Ubuntu+NTFS directions.  Made a FAT32 partition so that Ubuntu and Windows can pass data back and forth.  Worked like a charm.  Windows will see the FAT32 partition, but Ubuntu probably won't.  When you get done, in Ubuntu go to Administration>Discs and look at the partitions.  If you can see the FAT32 partition (it'll be called vfat) but can't enable it you'll have to edit your fstab.    I did it so you can too. 

I didn't do any partitioning beforehand.  Windows had the entire drive.  The Ubuntu CD has all the tools built into GRUB.  If you can, set yourself up in front of a computer that's connected to the internet so you can follow the steps one by one.  I wasted paper trying to print the instructions; none of the screenshots were printed.
Defrag, back up your valuable data, find your Windows CD and key codes, take notes.  GRUB works but there are about two million things that can go wrong, from power outage to failing hardware, and there can be no guarantee that you won't be re-building from scratch.

---

