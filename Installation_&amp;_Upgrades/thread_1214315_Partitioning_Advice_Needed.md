---
title: "Partitioning Advice Needed"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by wjwh on 2009-07-15
I have just received a new computer. It has a 1 TB hard-drive.  I want to set it up to dual boot Windows XP/Ubuntu.  I would like to be able to set the XP portion up so as to have the user and application data on a separate partition from the operating system. I would set up the Ubuntu with /, home and swap partitions, as usual.  What series of partitions - primary, extended, etc. should I set up initially to achieve this?  Please make the advice simple - for a beginner.

---

### Post by aesis05401 on 2009-07-15
Just to clarify, you have a stand alone XP disc?  

Manufacturer restore discs usually require the image that is restored to match original metrics, so the first thing to do is make sure there are no constraints on your partition geometry (ie:size and placement).

Second, are you familiar with partitioning in general?  If so, are you already familiar with a partitioning tool or do you need a step by step guide?

---

### Post by starcraft.man on 2009-07-15
> **wjwh said:**
> I have just received a new computer. It has a 1 TB hard-drive.  I want to set it up to dual boot Windows XP/Ubuntu.  I would like to be able to set the XP portion up so as to have the user and application data on a separate partition from the operating system. I would set up the Ubuntu with /, home and swap partitions, as usual.  What series of partitions - primary, extended, etc. should I set up initially to achieve this?  Please make the advice simple - for a beginner.

For this advice, I'm assuming you know exactly how to work gparted. If you need any help, see their [documentation]("http://gparted.sourceforge.net/documentation.php") page on their site.

My advised partitioning would be as follows:

X - Means a primary partition.
--> Extended space/logical partition

X - Main XP install, 30GB, NTFS
X - Program/user/Storage partition (Z1 Size)
--> Root / (only 10 GB max, EXT4)
--> swap (1GB or less, I only have 512)
--> home (ext4, Z2 size)

Z1 and Z2 are wild cards. If you plan on going back and forth between Windows and Ubuntu and want to have one central location for storing files, ya might make the Program/usr/storage partition the remainder of the drive (minus maybe say 50GB for home). Otherwise, you could make home larger and subtract from the second primary.

As to specifics, way I see it, you make the second primary (Program/Storage/usr) to have 3 folders. 1 call programs, simply point installs of third party programs to there (like games or adobe programs). The second, call My Documents. You can very easily in Windows move my documents folders to any target path. [link]("http://www.watchingthenet.com/change-location-of-mydocument-folder-in-windows.html").

Last folder, I'd just call storage and put all your files in there (media etc...). Your free to arrange differently if you like.

I encourage using NTFS as the go between, because the NTFS3g drivers are much better in my experience than the EXT2 drivers that you must install into Windows to write to ext linux partitions. I think that covers everything, any questions, just reply again.

Note: aesis raises a good point. I'm assuming you have an XP install CD. If you only have images on DVD or a hidden partition, you'll need to first restore to a clean install or use existing, and resize the XP partition down until acceptable free space is made available. See resizing and moving in documentation.

---

### Post by wjwh on 2009-07-15
Many thanks to both aesis05401 and starcraft.man for their replies.  I do indeed have a stand alone XP disc.  I was planning to install XP first and then install the Ubuntu, as I have found this easier to do in the past (but then I had only one XP partition).  I would hope to use Ubuntu for almost everything except printing, as I have been unable to find Linux drivers for my Canon imageClass D320.

Thanks again.

---

### Post by aesis05401 on 2009-07-15
> **wjwh said:**
> Many thanks to both aesis05401 and starcraft.man for their replies.  I do indeed have a stand alone XP disc.  I was planning to install XP first and then install the Ubuntu, as I have found this easier to do in the past (but then I had only one XP partition).  I would hope to use Ubuntu for almost everything except printing, as I have been unable to find Linux drivers for my Canon imageClass D320.

Thanks again.

Not sure if this has changed, but you will need to make some registry changes to streamline the separation of data from your XP install.  

Off tops:
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\ProgramFilesDir value should be changed to reflect your data drive letter.  

I don't recall the other keys, but an internet search should yield the other settings to cause your non system files to target your data drive.

As for partition, with 1TB the only really important thing is that you don't skimp on the OS base partitions - and Starcraft posted sane partition sizes... so good luck, post back with issues.

---

### Post by shicy on 2009-07-16
> **wjwh said:**
> Many thanks to both aesis05401 and starcraft.man for their replies.  I do indeed have a stand alone XP disc.  I was planning to install XP first and then install the Ubuntu, as I have found this easier to do in the past (but then I had only one XP partition).  I would hope to use Ubuntu for almost everything except printing, as I have been unable to find Linux drivers for my Canon imageClass D320.

Thanks again.
i also had problems with my printer (canon pixma ip1600) but i found similar driver on internet amd detail description of installation and it works!
you should try to find drivers, can't loose anything ;)

---

