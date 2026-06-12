---
title: "Installing Ubuntu to an External USB hard drive"
date: 2011-06-16
forum: Hardware
---

### Post by Richbuntu on 2011-06-16
Hi,
I dual boot Ubuntu and Windows on my computer, but my Ubuntu runs on an old hard drive that really takes the fun out of using Ubuntu.
I decided to replace the old hard drive with a new external one and I've got a few questions (they might seem silly):
1) Can every computer boot from a USB hard drive?
2) What happens if I remove the USB hard drive (assuming that grub is installed on it), will I still be able to boot Windows?
3) Can I take the external hard drive with me and use Ubuntu wherever I want?

Thanks,
Elad

---

### Post by C.S.Cameron on 2011-06-16
External USB hard drives are limited to USB speeds, much slower than SATA.

Not every computer can boot USB but most newer ones can.

If you unplug your hard drive when making your external drive the new grub will nor effect your internal drive. Alternately use manual partitioning and make sure the bootloader is installed on the external drive. 

You can boot the USB drive on most other computers as long as you don't install proprietary drivers, (ATI, Nvidia).

Following a step by step for installing 10.10 and 11.04 to USB.

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Forward
At "Allocate drive space" select "Specify partitions manually (advanced)".
Forward
Confirm Device is correct.
(Optional partition for use on Windows machine)
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 4GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4 to 6 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4 to 8 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap space, allows hybernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB, same size as RAM), Beginning and "Use as" = "swap area" then OK.
(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

Some people prefer using NTFS for the first partition on a USB hard drive.

---

### Post by colin.p on 2011-06-16
When I got my Dell 1545 last year, I installed lucid to an external hd and used it that way for a month or so. If the USB drive was connected, it would boot into ubuntu, if it was removed, it would boot into 7. I made sure grub was installed to the external drive so as to not "frig" with the boot loader in 7.
It ran ok, fairly fast, but I was trying it to make sure everything worked.
After awhile, I installed lucid as a dual boot to the internal hd.

---

### Post by Richbuntu on 2011-06-20
I think I'll just buy a new internal hard drive.
Thanks for the Help

---

