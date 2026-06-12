---
title: "Installation on separate HD"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by lbmachado on 2009-08-05
Hi all !

I have a PC with 3 HDDs. The list, as described during the 9.04 version installation, is as follows:

SCSI 3 (0,0,0) (SDA) 320,1 GB ATA SAMSUNG HD322HJ
SCSI 3 (0,1,0) (SDB)    80,1 GB ATA SAMSUNG SP0812C
SCSI 4 (0,0,0) (SDC)    80,0 GB ATA WDC HD8008BD-22MR

I have Win XP installed on the 320,1 GB HD and I intend to install Ubuntu in one of the other two HDDs. The problem is that I have already tried: At the first time the system just did not reboot and, on the second time, I think it screwed up the Win XP boot loader. I had to run "fixmbr" in the recovery mod to get it fixed.

Based on the previous experience, it seems to me that the "use entire disk option"  does not work very well or that the Ubuntu boot loader doesnt get along with 3 HDDs. Does that make sense ? What should that right steps to follow when installing Ubuntu on a separate HD and having the option to choose between Win XP and Ubuntu at startup ??

Thank you very much.
Lbmachado

---

### Post by Ozsmoka on 2009-08-05
Fwiw, I disconnect all hdds but the one I want to install Ubuntu on. 

I install to the entire drive (guided), then once Ubuntu is installed, with the system shut down, I reconnect all drives.

I use the motherboards boot loader (press F8 during boot, and select the drive I want to boot from - not sure if all mobo's/BIOS have this utility, but many do) to load either WIndows or Ubuntu.

In BIOS, I select the boot order to default to the appropriate installation - either Windows or Ubuntu (in my case Ubuntu), so that that particular drive will load as normal by default, UNLESS I hit F8 at boot and select the alternate hdd.

This way Windows and Ubuntu can coexist without having to share a boot loader. If one install fails the other works seamlessly. Just reinstall the other os again, the same way, and away you go. 

Windows drives are accessible from Ubuntu and files can be worked on as if they were part of Windows. For example, you can access the 'Desktop' folder in Windows and work on files there from Ubuntu.  BE VERY CAREFUL if you do this though, as you don't want to trash any critical Windows files.

Windows however will not be able to access the Ubuntu system. You will only detect the Ubuntu system from 'Disk Management' in Windows.

I hope this helps.

Cheers 

oz

---

### Post by konqui on 2009-08-05
Actually there is no need to disconnect! At last install step of desktop cd, before you press install click advanced options. Then enter where you want bootloader. (hd0,0) means 1st Hdd 1st partition. (hd0,1) 1st hdd 2nd partion (hd1,0) second hdd first partion.................................:popcorn::popcorn:

---

### Post by oldfred on 2009-08-06
I have been running Windows XP on one sata drive and Ubuntu on another without significant problems for 2-3 years. I just bought a new 640G drive and installed Ubuntu 64bit. I had also plugged in an old drive to copy some data from. The install found the XP, the 32 bit Ubuntu and the old XP on the old drive (I forgot that it was even bootable).  I always do manual partitions since I want extra NTFS and EXT3 partitions for data to be shared and separate data within Ubuntu. Grub can handle as many drives and partitions as you want.
**How to install and boot 145 operating systems in a PC**
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)
Info is older but has some updates for more current configurations.

---

### Post by lbmachado on 2009-08-07
> **konqui said:**
> Actually there is no need to disconnect! At last install step of desktop cd, before you press install click advanced options. Then enter where you want bootloader. (hd0,0) means 1st Hdd 1st partition. (hd0,1) 1st hdd 2nd partion (hd1,0) second hdd first partion.................................:popcorn::popcorn:
 
In my specifi case (see hdds list below), where should I install dthe bootloader (my win XP is installe on SDA) ??
 
SCSI 3 (0,0,0) (SDA) 320,1 GB ATA SAMSUNG HD322HJ
SCSI 3 (0,1,0) (SDB) 80,1 GB ATA SAMSUNG SP0812C
SCSI 4 (0,0,0) (SDC) 80,0 GB ATA WDC HD8008BD-22MR
 
Thanks

---

### Post by presence1960 on 2009-08-07
Ideally the GRUB bootloader should be installed to MBR of the first hard disk to boot in your BIOS hard disk boot order. if not GRUB will not take over when you boot your rig.

Also if you choose manual at the Prepare disk space window of the install you can choose which disk to install Ubuntu to.

When you get to the ready to install window click the advanced tab and place GRUB on the MBR of the hard disk which boots first.

---

