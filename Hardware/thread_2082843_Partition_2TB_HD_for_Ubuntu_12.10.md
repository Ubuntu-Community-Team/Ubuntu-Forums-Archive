---
title: "Partition 2TB HD for Ubuntu 12.10"
date: 2012-11-10
forum: Hardware
---

### Post by claven123 on 2012-11-10
I just go my new computer yesterday and I need to partition the HD to allow for Ubuntu 12.10. 

I plan on making at least a 100gb partition for this install, but wonder what do I use?  Can I just use gparted like before and I assume it's included on the Ubuntu 12.10 install files.

Question is.... are there any good tutorials or guides on the correct steps to doing this?

D

---

### Post by ahallubuntu on 2012-11-10
You mean it's an empty 2TB drive with no partitions?  Or it already has Windows on it and you need to make room for Ubuntu?

If you already have Windows on that drive, I'd use the built- in Windows partition shrink tool - it's pretty good.  After you shrink it you can then use Gparted to make the new partitions if you wish.

I don't recall if 12.10 has Gparted included on the live CD (12.04 does).  At worst, you can install gparted in a live session if you are on the internet.

If you plan to install Windows on the same drive, I recommend installing it FIRST then install Ubuntu.

100GB would be too big for me for a basic Ubuntu partition with no data.  I usually aim for about 20GB or maybe a little more if you plan to install a lot of software.  I make my swap partition at least the same size as the amount of RAM I have, so I can use hibernation.

---

### Post by oldfred on 2012-11-10
Are you going to install Windows? 

Ubuntu's default install will use gpt partitioning for drives somewhat over 1TB. But gpt is only required for drives over 2TB, so you could use the older MBR partitioning. But if installing Windows you have to have a computer that boots with UEFI with gpt partitioning, otherwise you have to use MBR.

We also have seen some issues with very large / (root) partitions. Better to have a smaller root of 25GB or so and larger /home or other data partitions. Will you want to install other Linux systems to test or experiment?

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
    250 MB efi FAT32  (for UEFI boot or future use for UEFI)
    1 MB bios_grub  no format (for BIOS boot)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by claven123 on 2012-11-10
Ok, sorry I didn't clarify up front.... but

I have Win 8 pre-installed on the 2TB HD.

I'm planning a dual boot.  

I would like to experiment in the future with other flavors of linux etc.... but not now.

I down loaded the 64bit Ubuntu 12.10 and will be using a USB drive to install.

I'm not sure what is there on the current HD, but will take a look.  I'm sure Dell has made a bunch of partitions....



What is the advantage and or disadvantage of have a different partition for data? 


Thanks,

D

---

### Post by claven123 on 2012-11-10
I'm reading up on the dual boot and see a bit of traffic on issues with windows not being accessible after and or the blank screen.  (I assume the blank screen is a video driver issue) but not sure.  Seems there are a few problems with the install.  I have read a guide on this and not sure if this will work for me or not.

[http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/](http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/)

I just want to do this right (setting up the HD with the partitions) before I install ubuntu.  I've found in the past this makes it a whole lot easier.

D

---

### Post by oldfred on 2012-11-10
If you have Windows 8 pre-installed you have secure boot. Supposedly grub2 2.00 has enabled the secure boot that works, but just about everyone so far seems to have turned secure boot off.

Be sure to use Windows to shrink the Windows partition and reboot several times before installing Ubuntu.

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)

What video system do you have as that seems to make a big issue lately.

---

### Post by claven123 on 2012-11-11
AMD Radeon HD 7570 1GB GDDR5 for Win 8

This was pre-installed on the system.  I was trying to get an NVIDIA, but this is what got.  I will try to tackle this issue once I get the partition completed.

I also use two monitors, but initially I will settle for one monitor for now and work on the second later.


D

---

### Post by claven123 on 2012-11-11
How do I turn off the secure boot feature?

D

---

### Post by oldfred on 2012-11-11
The Microsoft specification/UEFI specification says there must be a way to turn it off in UEFI menu/BIOS. Vendor should have it in their manual or something on the UEFI page.

But Ubuntu 12.10 should install with secure boot on.

---

### Post by claven123 on 2012-11-12
Ok, so I looked up the info on the Win 8 machine and this is what I have...
 
I have 5 partitions...
 
500mb (Healthy EFI partition)
40mb (Healthy OEM partition)
500mb (Healthy Recovery partition)
10.75gb (Healthy Recovery partition)
1851gb NTFS OS (C:) (Healthy Boot, Page file crash dump, primary partition)
 
 
This is my plan...
 
Using windows disk managment I will shrink the OS (C:) partition to 200gb  leaving me a large unused space.  I will then reboot windows several times.
 
I will then use the live USB to try ubuntu 12.10 64b, then install it.
 
[http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/](http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/)
 
I was going to kinda follow these instructions as this is the closest thing I can find.  I'm installing ubuntu 12.10 on a machine that HAS windows 8 pre installed.
 
What other key features am I missing.  I don't see about secure boot turned on or off, not sure if I need to make all those partitions?
 
 
D

---

### Post by oldfred on 2012-11-12
Lots of technical detail if interested.

[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

None of these were Windows 8 with the secure boot, but show UEFI installs.
UEFI boot Issue with Alienware X51 
[http://ubuntuforums.org/showthread.php?t=2039451](http://ubuntuforums.org/showthread.php?t=2039451)
UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
UEFI screen shots with choice to boot
[http://ubuntuforums.org/showthread.php?p=12030957#post12030957](http://ubuntuforums.org/showthread.php?p=12030957#post12030957)
Dual Video Intel & nVidia
[http://ubuntuforums.org/showthread.php?t=1994622](http://ubuntuforums.org/showthread.php?t=1994622)

---

