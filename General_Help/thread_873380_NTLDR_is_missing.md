---
title: "NTLDR is missing"
date: 2008-07-28
forum: General Help
---

### Post by kdidrickson on 2008-07-28
So, I've been trying to get something... *anything* to dual boot with Ubuntu. I have Ubuntu installed on the first partition of the first hard drive (sda1). I have two data partitions. One is on the same hard drive as ubuntu (sda3), the other is on my second drive (sdb1).

So, first I tried to install xp on a partition on the second drive (sdb2), and the furthest I ever got was the part of the installation where windows is running from the cd. I couldn't even boot into windows to finish the installation after the restart as it would complain that "NTLDR is missing." After attempting numerous fixes like transferring files from an existing windows installation to the C drive and editing the GRUB menu commands, I finally gave up and decided to try OSx86 on the same partition.

This is where I am currently stuck. I formatted the partition to HFS+ and OS X installed without issue. I added OS X to the GRUB boot menu and when I boot to the partition, I get "NTLDR is missing"! I thought to myself, 'Of course it's missing, silly computer, I deleted windows!!' At first I thought that the installer didn't write anything but I checked the partition and everything appeared as it should.

I googled this problem and everything I saw said to change the boot.ini file. This was confusing to me because I wiped it off my hard drive along with everything else in the Windows partition. The only explanation that I can think of is that it's the MBR left over from the Windows install telling the computer to look in hd1,1 for NTLDR. Can someone please help be done with this mess once and for all?? I just want know the kind touch of my precious Adobe software once again...

**Here's my fdisk output:**

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x092a0929

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2117    17004771   83  Linux
/dev/sda2            2118       38913   295563870    f  W95 Ext'd (LBA)
/dev/sda3   *        2362       38913   293603908+   7  HPFS/NTFS
/dev/sda5            2119        2361     1951866   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d6a4c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       59526   478142563+   7  HPFS/NTFS
/dev/sdb2           59527       60800    10233405    5  Extended
/dev/sdb5   *       59527       60800    10233373+  af  Unknown

**And menu.lst:**

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=85dc40d0-1c74-4c8c-aeff-be712697f1f5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		OS X
rootnoverify	(hd1,1)
savedefault
makeactive
chainloader 	--force +1

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=85dc40d0-1c74-4c8c-aeff-be712697f1f5 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

---

### Post by kdidrickson on 2008-07-29
anyone?

---

### Post by cdtech on 2008-07-29
I see that sdb2 has no boot flag. Your MBR is probably still on the sdb1 partition which has the boot sector.

---

### Post by kdidrickson on 2008-07-29
So how do I change it?

---

### Post by cdtech on 2008-07-29
I'm not really sure what you want to do with the sdb drive. Are you wanting to keep the windows on the sdb1 partition? You could use the gparted live cd to arrange the drive for the ubuntu install.

You can start by removing the extended partition and just add one for root "/" and one for "swap" (sdb2, sdb3) and you could even have an extra one for your "/home" partition (sdb4) and still be within the allowable partitions on a drive (4) without extending.

Does your primary drive boot ok?

**P.S.**
I see that your menu.lst should be:
title OS X
rootnoverify (hd1,**4**)
savedefault
makeactive
chainloader --force +1

---

### Post by kdidrickson on 2008-07-29
Sorry, I don't think I mentioned that I already have Ubuntu installed on sda1 and the swap partition on sda5. I really don't want to have to reinstall Ubuntu or mess with it as it seems to be the only thing that will work on my computer's horribly messed-up partition table. sdb1 is also one of my data drives so I don't want to mess with it unless I have to. Would the fact that the partition that I am installing OS X and Windows on is encapsulated by an extended partition make any difference?

My primary drive does boot okay but for some strange reason gparted shows it as a totally unpartitioned, blank disk.

---

### Post by NeoAndersen on 2008-08-01
I have a "NTLDR is missing" problem too.
But in my case I have 2 HDs sata...
I firstly installed XP in the 500 GB HD...
Immediately after this I installed Ubuntu 8.04.1 amd64 in the 320 GB HD...

The PROBLEM is that the option to boot windows dont appeared in the GRUB options...

I've tried to edit the GRUB and then the XP option appeared but it haven't worked. When I choose start XP just a error message appears: NTLDR is missing...

Help please!!

---

### Post by 3rods on 2008-08-01
I don't see an entry for XP in the menu.lst, did you delete it? 

The entries you have are unusual as well, are you running hackintosh, ubuntu and XP? 

I see 2 NTFS partitions, which one are you trying to boot? If you're trying to boot the first drive, is XP in a Primary, Active partition? You can only have two Primary per drive. 


My suggestion would be to take out or disconnect the working ubuntu drive (to avoid damage), put the drive you want XP on the first channel, primary controller (in BIOS). Then boot the XP CD, wipe the entire disk, partition as desired, install XP. Then, put ubuntu back in, switch the XP drive to secondary, and follow the knowledge-base instructions to chainload XP off of the GRUB bootloader.


I didn't see this the first go around:
> So, first I tried to install xp on a partition on the second drive (sdb2)

sdb2 says it's extended - you can't boot XP in a logical/extended partition.

Check this out:
[http://ubuntuforums.org/showthread.php?t=867503]("http://ubuntuforums.org/showthread.php?t=867503")

---

### Post by linux_tech on 2008-08-01
There are a few ways of fixing this, depending whether you have a boot disk or if you have the install cd;
If you have a windows boot disk, you can boot using this , go back into windows and replace ntldr.
method2- 
NTLDR missing or corrupt - 
Boot to windows install cd, try to do a non destructive install (repair)
which should replace ntldr

method 3; using recovery console
1.Insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
 
2.When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
 
3.If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
 
4.When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
 
5.Enter in the following commands
 
COPY X:i386NTLDR C:
COPY X:i386NTDETECT.COM C:
[where X=CD ROM Drive]
Take out the CD ROM and type exit

---

### Post by linux_tech on 2008-08-01
For a dual boot to work without issues, its easiest to install windows xp 1st, then install Ubuntu 2nd, in its own partition.

---

### Post by 3rods on 2008-08-01
The NTLDR is not *missing*, it's that XP can't find it on a Primary, Active Boot partition. It just thinks it's missing. You can't boot XP from extended partitions.

---

