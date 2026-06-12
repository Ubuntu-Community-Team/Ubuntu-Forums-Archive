---
title: "Explain how to install Win2000 after Ubuntu"
date: 2009-03-14
forum: Installation &amp; Upgrades
---

### Post by BudE on 2009-03-14
Good morning,

I have recently installed Ubuntu 8.04 and seem to like it so far. However, I need to run a few programs that are Windows specific for my son. I inserted my Windows 2000 Pro cd and boot up the computer, which boots straight into Ubuntu. When I reach the desktop I can see the cd is there, but can't run the "exe" file and have been told that won't work in Ubuntu. HOW then can I go about installing Win2K so that I can dual boot both systems? I am a newbie so please go slow and clear please  :)
Oh, I have 2 partitions:
/dev/sda1...ext3   is where I installed Linux
/dev/sda3...NTFS   is where I hope to install Win2K
/dev/sda2...extended
/dev/sda5...linux-swap


have a nice one,
Bud   :D

---

### Post by Shazaam on 2009-03-14
You have a few options here.
1. Go into your pc's bios (the boot screen should tell you what key combo to press) and make the cdrom first in the bios boot order. The Windows disk should then boot. Remember, Windows likes to be installed first on the  hard drive and will cause problems with Ubuntu/grub. Fixing that may be as easy as reinstalling grub or using something like a SuperGrubDisk.
2. If the program that your son needs is not graphics intensive you might consider installing something like VirtualBox or VMware on Ubuntu. This will allow you to keep your pc as-is and install Windows as a virtual machine (on top of Ubuntu).

---

### Post by BudE on 2009-03-14
> **Shazaam said:**
> You have a few options here.
1. Go into your pc's bios (the boot screen should tell you what key combo to press) and make the cdrom first in the bios boot order. The Windows disk should then boot. Remember, Windows likes to be installed first on the  hard drive and will cause problems with Ubuntu/grub. Fixing that may be as easy as reinstalling grub or using something like a SuperGrubDisk.
2. If the program that your son needs is not graphics intensive you might consider installing something like VirtualBox or VMware on Ubuntu. This will allow you to keep your pc as-is and install Windows as a virtual machine (on top of Ubuntu).

Shazaam,

Thanks, I will try that. Which is best of the two? So when installing these I can run Windows programs without even having to install Windows itself? Wonderful. So just install either and then pop in my program cd's with the Windows type programs and that's it?

Bud

---

### Post by Shazaam on 2009-03-14
When you run a virtualization program such as VirtualBox you would install Windows (or any other os) to a "virtual" hard drive. Then when you are running the host os (Ubuntu or any other os) you can start up the "virtual" (guest) os to run at the same time. That way you don't have to carve up your real hard drive(s). Here is a good post to read...
[http://ubuntuforums.org/showthread.php?t=973756](http://ubuntuforums.org/showthread.php?t=973756)

---

