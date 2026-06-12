---
title: "Install full ubuntu 8.10 onto a External HD... help?"
date: 2008-12-26
forum: Installation &amp; Upgrades
---

### Post by PwnCakes193 on 2008-12-26
Hey,

I just got a WD My passport 250 gig external hardrive, and I wanted to have a full installation of Ubuntu on there, and still be able to transfer files to the hard drive from Ubuntu and Windows. So basically, if I put a file on there in ubuntu, I want to be able to move it to windows, and such. Is there any way to make it so that it can be a ubuntu install and still have space so that I could transfer my files between XP and ubuntu, and how would I do this?

---

### Post by neu2buntu on 2008-12-26
to install to your external hdd ,boot with live cd in tray and ext hdd plugged in.... and click on the install icon when ubuntu 8.10 loads.....   choose your settings eg country keyboard etc....  then when it comes to install option choose >guided >use entire disk and make sure it is on the external hdd this should be (hd1,0) as your internal hdd is (hd0,0)...... and on the final step of install (think step7) there should be an advanced option,click this and put the bootloader(grub) on (hd1,0) ...as for your second question im not too sure about this, i think you will have to install some program to open NTFS on windows

---

### Post by infamous-online on 2008-12-26
Another suggestion, if you have a spare harddrive lying around, format it and make it a fat32 partition. Windows and Linux can read and write from a fat32 partition. :cool:

---

### Post by caljohnsmith on 2008-12-27
If I were in your shoes, I would create an NTFS partition for all your personal files, and then you can easily access that partition with either  Linux or Windows. Using FAT32 like infamous-online mentioned could work too, but FAT32 has a max file size limit of 4 GB, so you won't be able to store any DVD ISOs for example. Good luck and let us know how it goes.

---

