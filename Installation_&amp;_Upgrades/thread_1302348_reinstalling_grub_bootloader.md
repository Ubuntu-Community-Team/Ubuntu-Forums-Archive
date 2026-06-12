---
title: "reinstalling grub bootloader"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by rayerta on 2009-10-27
Hi,
  I need help getting Windows running again after reinstalling GRUB - I'm running a dual boot system and here is the output from fdisk:

Disk /dev/sda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3ab1acba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1402    11261533+   7  HPFS/NTFS
/dev/sda2            1403        3648    18040995    f  W95 Ext'd (LBA)
/dev/sda5            1403        1784     3068383+  82  Linux swap / Solaris
/dev/sda6            1785        3648    14972548+  83  Linux

and my GRUB menu entry for Windows currently reads:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
savedefault
chainloader	+1

however, when i select the Windows option while booting, the screen very briefly says something like "GRUB loading stage 2" and then returns to the menu. Ubuntu boots fine.

---

### Post by sliketymo on 2009-10-27
> **rayerta said:**
> Hi,
  I need help getting Windows running again after reinstalling GRUB - I'm running a dual boot system and here is the output from fdisk:

Disk /dev/sda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3ab1acba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1402    11261533+   7  HPFS/NTFS
/dev/sda2            1403        3648    18040995    f  W95 Ext'd (LBA)
/dev/sda5            1403        1784     3068383+  82  Linux swap / Solaris
/dev/sda6            1785        3648    14972548+  83  Linux

and my GRUB menu entry for Windows currently reads:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
chainloader    +1

however, when i select the Windows option while booting, the screen very briefly says something like "GRUB loading stage 2" and then returns to the menu. Ubuntu boots fine.

:popcorn: What caused you to have to re-install grub ?

---

### Post by rayerta on 2009-10-27
I had to reinstall Windows XP, so I loaded a live version of Ubuntu on a USB key and used grub-install to recreate the GRUB bootloader (i followed the instructions from [Ubuntu Help]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")):

mkdir /media/root

mount /dev/sda6 /media/root

sudo grub-install --root-directory=/media/root /dev/sda6

---

### Post by sliketymo on 2009-10-27
> **rayerta said:**
> I had to reinstall Windows XP, so I loaded a live version of Ubuntu on a USB key and used grub-install to recreate the GRUB bootloader (i followed the instructions from [Ubuntu Help]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")):

mkdir /media/root

mount /dev/sda6 /media/root

sudo grub-install --root-directory=/media/root /dev/sda6

  Scroll down to the middle of the page you got your earlier instructions from.There is information on restoring your windows bootloader. You may have to insert your windows install disk,and fix you xp boot MBR  first.

---

### Post by Shakeysteve on 2009-10-27
Check out [http://apcmag.com/howto_home.htm](http://apcmag.com/howto_home.htm) 
Excellent step by step guides on how to dual boot.

---

### Post by oldfred on 2009-10-27
If when you select windows from the menu.lst and you get another grub loading screen you must have installed grub into hd0,0, the windows partition not just hd0. The partition hd0,0 needs also to have windows boot into it. The normal repair of windows are two commands one fixes the mbr and the other fixes the partition.

This set of commands total recovers windows, I do not know if you can run just the fixboot and solve you problem. If not do the total fix, make sure windows boots, then reinstall grub.

To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

FIXMBR  C:
FIXBOOT  C:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
BOOTCFG  /rebuild

---

### Post by rayerta on 2009-10-28
thank you oldfred for helping me understand what happened. I won't have the opportunity this time to try out your solution (i completely reinstalled windows and then ubuntu - the ubuntu installer knew what to do and set it up right), but I will remember it for the next time.

---

