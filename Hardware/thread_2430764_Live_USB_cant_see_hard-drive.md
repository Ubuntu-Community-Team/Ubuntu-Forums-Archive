---
title: "Live USB cant see hard-drive"
date: 2019-11-07
forum: Hardware
---

### Post by emera2 on 2019-11-07
**machine **
        dell inspiron 14 5000 
        only 1 SSD slot

    **goal**
        dual boot Linux alongside windows
   
**problem**
Normally I have always set up linux on a separate hard-drive to windows, but my Dell inspiron 14 5000 only has one hard-drive slot
When I boot into a live-usb, and run fdisk -l, gparted or the installer, the live usb cant see my hardrive. Ive tried this with mint and vanilla ubuntu

**other problems** (dont need to fix right now but might be related)
        the touchpad does not work on the live usb (external mouse works)
        manjaro live usb wont boot into GUI with free or non-free drivers

Thanks for any help

---

### Post by yancek on 2019-11-07
You neglected to indicate which release of windows you are using so we are left to guess.  Is it windows 8 or 10?  If so, the likely reason is that you have the default fast boot and hibernation on as no Linux OS will mount a hibernated system and thus will not be available or seen in the installer.  Turn off fastboot and hibernation and try again.  Also, try reading the Ubuntu documentation on dual booting with a windows UEFI system (if that is what you have) at the link below as it gives a lot of useful information.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2019-11-07
Dell typically needs UEFI update, if SSD firmware update.
It also needs drive(s) changed from RAID/Intel RST to AHCI. But if dual booting with Windows you must install AHCI driver into Windows first.

How to Install Ubuntu Linux on your Dell PC 
[https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en)

Intel or AMD based version? Issues common with Dell across many models, bigger differences if AMD or Intel based.

Dell Inspiron 15 5567 AMDGPU-Pro driver causes a kernel panic  Jan 2017
[https://ubuntuforums.org/showthread.php?t=2347889](https://ubuntuforums.org/showthread.php?t=2347889)

Dell  Inspiron 3670 UEFI update & AHCI worked
[https://ubuntuforums.org/showthread.php?t=2412152](https://ubuntuforums.org/showthread.php?t=2412152)

---

### Post by emera2 on 2019-11-07
Thanks for any input, sorry for leaving stuff out
**Info left out**
win10 
fastboot, secureboot and hybernation disabled
8 intel i5 cores
no dedicated GPU
up to date UEFI/firmware

I think the RAID is the problem, so I'll try swaping it

---

### Post by emera2 on 2019-11-07
I solved the problem by following this guide:
[http://triplescomputers.com/blog/uncategorized/solution-switch-windows-10-from-raidide-to-ahci-operation/](http://triplescomputers.com/blog/uncategorized/solution-switch-windows-10-from-raidide-to-ahci-operation/)

---

