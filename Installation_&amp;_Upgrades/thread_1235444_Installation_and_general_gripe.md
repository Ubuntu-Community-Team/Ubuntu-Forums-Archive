---
title: "Installation and general gripe"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by Lifeboat on 2009-08-09
I can't tell you how disappointed I am about Ubuntu's disk partition! :(

After using fdisk for 15 years, I have 2 totally crap installs of two versions of Ubuntu, and one hard drive partition wiped out that never should have been.

I just finished installing 9.04 on a WD drive with 512GB of free space, and chose the default "side by side" since it already had Windows 7 in the other 512GB partition.

So the install goes through and tells me to remove the CD. Except it locked the drive (light was off, no activity any more), but I can't remove the CD.

After working out that problem, Ubuntu boots up, but I can't update Ubuntu because I don't have enough room - it seems Ubuntu decided to squeeze itself into a very tiny partition, on a huge (1 TB), drive, that was 90% empty. 

Total size of the Ubuntu partition it made for itself is < 500MB.

Is Canonical suffering from some mental affliction, or what's the deal with this? Hard drive partition programs have been around for decades, and they're a critical part of any install.

We don't need more junk every six months. We need a *quality* version, with default choices that make sense, and a partition program that's working right, and showing the right info, all the time. 

Also, why do we have file options for file systems that are easily corrupted? That makes no sense, and sullies the name of Ubuntu.

---

### Post by presence1960 on 2009-08-09
When choosing the side by side option you need to choose how much space to give Ubuntu by grabbing the right border of the Windows partition graphic and drag it to the left until Ubuntu has the space that you want to give it. If you fail to do this I believe you will wind up with 2.3 or 2.7 GB for the Ubuntu partition.

Don't take this personally but I say a lot on here that prior to installing a new OS (especially an OS that one is unfamiliar with) one should spend some time reading & studying about what it is they are going to do. Once one is familiar with the process they are about to undertake then and only then should they actually try. here are some links to get you up to speed:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm) - for XP installed first & has links for Vista installed first on the page
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html) - for a pdf Ubuntu Pocket Guide which BTW has an excellent step by step on how to install Ubuntu correctly.

I am sorry your install was not correct, but if you feel Canonical is giving us "junk" remember no one is forcing you to use Ubuntu, there are plenty of other Linux distros to choose from. Frankly from what you have posted it is a clear case of operator error. The installer and partitioner software does not usually mess up. like any other software it only does what the user tells it to do. You failed to specify how much space to give the Ubuntu partition so it was left on 2.3 or 2.7 GB.

I don't believe the <500 MB stat you reported because if that were true there would be no Ubuntu to boot into. 500 MB is far less than what is required to install the Ubuntu OS.

---

