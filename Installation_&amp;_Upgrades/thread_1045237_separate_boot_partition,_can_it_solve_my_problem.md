---
title: "separate /boot partition, can it solve my problem?"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by RyanVanDiemen on 2009-01-20
Hi all,
I have a weird problem I haven`t encountered before. I dual-boot WinXP and (currently) Ubuntu 8.10. The problem is that whenever I try to install another Ubuntu distribution (Xub, Kub) or some other Linux distro (apart openSUSE, it works fine) it sometimes doesn`t recognize WinXP system and even cannot load linux distro that was installed before. Basically everything works just fine only when it`s the first and only Linux installed on system. 

I`m thinking about creating separate /boot partition but I don`t really know how this works.
Here`s what I think. I would install first Linux on top of WinXP and make a backup of menu.lst file. During installation of another Linux distro I would tell him to use /boot partition of the first Linux, he would create it`s own menu.lst (possibly re-writing original one) and after that I can easily go to /boot and edit menu.lst and add the lines from my backup of the original menu.lst.
Can you, please, advise if this is how it works or what should I do to have more distros installed? This must be some new problem because I`ve never had this problem before...


I have 2 HDDs and primary one is SATA, secondary is IDE. Problem might be that Linux usually consider IDE disc as sda and SATA as sdb. That`s why installer creates GRUB menu with WinXP in wrong partition. I can easily edit menu.lst and tell him where to look for WinXP partition, the biggest problem is that it somehow wrongly recognize the original linux installed on the system.

I hope it doesn`t sound too confusing...

One more thing: why am I not able to choose in Ubuntu where should it install GRUB? It is a possibility on some distros, I`d love to have it in ubuntu too...

---

### Post by caljohnsmith on 2009-01-20
With Ubuntu, you can specify where Grub gets installed by clicking the "advanced" button near the end of the installation process. There you can specify to have Grub installed to /dev/sda or whichever drive you want, or have Grub installed to the boot sector of a partition by using something like /dev/sda2. Also, I woudn't recommend trying to share the same boot partition with multiple distros, or I'm not sure if that is what you meant, but that unfortunately can cause problems. Editing the menu.lst to add Windows or another Linux distro as a boot option is usually not a big deal, so if the Linux distro you install doesn't add them to Grub by default, I can help you add them if you want. If you want a hand with it, how about posting:
```
sudo fdisk -lu
```
And please identify your partitions; we can work from there if you want.

---

### Post by RyanVanDiemen on 2009-01-20
Thank you for your reply. I wanted to share as much information as possible and the point was lost in text... :-) 

That actually helps me a lot, to be honest I noticed advanced button but never tried it before (never needed it until this GRUB problem). I will probably install GRUB for the second distro at the beginning of its partition and then edit GRUB in MBR and add the line to this second distro. Thanks a lot.

What I actually wanted is the opinion of people about sharing the same /boot partition for more distros. You mention it can cause problems. What kind of problems?

PS: I think I have my problem solved (advanced button helps :-) ) but I will keep it open for now for opinion and experience about sharing /boot partition.

---

### Post by caljohnsmith on 2009-01-20
> **RyanVanDiemen said:**
> 
What I actually wanted is the opinion of people about sharing the same /boot partition for more distros. You mention it can cause problems. What kind of problems?

Well, if you are really careful, sharing a boot partition can be done I think. You just would want to make sure that each distro has its own separate kernels/initrd and other boot files, because if one distro overwrites another distro's boot files, that will most likely cause problems. So you could for instance manually rename your boot files so there is no ambiguity, and that will also help prevent them from being overwritten:
```
vmlinuz-2.6.27-9-generic-[COLOR="Blue"]Ubuntu[/COLOR]
initrd.img-2.6.27-7-generic-[COLOR="Blue"]Ubuntu[/COLOR]
...etc.
```
Something like that would work I think. But why do you want to share a boot partition between distros? Off-hand I don't see any advantage of doing that.

---

### Post by dabl on 2009-01-20
> **RyanVanDiemen said:**
> 

What I actually wanted is the opinion of people about sharing the same /boot partition for more distros.



That strikes me as a bad idea, although I'm not sure I can say precisely what will go wrong.  I suspect some of the stage 1 files that are normally located in /boot are not all the same, but they may have the same names -- moreover, what are you going to do about the /boot/grub subdirectory -- I would think you can only have one?

What benefit would you hope to achieve with this approach?  With hard drive space selling for ten cents per Gigabyte, you can't be worried about the 40MB or whatever that a /boot directory and its files consume.   :confused:

---

### Post by RyanVanDiemen on 2009-01-20
> **caljohnsmith said:**
> But why do you want to share a boot partition between distros? Off-hand I don't see any advantage of doing that.

> **dabl said:**
> 
What benefit would you hope to achieve with this approach?  With hard drive space selling for ten cents per Gigabyte, you can't be worried about the 40MB or whatever that a /boot directory and its files consume.   :confused:

Thanks guys. I really confused you..:D It wasn`t the space issue. My problem is that whenever I try to install second distro on the same computer it always messes up my GRUB (have small idea why this happens). To be honest I didn`t think about other boot files, just GRUB. The idea behind sharing /boot partition was that I will keep everything in one place and after installer messes up my menu.lst file I will re-write it with back-up created originally and just update it with info for new distro. That was however before I realised I can tell installer where it should install GRUB (completely ingored Advanced button before). 

I thought sharing /boot partition is common, but I guess it`s really not a good idea... ;) thanks guys again

---

