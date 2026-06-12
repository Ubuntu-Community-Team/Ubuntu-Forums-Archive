---
title: "need simple advice to set up Ubuntu and XP on my laptop"
date: 2009-10-04
forum: Installation &amp; Upgrades
---

### Post by irockonguitar on 2009-10-04
Hi

I've been using Ubuntu for almost 2 years now, and I'm currently running 9.04 Jaunty Jackalope. I'm very happy with it, but I have some issues that are leading me to think that I probably need Windows for some things, for instance in the near future I'm going to need to install some programs such as AutoCAD and MicroSurvey, and possibly ArcGIS, for my university courses and ultimately for my career. I'm also tired of creating documents in OpenOffice and having to reformat them on a Windows computer before I submit them.

Anyways, I am a complete IDIOT when it comes to the technical aspects of computers, and even worse with Windows.  I know almost nothing about how partitioning works and how to set it up, but this is what I want to do, so any advice or reference to some solid information would be greatly appreciated. Basically what I need is a step-by-step beginner's guide, if such a thing exists.

Many thanks in advance to anybody who is able to give some advice or point me in the right direction. :)

---

### Post by donato roque on 2009-10-05
Partitioning can be a little hairy so my first advice is BACKUP.
Here are links to basic things when partitioning and creating space in your hdd.

1)  [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

2)  [https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html)

