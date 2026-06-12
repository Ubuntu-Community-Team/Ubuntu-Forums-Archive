---
title: "Installation Issues - Kubuntu and Ubuntu"
date: 2009-03-14
forum: Installation &amp; Upgrades
---

### Post by YOURS3LF on 2009-03-14
I have tried to install both Kubuntu and Ubuntu from the live cd and from within Windows XP. When I run the live cd neither Kubuntu or Ubuntu recognize my hard drive on install. When I run from within Windows XP it runs the program like it should but when I reboot to complete the install it won't boot. What is wrong? 

My system specs are:

- Windows XP Home SP3
- Hitachi HDP725050GLA360 HDD
- XFX GeForce 8200 Mobo
- AMD Athlon 64 X2 Dual Core Processor 4400+ 2.64Ghz
- HP dvd1035
- NVIDIA GeForce 8200 integrated graphics
- 4gb DDR2 667 ram

---

### Post by tommcd on 2009-03-14
> **YOURS3LF said:**
> I have tried to install both Kubuntu and Ubuntu from the live cd and from within Windows XP. When I run the live cd neither Kubuntu or Ubuntu recognize my hard drive on install. 

- NVIDIA GeForce 8200 integrated graphics

So you are able to boot the live CD, and start the installer, is that correct? Are you able to get to the part where you partition the hard drive? If so what happens when you start partitioning? Post any errors you get.
Which version of Ubuntu are you trying to install? Ubuntu 8.04 will likely not work on your motherboard's chipset, but Ubuntu 8.10 should work. See this:
[http://www.phoronix.com/scan.php?page=article&item=nvidia_8200&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_8200&num=1)

And welcome to the Ubuntu forums!

---

### Post by YOURS3LF on 2009-03-15
> **tommcd said:**
> So you are able to boot the live CD, and start the installer, is that correct? Are you able to get to the part where you partition the hard drive? If so what happens when you start partitioning? Post any errors you get.
Which version of Ubuntu are you trying to install? Ubuntu 8.04 will likely not work on your motherboard's chipset, but Ubuntu 8.10 should work. See this:
[http://www.phoronix.com/scan.php?page=article&item=nvidia_8200&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_8200&num=1)

And welcome to the Ubuntu forums!

The live cd works fine. I can boot from it and run everything from the cd. I run the installer and when I get to the point where I am supposed to partition the drive it shows that there are currently no installed drives. I have tried installing both Ubuntu/Kubuntu 8.04 and 8.10 and no success.

---

### Post by tommcd on 2009-03-15
Try different options for the hard drives in the motherboard's BIOS. If there is a setting for "IDE mode" or something like that, then try it. It is possible that the Ubuntu installer is not recognizing your hard drive controller.

EDIT: When the live CD boots up, hit F6 to enter additional boot options. Type **all_generic_ide** and hit enter and see if you can install. See this:
[http://ubuntuforums.org/archive/index.php/t-902561.html](http://ubuntuforums.org/archive/index.php/t-902561.html)
Use the Ubuntu 8.10 32 bit live CD. If you still have problems then use the 8.10 32 bit alternate install CD for the most fail safe install.

---

### Post by YOURS3LF on 2009-03-15
> **tommcd said:**
> Try different options for the hard drives in the motherboard's BIOS. If there is a setting for "IDE mode" or something like that, then try it. It is possible that the Ubuntu installer is not recognizing your hard drive controller.

EDIT: When the live CD boots up, hit F6 to enter additional boot options. Type **all_generic_ide** and hit enter and see if you can install. See this:
[http://ubuntuforums.org/archive/index.php/t-902561.html](http://ubuntuforums.org/archive/index.php/t-902561.html)
Use the Ubuntu 8.10 32 bit live CD. If you still have problems then use the 8.10 32 bit alternate install CD for the most fail safe install.

I'm currently running from the live disc. I did what you recomended and typed in all_generic_ide where you said. I'm running the partition manager now. It recognizes my HD but it has been an hour and nothing has happened. Any other advice?

EDIT: 
After about an hour and 20min I finally got an error message. 
The message was: 

An error occurred while writing the changes to the storage devices.
The resize operation has been aborted.

I rebooted in Windows XP and it ran chdsk and fixed a few errors on the drive. 
Is it worth risking all my data?

---

### Post by tommcd on 2009-03-16
> **YOURS3LF said:**
> 
I rebooted in Windows XP and it ran chdsk and fixed a few errors on the drive. 
Is it worth risking all my data?

It is always good to perform backups of your data. If your data is important enough that you are worried about loosing it then it should be backed up already.

Ubuntu must be having a problem with your sata controller. (I assume this is a sata drive. Is that correct?) I would try a parted magic live CD to partition the drive. 
[http://partedmagic.com/](http://partedmagic.com/)
Create at least one linux ext3 partiton of about at least 10G and a swap partition of 1GB. If you have a lot of space make 3 partitions: one ext3 partition of 10GB for root, a swap of 1GB, and an ext3 partition for home that can be as big as you want. 

Also,
How many partitions are on your drive? And how much free space do you have? If you have 4 primary partitions already, or if don't have enough free space, then that could be the problem.

---

### Post by YOURS3LF on 2009-03-16
> **tommcd said:**
> It is always good to perform backups of your data. If your data is important enough that you are worried about loosing it then it should be backed up already.

Ubuntu must be having a problem with your sata controller. (I assume this is a sata drive. Is that correct?) I would try a parted magic live CD to partition the drive. 
[http://partedmagic.com/](http://partedmagic.com/)
Create at least one linux ext3 partiton of about at least 10G and a swap partition of 1GB. If you have a lot of space make 3 partitions: one ext3 partition of 10GB for root, a swap of 1GB, and an ext3 partition for home that can be as big as you want. 

Also,
How many partitions are on your drive? And how much free space do you have? If you have 4 primary partitions already, or if don't have enough free space, then that could be the problem.

Yes it is a sata drive. I have most of my important files on my flash drive but that ran out of space. My HD has around 375GB free and only has one partition. I would like to keep windows as well if at all possible. I'm going to try and repartition now.

EDIT: How would I install once partitioned? I have all three partitions ready. Root - 10Gib; Swap - 1Gib; ext3 - 255Gib

---

### Post by tommcd on 2009-03-17
> **YOURS3LF said:**
> 
EDIT: How would I install once partitioned? I have all three partitions ready. Root - 10Gib; Swap - 1Gib; ext3 - 255Gib
Congratulations on successfully setting up your partitions then!
To install Ubuntu choose manual partitioning. Choose to install to your 10GB root partition. Your swap will be auto-detected. Choose to mount your 255GB partition as /home. Do not format the 255GB home partition if it has data on it. If it is empty then it does not matter if you reformat it or not.

So go ahead and install Ubuntu.
Welcome to the cool side of computing!
Let me know how you made out. Your motherboard chipset is fairly new, so it sometimes takes a while to get full support for new chipsets in the linux kernel. The links I gave in posts 2 and 4 of this thread would suggest that your chipset should already work though.

---

### Post by YOURS3LF on 2009-03-17
> **tommcd said:**
> 
So go ahead and install Ubuntu.
Welcome to the cool side of computing!
Let me know how you made out. Your motherboard chipset is fairly new, so it sometimes takes a while to get full support for new chipsets in the linux kernel. The links I gave in posts 2 and 4 of this thread would suggest that your chipset should already work though.

I have used Ubuntu before and loved it. Last semester at my school I actually took a class specifically on how to work in a linux environment. It's just that when I installed on the computers at my school there were no install issues. Thank you much for assistance with my issues. I'll definitely be keeping Ubuntu and will definitely frequent these forums.

EDIT: Install complete, everything is running great so far. And again, thanks for your help!

---

