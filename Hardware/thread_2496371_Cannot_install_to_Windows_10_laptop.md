---
title: "Cannot install to Windows 10 laptop"
date: 2024-03-25
forum: Hardware
---

### Post by guy14 on 2024-03-25
The installation usb process does find the hdd in the laptop.
Is there something special on some hdd in WINDOWS PC to make them visible?

More info:
This laptop belongs to a friend , it had WIN10, he tried upgrading to WIN11.  Afterwards the laptop only boots into the bios.  I planned on installing Linux on the laptop but Live OS cannot see the internal HDD to resque any existing files.  In trying to do an installtion fails as the install process only sees the USB drive which doesn't have sufficient space for a WINDOWS install.

---

### Post by oldfred on 2024-03-25
You cannot install Windows to an external drive. Just the installer. And best to make USB flash drive installer from Windows as its ISO now uses a .wim file that is too large for the required FAT32 UEFI boot partition. It automatically splits the .wim file when making the installer.

Windows has fast startup & bitlocker which prevent Linux NTFS driver from correctly seeing any drive that is then locked.
turn off bitlocker & shutdown Windows so fast startup does not set the hibernation flag on all NTFS partitions.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/](https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/)

If you want to keep Windows use Windows tools to shrink NTFS partition to make unallocated space for Ubuntu install.

Have you updated UEFI and SSD firmware?
Is/are drives set in AHCI mode?
Is Windows fast start up off?
Some other settings:
UEFI & Windows Settings for UEFI install  - tea for one 
[https://ubuntuforums.org/showthread.php?t=2467629&p=14061395#post14061395](https://ubuntuforums.org/showthread.php?t=2467629&p=14061395#post14061395)
[https://ubuntuforums.org/showthread.php?t=2461231](https://ubuntuforums.org/showthread.php?t=2461231)

[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

---

### Post by guy14 on 2024-03-25
Thanks, lots of info to get a handle on. 
Some additional info since first posting:
I down loaded WIN10 ISo and copied it to a VENTOY usb stick.  It can boot and offers the option to install Windows or do a repair.  The various repair options fail I also downloaded WINDOWS PE.  It boots a minimal Windows OS and it also cannot see the HDD.

---

### Post by yancek on 2024-03-26
As explained above, the default on newer windows 10/11 is to leave the system hibernated.  When you tried to install Linux, it did not mount the partitions filesystem as they were hibernated and the risk of data loss is high.  You would need to turn off hibernation and check the other suggestions in post 2 before trying to install Linux.

Posting that the various repair options fail in your attempt to install windows is a bit pointless unless you explain exactly what failed/happened and any error or warning messages you got.  If you are now trying to install windows, why don't you go to the microsoft support site or a windows forum since they should be more likely to be able to help.

How old is this hardware?  Were there any problems with the drive prior to the failed attempted to upgrade to windows 11?

---

