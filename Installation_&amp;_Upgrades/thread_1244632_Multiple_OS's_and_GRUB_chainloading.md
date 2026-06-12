---
title: "Multiple OS's and GRUB chainloading"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by tnek on 2009-08-19
Hi,

I want to have multiple OS installations and I have been advised that chain loading using GRUB is a good way to handle this. I have looked at tutorials on the web but I still have some questions before I can start.

I want:

[LIST]
[*]Windows XP: 20 GB. For running some school stuff and a game which does not work through WINE.
[*]Xubuntu 9.04: 85 GB. My main OS.
[*]Another Linux distribution: 15 GB . For experimenting and trying Linux distributions out.
[/LIST]
I will:

[LIST]
[*]Wipe and install various distributions quite often on the 15 GB.
[*]Use dd to make a copy of my Windows partition after installing it and getting things to work as I like. My experience is that Windows needs to be re-installed maybe once per year to not get bloated and slow.
[/LIST]
I have been told:

[LIST]
[*]To use GRUB chain loading. It will make it easier when kernel upgrades are made in the Linux distributions, as they modify the GRUB boot-menu.
[/LIST]
To my understanding I need to:

[LIST=1]
[*]Install Windows first.
[*]Then install Xubuntu and let it write over the MBR with GRUB (I guess this is the default).
*Now things aren't so clear anymore. I need to... Eh.. .I guess I need to:*
[*]Get the GRUB on the MBR start Windows XP if I want to (it's done by default), start Xubuntu using the kernel of my choice **or** defer execution to the boot sector of my other Linux distribution. The actual chainloading will only occur when I want to start my experimental install of Linux.
[/LIST]
I wonder:

[LIST]
[*]Is step 3 above correct and a good way to handle this?
[*]Is it also a good way to use chain loading for both Xubuntu and my experimental Linux installation?
[*]How do I get a Linux distribution to install the boot loader it comes with to the boot sector of its partition and _not_ to the MBR?
[*]If I can't get it to not touch the MBR. Then I could make a backup of the MBR using dd and then write it back after installing my experimental Linux installation. But then, how would I get the boot loader (lets say GRUB) into the boot sector of the experimental Linux installation? How would it work if said Linux installation gets a new kernel update and needs to update the GRUB menu?
[/LIST]
Thank you for reading. I hope I can get some expert advice. :)

---

### Post by louieb on 2009-08-19
> I will: Wipe and install various distributions quite often on the 15 GB.

You may have to look for it but every Linux distribution I have install will have a where to install grub option sometime during the install. That is were you will get it to put GRUBs stage1 code in the boot sector of its partition. 

And if you miss it and it gets installed in the drives MBR. Easy enough to fix from the **grub>** prompt.
Nice reference here on how to this and that with GRUB. [IDBS GRUB Page]("http://members.iinet.net.au/%7Eherman546/p15.html")

> How would it work if said Linux installation gets a new kernel update and needs to update the GRUB menu?
Nice thing about chainloading or using the configfile option each Linux install keep its own menu.lst, and handles it own updates..  
> To my understanding I need to: 1,2,3

You'll do fine using this plan.

---

### Post by presence1960 on 2009-08-19
1. Install Windows.
2. Install Xubuntu. The GRUB bootloader will be put on MBR of disk by default.
3. install other Linux distro. This is where you have to be careful. Always install GRUB of the new distro to the partition that distro is installed on. This will allow you to chainload it off xubuntu's GRUB menu. If you put it on MBR you are cooked.

Here is my fdisk output:
```
raz@raz-desktop:~$ sudo fdisk -l
[sudo] password for raz: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d179

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7833    62918541    5  Extended
/dev/sda2            7834       25064   138408007+  83  Linux
/dev/sda4           25065       30401    42869452+   7  HPFS/NTFS
/dev/sda5               1        2350    18876312   83  Linux
/dev/sda6            2351        2872     4192933+  82  Linux swap / Solaris
/dev/sda7            2873        5222    18876343+  83  Linux
/dev/sda8            5223        7833    20972826   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a57e45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux

Disk /dev/sdg: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00079662

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1         115      923706    b  W95 FAT32
/dev/sdg2             116        9964    79112092+  83  Linux
raz@raz-desktop:~$
``` 
sda1 is extended containing : sda5-ubuntu 9.04, sda6-swap, sda7 Mint5, sda8-sabayon 4.1
sda2 is ext3 data partition
sda4 is Windows 7
sdb1 is ext3 data partition

I have my back up disk plugged in -sdg 

Ubuntu's GRUB is on MBR of first disk, I chainload MINT, Sabayon & windows off that. here is my menu.lst file from Ubuntu for the chainloaded items:

```

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Windows Vista (loader)
rootnoverify	(hd0,3)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Linux Mint x64 (on /dev/sda7)
root	        (hd0,6)
chainloader     +1

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2

title           Sabayon 4.1
root		(hd0,7)
chainloader     +1
```

---

### Post by oldfred on 2009-08-19
[I]How to multiboot: 
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817) 
 
comment in above. 
[/I]By far, the easiest way to do this is to install grub BOTH to the MBR and your root (or /boot) partition with each install.

There are many instructions and several ways to reinstall GRUB into the MBR including supergrub and using the install CD. You do need to understand partitions and which partition is which so when you do have to edit menu.lst to add a chainboot you know which is which.

I have not had any issues as I have only chainbooted versions of Ubuntu. I understand some versions are a little more difficult.
See also:
boot 145 systems - it is older but has been somewhat updated and discusses many issues of different ooperating systems.

[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

---

