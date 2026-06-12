---
title: "Boot after First Stage Installation Fails"
date: 2005-01-28
forum: Installation &amp; Upgrades
---

### Post by vadude on 2005-01-28
During installation of Ubuntu, the first stage went very well and automatically - chose automatic mode for full disk.  At installation of boot loader it found my WinXP operating system, ejected the disk, and told me to hit ENTER. I did so and reboot started but failed with an "Error 21" message - system froze. The full message was:

Verifying DMI pool data
Boot from CD:
Boot from CD:
GRUB loading stage1.5
Grubloading, please wait
Error 21

Can anyone help??

---

### Post by nikopol on 2005-01-28
[QUOTE=vadude]During installation of Ubuntu, the first stage went very well and automatically - chose automatic mode for full disk.  At installation of boot loader it found my WinXP operating system, ejected the disk, and told me to hit ENTER. I did so and reboot started but failed with an "Error 21" message - system froze. The full message was:

Verifying DMI pool data
Boot from CD:
Boot from CD:
GRUB loading stage1.5
Grubloading, please wait
Error 21

Can anyone help??[/QUOTE]
 I had this one and _I think_ I used a DOS boot disk to wipe the MBR with a fdisk /mbr and then reinstalled Grub but I wouldn't bet on it 100%. Sorry the advice isn't anymore set in stone :(

---

### Post by Buffalo Soldier on 2005-01-28
According to [GRUB manual](http://www.gnu.org/software/grub/manual/grub.html) error 21:

> Selected disk does not exist
This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. 

How about giving more details about your installation?
- Where did you install GRUB? in the MBR?
- What is your harddisk like? In which partition was WinXP and in which partition did you installed Ubuntu?

From what I know I can only guess that GRUB couldn't find your Ubuntu because it was refered to different partition than the partition where Ubuntu is residing on. 

OR, your BIOS is reporting your harddisk wrongly. How about changing (in BIOS) your harddisk from LBA to Normal or Auto.

Here's a thread I post earlier that could point you to some helpful links [http://ubuntuforums.org/showthread.php?t=13042](http://ubuntuforums.org/showthread.php?t=13042)

---

