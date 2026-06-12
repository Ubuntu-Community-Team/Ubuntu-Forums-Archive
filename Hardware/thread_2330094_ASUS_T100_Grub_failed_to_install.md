---
title: "ASUS T100 Grub failed to install"
date: 2016-07-07
forum: Hardware
---

### Post by Visseroth on 2016-07-07
OK, I just recently received a T100 and I've downloaded the 15.10 installer, put it to a flash drive and have successfully booted to the flash drive and connected to the wifi. However the Windows install was damaged, I'm not sure why and I believe something was wrong with the efi partition so I have since wiped the drive (/dv/mmcblk0) completely.
I've tried installing Ubuntu various different ways including creating a efi, boot and / partition and no matter what I try it always fails with "grub could not install /dev/mmcblk0".
So here I am now posting on this forum to see if I can get some help. I'd like to install directly to the internal SSD but I'm not having any luck and I'm not sure what to do next. Any help would be appreciated.

---

### Post by yancek on 2016-07-07
You need to start by reading the Ubuntu documentation page at the link below for dual booting with windows using UEFI.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2016-07-07
Several things:
 The ASUS "Bay Trail" T100 Is Not Linux Friendly
[http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE)
Bay Trail freeze need boot parameter: intel_idle.max_cstate=1 or patches, see comments
[https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051)
Many Intel Bay Trail Devices Have Been Borked On Linux For The Past Year - Mar 2016
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail) 

Is the T100 one of the limited 32 bit UEFI systems? They made those to prevent Linux as then Linux did not have a 32 bit UEFI. And even now it is not totally easy.

 But someone has it partially working:
[http://liliputing.com/2013/10/booting-ubuntu-asus-transformer-book-t100.html](http://liliputing.com/2013/10/booting-ubuntu-asus-transformer-book-t100.html)
Asus T100 Compile own grub 32 bit
[http://ubuntuforums.org/showthread.php?t=2191557](http://ubuntuforums.org/showthread.php?t=2191557)
 ASUS Transformer Book T100TA that was one of the early Intel Bay Trail convertible laptops/tablets. 
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI) 

Some Bay Trail work better with 14.04 as newer kernels have issues.

And Ubuntu 15.10 (Wily Werewolf) reaches End of Life on July 28 2016

You should not have to compile 32 bit UEFI/grub, but can download the 32 bit UEFI files.
 bootia32.efi

Details on another system.
 [https://github.com/lopaka/instructions/blob/master/ubuntu-16.04-install-asus-x205ta.md](https://github.com/lopaka/instructions/blob/master/ubuntu-16.04-install-asus-x205ta.md)

---

