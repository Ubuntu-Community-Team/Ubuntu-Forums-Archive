---
title: "Switching from LILO to GRUB"
date: 2008-11-22
forum: General Help
---

### Post by madengineer on 2008-11-22
Hey all,

I'm running Kubuntu Hardy on X86_64, dual booting with Windows XP. I've just installed a new HD but am keeping the old RAID, and my BIOS doesn't seem to be able to decide which one is /dev/sda and which is /dev/sdb. This of course is wreaking havoc with bootup, since I'm using LILO (my root/boot partition used to be XFS, so I installed LILO rather than GRUB) and it can't do any of the smart things that GRUB can do to distinguish the drives.

I'd like to change to GRUB, but it doesn't appear to be as simple as installing the appropriate packages with apt-get. I've done that, but it doesn't construct the appropriate stuff for GRUB under /boot. I can try to construct it by hand, but I would be concerned that it wouldn't behave properly during kernel updates and the like. Can you suggest a better procedure for changing over?

Thanks!

---

### Post by caljohnsmith on 2008-11-22
How about first posting:
```
sudo fdisk -lu
```
And please identify your partitions. Also, if it's not too much trouble, how about downloading the "[Super Grub Disk]("http://www.supergrubdisk.org")", booting that, and when you get the main menu, press "c" to get the Grub command line, and then type the following:
```
grub> geometry (hd0)
grub> geometry (hd1)
```
Do you only get results from (hd0) and not (hd1)?

---

### Post by madengineer on 2008-11-22
**********************************************************************************

doug@ignatz:~$ sudo fdisk -lu

[sudo] password for doug:

Disk /dev/sda: 960.2 GB, 960205160448 bytes
255 heads, 63 sectors/track, 116738 cylinders, total 1875400704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9cbbe377

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    84566159    42283048+  83  Linux
/dev/sda2        84566160   100229534     7831687+  82  Linux swap / Solaris
/dev/sda3   *   100229535   220315409    60042937+   7  HPFS/NTFS
/dev/sda4       220315410  1875395969   827540280   83  Linux

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdcd8fca7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   142930304    71465121   83  Linux
/dev/sdb2       142930305   158947109     8008402+  82  Linux swap / Solaris
/dev/sdb3   *   158947110   586067264   213560077+   7  HPFS/NTFS

**********************************************************************************

/dev/sda1: old Linux root/boot partition
/dev/sda2: old Linux swap
/dev/sda3: old Windows partition
/dev/sda4: document storage partition

/dev/sdb1: current Linux root/boot partition
/dev/sdb2: current Linux swap
/dev/sdb3: current Windows partition

/dev/sda and /dev/sdb interchange sometimes; it seems that, if I first boot Windows and then reboot and let LILO go to Linux, it will find and boot from the old partition, and the Linux system that comes up will think of its root disk as /dev/sdb1. This suggests to me that my BIOS is interchanging the two disks in its boot order, since as I understand it LILO doesn't understand file systems, and so, if my machine were running the LILO install from the 300GB drive but erroneously accessing the 960GB drive, the offset at which LILO normally finds the kernel would point to something else and the system would not boot. Therefore, my plan is to wipe the MBR on the 960GB disk and install GRUB on the 300GB disk, specifying which disk is to be /dev/sda by hardware path.

Booting from the SGD, I get results from both (hd0) and (hd1); (hd0) is the 300GB disk, BIOS drive 0x80; (hd1) is the 960GB RAID, BIOS drive 0x81.

---

### Post by caljohnsmith on 2008-11-23
OK, that's great that (hd0) is your 300 GB drive, because that's the one you said you want to boot from on start up. How about going ahead and booting into your sdb1 linux partition and installing Grub as follows:
```

sudo grub-install --recheck /dev/sdb
sudo update-grub
```
The grub-install command will install Grub to the MBR of sdb and point it to the current partition you are in (sdb1) for its boot files; you should then be able to boot sdb next time you start up since sdb is first in the the BIOS boot order (hd0). The update-grub command will create a new menu.lst, and hopefully it will do a good enough job that you won't need to tweak it. Let me know how far you get or if you run into problems.

---

### Post by madengineer on 2008-11-23
That works fine; the system boots with no problems, and I don't get the sda/sdb swap occurring after rebooting from Windows. However, I'm still wondering how to make update-grub run automatically after kernel updates.

---

### Post by caljohnsmith on 2008-11-23
> **madengineer said:**
> That works fine; the system boots with no problems, and I don't get the sda/sdb swap occurring after rebooting from Windows. However, I'm still wondering how to make update-grub run automatically after kernel updates.
When you get a new kernel, at the end of the process it always asks you if you want to update your menu.lst with the changes; so if allow it to update your menu.lst, then you shouldn't have to run update-grub.

---

### Post by madengineer on 2008-11-23
Does that include kernels downloaded by the Adept updater? I never remember getting a prompt like that when I was running Kubuntu with GRUB set up by the installer; it just did the update to menu.lst automatically. Will that happen now that GRUB is set up?

---

### Post by fjgaude on 2008-11-23
I believe this feature started with 8.10, where you have the option to let the menu.lst file stay as it is or have it updated with a kernel update. Yes, it works that way with apt-get, Update Manager, and I'm sure with Aptitude.

---