### Post by Herman on 2009-01-20
:) What you want is a 'Dedicated GRUB Partition, not a 'Separate Boot Partition'.

A '**Seperate Boot Partition**' is hard to share between two or more Linux distros, and it's really only for curing GRUB Error 18 in old computers with hard disks that are larger their  BIOS can map. 
A separate /boot partition is normally made with the Ubuntu, (or any distro's) partititioner at installation time and registered as /boot during the installation process. That means it is listed in the /etc/fstab file as that operating's /boot partition and that's where the operating system will keep it's kernels and initrd.img file and other important files.
The update-grub script from that operating system will own the menu.lst file, and update it when there's a kernel update.
If you really need to share a /boot partition between another distro, it's a real pain in the behind because they both think they own the menu.lst, and they'll fight over it, (to put it simply). 
To stop that, you have to rename one of the menu.lst files 'menu.lst_2nd or something, and then go edit the /etc/update-grub script and make it point to the alternative menu.lst, which isn't a job I would recommend for newcomers unless it's unavoidable.
The only good thing about it is it 'fences' the kernels in, and forces them to be written to disk inside the hard drive limit, (commonly 8.45 GB), which was the furthest some old BIOSes could address. Unless you have a very old computer, (more than 10 years old), you probablt don't want a 'Separate /boot'. 
They're still used today for special purposes such as when an encypted / is needed or maybe for setting up some RAID arrays maybe, I'm not sure. 

A '**Dedicated GRUB Partition**', is a partition that contains only GRUB files, and is operating system independant. This is the kind of GRUB partition that's great for anyone who likes GRUB, and wants to multi-boot. A 'Dedicated GRUB partition can be anywhere in a hard disk, and doesn't take up very much room at all.
The term 'Dedicated GRUB Partition', was probably coined by the web author Steve Litt, in his article ' [Making a Dedicated Grub Partition]("http://www.troubleshooters.com/linux/grub/grubpartition.htm")'.


Regards, Herman :)

---

### Post by Herman on 2009-01-20
If you have read that article by Steve Litt, you should understand by now what I mean by a 'Dedicated GRUB Partition'.

The easiest way to make yourself a 'Dedicated GRUB Partition', is to just create a new partition with Gnome Partition Editor, you don't have to use fdisk. 
It only needs to be 100 MiB or so, I prefer a little more room for adding splashimages and whatnot.
It can be located anywhere on the hard disk. (On any hard disk too).

I like ReiserFS instead of Ext2 or Ext3 for this job, because with ReiserFS, the stage1_5 can be installed in the partition too, (I'm not sure if it makes any difference, by it seems like a good idea), and also if hard drive space is any concern, ReiserFS seems to have less overhead. It really doesn't matter too much what file system you use.

Then you just need to copy all your /boot/grub files to it.

You can chmod it to make it easier to edit the menu.lst, and you can remove all the Ubuntu-specific stuff from the dedicated GRUB's menu.lst file. You can delete the entire automagic kernles list, for instance.

Replace all the direct kernel booting entries with chainloader commands.

All the operating systems you install can be installed with their boot loaders installed to the partition boot sector of their own partitions. Then, to boot them, you just need to edit your Dedicated GRUB's menu.lst, with a new chainloader command for each new OS you add.
Here's a link that might help you, [Operating System entries for multibooting other Linux Systems]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems").

Regards, Herman :)

---

### Post by RyanVanDiemen on 2009-01-21
Thank you Herman, that`s perfect link you pasted (GRUB one), I tried to search for something similar some time ago, but never have I found something so constructive.

I will "solve" my problem by either editing menu.lst whenever each new installation messes it up or by simply installing GRUB to the beginning of each distro partition and pointing master GRUB to it. 

Perfect, thank you all...

---

### Post by dabl on 2009-01-21
In addition to Herman's excellent method, which involves a separate partition for Grub files, you may wish to consider the benefits of using the "configfile" pointer to the other OS(s) that you want to boot from your main menu.lst.  As Herman says, only one OS can control your menu.lst file, and it will update it when a new kernel is installed, or whenever update-grub is run.  However, you can take advantage of this fact by installing Grub in the partition root, not the MBR, for other OS's that you wish to boot, and then using "configfile" in your main menu.lst file to point to them.  For example, on my system with two bootable OSs, Kubuntu owns and operates the menu.lst file that is the main boot menu. sidux has its Grub installed in the sidux /boot/grub filesystem.  Here is the part of the Kubuntu menu.lst that shows the on-screen boot menu -- notice the line that points to sidux:

> 
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=4ee99d57-a4e3-4381-a900-7a57cfa9eea2 ro vga=837 quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=4ee99d57-a4e3-4381-a900-7a57cfa9eea2 ro vga=837  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4ee99d57-a4e3-4381-a900-7a57cfa9eea2 ro vga=837 quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4ee99d57-a4e3-4381-a900-7a57cfa9eea2 ro vga=837  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title .
root

title Other operating systems:
root

title .
root

title	Debian sidux GNU/Linux on hd4,0
configfile (hd4,0)/boot/grub/menu.lst


This way, sidux can be updated with new kernels when needed, or have older kernels removed, and it will maintain its own menu.lst file, and I don't have to edit anything, ever.

:)

---

### Post by RyanVanDiemen on 2009-01-21
> **dabl said:**
> you can take advantage of this fact by installing Grub in the partition root, not the MBR, for other OS's that you wish to boot, and then using "configfile" in your main menu.lst file to point to them.
:)

Yes, this is exactly how I`m gonna do it. Thanks dabl for your post.

---