Edit: 3)  [https://help.ubuntu.com/9.04/installation-guide/i386/index.html](https://help.ubuntu.com/9.04/installation-guide/i386/index.html)

---

### Post by running_rabbit07 on 2009-10-05
[B]First, back up your files!!!
[/B]
You need to use a LiveCD to boot your system. 

Once booted, go to System>Administration>Partition Manager

Depending on how much free space you have, using the partition editor, shrink your Ubuntu partition so that you have enough free space for Windows.

After shrinking the partition, you are going to want to move it to the right, so that Your new Windows partition can be on the Left. Windows prefers to be the first system on the drive.

Once the Ubuntu partition is moved over, you will need to fill the unallocated space with an NTFS Primary partition.

Once the partitioning is done, throw in the Windows Installer disk and install it in your new NTFS partition.

Once Windows is installed, you will need to boot the Ubuntu LiveCD, yet one more time and go to **[this site]("http://ubuntuforums.org/showthread.php?t=224351")** and follow the directions for reinstalling the Grub boot loader.

If you need anymore help or clarification, feel free to ask. Someone will be here to help.

---

### Post by irockonguitar on 2009-10-05
Thank you both for the quick replies! (although I'm in no particular hurry, it's still nice to get answers quickly :D )  

Sorry if this is a juvenile question, but what is a "LiveCD?" Is that just the CD I made that I used for the clean install of Jaunty?

---

### Post by oboedad55 on 2009-10-05
> **irockonguitar said:**
> Thank you both for the quick replies! (although I'm in no particular hurry, it's still nice to get answers quickly :D )  

Sorry if this is a juvenile question, but what is a "LiveCD?" Is that just the CD I made that I used for the clean install of Jaunty?

That's the one.

---

### Post by luctor on 2009-10-05
Real quick and easy answer :
Step 1. Install XP
Step 2. Install Ubuntu

worked for me .. :p

---

### Post by tom.swartz07 on 2009-10-05
I agree with Rabbit's walkthrough, although I might suggest using gparted. It is available here[Gparted]("http://gparted.sourceforge.net/")

Burn that to a CD, then leave it in your tray when you boot.
I personally like GParted over the system tool because you could boot straight into the utility, and it is very thorough; you shouldnt have any problems with data loss as long as you make sure you let it finish its task.

Also, it would be wise to note that you should do a series of disk defragments on your XP partition first. (Even though Windows says one is complete, run a second or third to clean EVERYTHING up). It will make the partition move complete a lot more smoothly and quickly.

Hope this helps! Cheers!

---

### Post by running_rabbit07 on 2009-10-05
> **luctor said:**
> Real quick and easy answer :
Step 1. Install XP
Step 2. Install Ubuntu

worked for me .. :p

He already has Ubuntu Installed as a primary OS. Depending on the Windows install disk, it may not see the EXT partition.

As for the recommendation to download and burn GParted, that may work better, I've never tried GParted. I am sure being all on it's own it will have more features to make it work more smoothly.

---

### Post by Agent.Logic_ on 2009-10-05
> **irockonguitar said:**
> I know almost nothing about how partitioning works and how to set it up, but this is what I want to do...
[Here](http://www.psychocats.net/ubuntu/partitioning) is something that you could use to plan your partitioning scheme. And [here](https://help.ubuntu.com/community/WindowsDualBoot) is another guide on dual booting Windows and Ubuntu. The guide tells you how to install Ubuntu *after* installing Windows XP and vice versa.

Hope this helps. Cheers.

---

### Post by irockonguitar on 2009-10-05
> **Agent.Logic_ said:**
> [Here](http://www.psychocats.net/ubuntu/partitioning) is something that you could use to plan your partitioning scheme. And [here](https://help.ubuntu.com/community/WindowsDualBoot) is another guide on dual booting Windows and Ubuntu. The guide tells you how to install Ubuntu *after* installing Windows XP and vice versa.

Hope this helps. Cheers.

Thank you (and everyone above you, too). I have a question regarding the first link in your post, though. I read it and now I'm not quite entirely sure how the Ubuntu /home partition works. Can it serve as both a place to store shared data between the two operating systems, as well as a place to store my Ubuntu settings? And does this mean that if I go to install the next version of Ubuntu, I won't lose any settings, like desktop background, time zone, programs that run at startup, etc? 

Also, the fellow who wrote the article calls his "personal favorite" the scenario where there is a large Ubuntu /home partition, and no FAT32 partition, since he has FS-Drive. Does anyone else know anything about this?

I'm just trying to make sure I plan this out well now, so I don't have to do it again anytime soon.

Thanks again for all the help. :)

---

### Post by oldfred on 2009-10-06
The FS drive supposed works. It is fine for reading but there may be some remaining issues with writing. Ubuntu will  read & write both windows and ext3 or ext4 partitions. If you want to share a lot of data I believe a NTFS is the best way if you want to share with windows. I still have a shared FAT32 but will change soon. Three years ago the linux ntfs driver was not 100%, but is now. But Fat has many issues, it will not handle files over 4GB, does not work with utf8 (newer char encoding), and does not have journaling to allow possible recovery after a bad shutdown.

Separate/home is still a good idea if you plan on reinstalling Ubuntu every 6 months when it is updated. /home has most of your settings and local data. If you store most of your data, pictures, music, documents, movies etc, in a separate /data in either ext3 or ntfs then /home does not have to be as large.

NTFS and Fat info:
[http://technet.microsoft.com/en-us/library/cc938932.aspx](http://technet.microsoft.com/en-us/library/cc938932.aspx)
[http://technet.microsoft.com/en-us/library/cc940351.aspx](http://technet.microsoft.com/en-us/library/cc940351.aspx)

---

### Post by irockonguitar on 2009-10-06
Thank you :)

---

### Post by Agent.Logic_ on 2009-10-06
> **irockonguitar said:**
> Thank you (and everyone above you, too). I have a question regarding the first link in your post, though. I read it and now I'm not quite entirely sure how the Ubuntu /home partition works. Can it serve as both a place to store shared data between the two operating systems, as well as a place to store my Ubuntu settings? And does this mean that if I go to install the next version of Ubuntu, I won't lose any settings, like desktop background, time zone, programs that run at startup, etc? 

Also, the fellow who wrote the article calls his "personal favorite" the scenario where there is a large Ubuntu /home partition, and no FAT32 partition, since he has FS-Drive. Does anyone else know anything about this?

I'm just trying to make sure I plan this out well now, so I don't have to do it again anytime soon.

Thanks again for all the help. :)
You are welcome! Your /home partition *can* serve both purposes, but it is not advised, especially if your other operating system is Windows. That article is a bit old, a time when Ubuntu couldn't handle NTFS very well. Ubuntu can now handle NTFS partitions very well. Also, if your /home partition happens to be one of ext2, ext3, ext4 etc. formats, Windows can't read these partitions by default.

Your partitioning scheme depends on your disk usage requirements. If you want to work with the same files in both Windows and Ubuntu, then go for a / (root), /home (to save your settings so that when you reinstall/update, your settings will be saved), a Windows partition and a large chunk (the majority of your disk space) of NTFS/FAT32 partition for common files and programs is recommended. If you are going to use Windows and Ubuntu for different purposes, then a Windows partition (for both Windows, and the programs and files it will contain), a / (root) partition and a /home partition is recommended.

For example, on one of my laptops dual booting Vista and Jaunty on a 320 GB HDD, this is the partitioning scheme: 10GB Visa recovery partition, 40GB Vista partition, 25GB for / (root), 4GB for swap and the rest for /home. I use Vista and Ubuntu for different purposes, so I don't have a common partition for both. If you require a common partition for Windows and Ubuntu, I'll be happy to explain how it can be done, don't hesitate to ask!

Cheers!

---

### Post by irockonguitar on 2009-10-06
Ok, so I managed to create the partitions and install Windows with minimal trouble. Then I used the LiveCD and reinstalled Grub. Now when I boot, it defaults to Ubuntu, but I'm not entirely sure how to make it boot into Windows. Is there an option at startup that I'm not seeing?

---

### Post by running_rabbit07 on 2009-10-06
> **irockonguitar said:**
> Ok, so I managed to create the partitions and install Windows with minimal trouble. Then I used the LiveCD and reinstalled Grub. Now when I boot, it defaults to Ubuntu, but I'm not entirely sure how to make it boot into Windows. Is there an option at startup that I'm not seeing?

```
sudo apt-get install startupmanager
```
Will install Startup Manager, which will be under the System>Administration menu.

Open the program and go through the tabs and select the show boot loader menu. Afterwards you should see a menu at startup to choose which OS to boot.

---

### Post by irockonguitar on 2009-10-06
Alright, thank you. Now it shows me a bunch of options, but none of them are Windows. What happened to it?

---

### Post by oldfred on 2009-10-06
When you install Windows after Ubuntu, grub does not know about windows. You have to manually add the windows boot stanza to menu.lst for grub to have the option. It will depend on what partition you installed it on, and it must have been a primary partition to get it to work.

in terminal run:
```
sudo fdisk -l
``` -l is el not 1.This will list your partitions so you know which is windows. Linux partitions start at sda1, but Grub starts at (hd0,0) or you subtract one from the linux entry since grub starts at 0.

edit menu.lst in terminal:
```

gksudo gedit /boot/grub/menu.lst
```add, but adjust the entry from sda2 or (hd0,1) to your entry, You may have windows in sda2 or sda3 so the numbering in grub would be (hd0,1) or (hd0,2), Grub counts from zero, linux from 1:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Microsoft Windows XP Professional
rootnoverify (hd0,1)
savedefault
chainloader +1

---

### Post by irockonguitar on 2009-10-06
Thank you. This is the result I get when I run 

```
fdisk -l
```


```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x96dfc149

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3916    31455238+   7  HPFS/NTFS
/dev/sda2            3917       16098    97851915   83  Linux
/dev/sda3           16099       18709    20972857+  83  Linux
/dev/sda4           18710       19457     6008310    5  Extended
/dev/sda5           18710       19457     6008278+  82  Linux swap / Solaris
```



I had made an NTFS partition for Windows, and placed it on the left, moving Ubuntu to the right. So does that mean that sda1 is the Windows one, or is it still Linux? In which case, where did my Windows go?

---

### Post by oldfred on 2009-10-07
sda1 is your ntfs drive and * means it is bootable.

Your entry should be and placed before or after the automagic area, as everything in the automagic area gets rewritten on every kernel update:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
rootnoverify (hd0,0)
savedefault
chainloader +1

---

### Post by irockonguitar on 2009-10-07
It worked! Thank you very very much. :D  Now I just have to learn how to make Windows work for me... :)

---

### Post by running_rabbit07 on 2009-10-07
> **irockonguitar said:**
>  :D  Now I just have to learn how to make Windows work for me... :)

Now that sounds like it will be fun!:popcorn: J/K

---

