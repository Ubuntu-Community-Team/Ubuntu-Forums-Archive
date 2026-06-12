---
title: "re-formatted hdd install from live usb"
date: 2012-06-06
forum: Hardware
---

### Post by killer62491 on 2012-06-06
ok so i wanted to install Ubuntu 12.04 on my Acer Aspire 9410 laptop, and i wanted to only have Ubuntu on the hard drive, as my windows install was ridiculously messed up. the laptop isn't even booting into it (the Windows inst.) anymore. so i went and downloaded partedmagic to reformat the HDD, but i don't know what filesystem type to format it to to put Ubuntu on there alone. i did some digging into that on here not much luck, i've had people tell me to do FAT32, but others say it wont work with that, unless Windows will be there as a host OS. i'm seriously confused here for filesystem type, FAT32, or EXT2? and once i do that, will i be able to use the partedmagic's Unetbootin to install Ubuntu on it via Hard Disk mode (i've seen other people use Unetbootin for Hard Drive writes, i know its possible)? Also,  LiveCD is a no-go, as when i boot to it, i get a gfxboot error, which is simply this: 
"could not setup gfxboot". when this message appears, it stays for about 10 seconds, then it retries the setup (i think) and gives same error message every time it does so.

---

### Post by 1Yeoj1 on 2012-06-06
Go online to [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) and if you can reinstall a Live CD or a Live USB._ If it is on Windows_ then Ubuntu will tell you where you need to go to download a installer that will install it onto a Live CD or USB. _If you are on another Ubuntu computer _then the installer is already on it and all you need is the .iso.
Once you have an install disk... All you have to do is plug it in and choose to format the drive and install Ubuntu. It will warn you that all of your information will be erased so if you need to keep something get it first.

Yeoj

---

### Post by killer62491 on 2012-06-06
> **1Yeoj1 said:**
> _ If it is on Windows_ then Ubuntu will tell you where you need to go to download a installer that will install it onto a Live CD or USB. _If you are on another Ubuntu computer _then the installer is already on it and all you need is the .iso.
Once you have an install disk... All you have to do is plug it in and choose to format the drive and install Ubuntu. It will warn you that all of your information will be erased so if you need to keep something get it first.

i HAVE an installation CD, but when i put it into the drive and boot from it, it says that error i mentioned, about "gfxboot". my HDD is OS trashed, it wont boot into the Windows XP which is on it. if it was able to, i would have been fine and dandy, but it isn't like that. so basically, i need to reformat my HDD, also, my only thumbdrives are 512M ones. (i know, i'm in serious need of a newer one.) the only things i have larger than those are my SD cards, which for some reason, my laptop isn't reading as bootable. if i could make it read THAT as bootable i'd be set too. the only way i can think of is to re-format my HDD to a proper FS to write my ISO from my SD card to my HDD, then see if it'll boot. again, i need to know WHAT FS TYPE TO FORMAT TO...

---

### Post by 1Yeoj1 on 2012-06-06
I will try to breakdown your question. 1) You need to format it as EXT4 for the best results. 2) You may try a Local Library for a computer to reload. 3) You _**may be able**_ to boot an SD card but you will need to go into BIOS to that. In the BIOS options there is the ability to change the order and possibly the SD option is turned off. On my BIOS, for example, floppy boot is turned off. 
Bye the way 2 GB flash drives are about $8 at Wal-Mart and 4 GB are like $2 more (SanDisk)

Yeoj

---

### Post by wilee-nilee on 2012-06-06
You could easily use the mini cd to do a netload with your usb/thumb.

You don’t have to format before installing with this or a regular cd, it is done in the install, ext4 is your goal.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by oldfred on 2012-06-06
From a flash drive you may need to add some boot parameters:

If booting from USB it just may be easier to edit syslinux with whatever boot parameters you need like this:
Ubuntu 12.04 has been officially released and, with minor adjustments, the intel gma500 video card is working out of the box.
[http://blog.bodhizazen.net/](http://blog.bodhizazen.net/)
simply edit “syslinux.cfg”
How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

How you partition depends a lot on what you plan to do. One suggestion on partitioning:
For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

