---
title: "Help with dual boot..."
date: 2008-09-18
forum: General Help
---

### Post by pirates on 2008-09-18
Hi all,

First post on the forum and very glad to be a part of this community:)

I currently have a dual boot setup with Windows XP and Linux (Ubuntu 8.0.4), as well as a DATA partition. I would like to know how to "re-install" Windows XP without messing up my Linux installation and my data partition. My configuration is as follows:

- HDD size is 100GB partitioned as:
25GB Windows, 25GB Linux, 50GB DATA

When I tried to re-install Windows, the installation gets to the point of copying the "ntldr" file and throws out a message that it cannot copy this file to the HDD:confused: The only way I was able to overcome this issue was to format the entire HDD and re-install both Linux and Windows from scratch. You guys can imagine the nightmare of getting the data off the DATA partition. I am posting this question for the purposes of learning so as to know what to do in future. I'm new to Linux and am enjoying the challenges of learning this wonderful OS. Looking forward to a long term participation on this forum.:KS

Thanking you guys in anticipation. Sorry for the long post, it is my first, so please excuse me...Cheers

---

### Post by northern lights on 2008-09-18
> **pirates said:**
> I currently have a dual boot setup with Windows XP and Linux (Ubuntu 8.0.4), as well as a DATA partition. I would like to know how to "re-install" Windows XP without messing up my Linux installation and my data partition.Can't (as far as my experience goes). Windows will inevitably overwrite the MBR. Still, [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") should prove a worthy read.

> **pirates said:**
> When I tried to re-install Windows, the installation gets to the point of copying the "ntldr" file and throws out a message that it cannot copy this file to the HDD
ntldr is short for ntloader and, you might have guessed, the standard Windows bootloader. Why Windows setup would complain being unable to install it, is trifling to me.

---

### Post by mb_webguy on 2008-09-18
While the preferred order of installation is Windows and then Ubuntu, you should be able to install Windows after you install Ubuntu.  You would just have to re-install the GRUB bootloader after you install Windows.  The first two posts in this thread describe two different ways of doing this.  I would suggest the second, as it's entirely too easy to accidentally format a partition using the first.

However, I also have no idea why Windows would have a problem writing the Windows bootloader.

By the way, I don't know what sort of partitioning scheme you're planning on using, but I would suggest a 15GB NTFS partition for Windows, an 8GB ext3 partition for Ubuntu root, a 1GB ext3 partition for Ubuntu home, a swap partition equal to 1.25x your system memory, and an NTFS partition using the remaining drive space for file storage.

---

### Post by caljohnsmith on 2008-09-18
> **pirates said:**
> 
When I tried to re-install Windows, the installation gets to the point of copying the "ntldr" file and throws out a message that it cannot copy this file to the HDD:confused: 
Did you by chance try to install Windows to a logical partition rather than a primary partition? If so, that would probably explain that error; if you install Windows to a logical partition, Windows will install, but it will try and put its boot files (ntldr, boot.ini, and NTDETECT.COM) on a primary partition. So if no NTFS/FAT32 primary partition is available, then the Windows installer would most likely choke.

---

### Post by TeXtonyx on 2008-09-18
Yes, make Windows on first drive primary/active. Then use boot.ini to boot Ubuntu.
When installing Ubuntu, just after setting up the partition information, a screen appears which says "Advanced", before proceeding to write the partition information. The Advanced option lets one install Ubuntu to the first sector of its boot  partition.
[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
C:\ubuntu.bin="Ubuntu"
------------------------------
ubuntu.bin is the file created by writing the first sector,  512 of the Ubuntu boot partition.
BootPart mostly automatically will create ubuntu.bin and write the option to boot.ini
This method avoids writing grub to the MBR, so that if one has to reinstall Ubuntu, the Windows partition will continue to boot without problem. There are fewer problems when Windows is the first drive. C:\ the Windows NTFS partition, is primary/active.

---

### Post by Teetdiro on 2008-09-18
bump up ..Traveling salesmen make their living visiting as many customers as possible. So speeding to get from one appointment to the next is not unheard-of. Which is how I got pulled over by a highway patrolman. "Don't you ever look at the speedometer?" the officer scolded. Before I knew it, the truth spilled from my mouth. "As fast as I was going," I admitted, "I was afraid to take my eyes off the road." ------------The WOW gold Online Store, Open 24/7 Looking to buy [wow gold](http://www.u4game.com), Items or Accounts? You would find the cheapest gold here. We always online 24 hours a day, 7 days a week, any questions regarding [world of warcraft gold](http://www.u4game.com), powerleveling,wow leveling ,[warcraft gold](http://www.u4game.com), just talk to our representatives using our 24/7 live chat service.[world of warcraft gold](http://www.u4game.com/world-of-warcraft-gold.html),[wow leveling](http://www.u4game.com/Wow_Power_Leveling.html),

---

