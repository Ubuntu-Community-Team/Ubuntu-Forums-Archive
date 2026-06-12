---
title: "Installer does not find my EIDE drive"
date: 2009-10-13
forum: Installation &amp; Upgrades
---

### Post by SublimeHiPpOs on 2009-10-13
Hello all. I'm a novice Ubuntu/Linux user, but pretty experienced in the Windows world. I've casually used Ubuntu in the past and want to install it on my new build.

The new system has two SATA DVD drives and two SATA HDDs, as well as an older 160GB EIDE drive that I wish to install Ubuntu on. The BIOS and Windows recognize all drives just fine, so I konw they're all working and configured correctly. I've tried having the EIDE drive as the master and on Cable Select, either way, the Ubuntu installer only recognizes my two SATA HDDs. Any ideas on how I can get it to allow me to install to the EIDE drive?

Thanks in advance!

---

### Post by lindsay7 on 2009-10-13
is the ide drive formatted?  Are you going to have a dual boot system on this computer. If so are you going to put the os's on separate drives or on the same drive.

---

### Post by 123456789123456789123456 on 2009-10-13
> **SublimeHiPpOs said:**
> Hello all. I'm a novice Ubuntu/Linux user, but pretty experienced in the Windows world. I've casually used Ubuntu in the past and want to install it on my new build.

The new system has two SATA DVD drives and two SATA HDDs, as well as an older 160GB EIDE drive that I wish to install Ubuntu on. The BIOS and Windows recognize all drives just fine, so I konw they're all working and configured correctly. I've tried having the EIDE drive as the master and on Cable Select, either way, the Ubuntu installer only recognizes my two SATA HDDs. Any ideas on how I can get it to allow me to install to the EIDE drive?

Thanks in advance!

Question one, how does the BIOS reconize the drive, as hard drive 3 or 4?  If for some strange reason you have two IDE connectors/headers on the motherboard, you need to jumper the drive possibly as CS(cable select), and plug it into IDE header 1 on the motherboard.  Plugging it into the second one will cause the drive to be reconized only as a secondary non boot device.  Question 2, with so many SATA drives, your BIOS and motherboard may consider the IDE drives as non bootable, which could cause Ubuntu not to reconize it, so that it would not install on a non boot device.  Make sure that the BIOS is set to boot from IDE drives.
The only other question would be is the drive formatted in a format Ubuntu does not understand, but that should not make a difference as that the installer will erase the disk if needed to install the OS on.  Only other possibility I can think of is that the drive could have been through a zero out process that was ended prematurely, that would result in the BIOS reconizing the disk, but WIndows, and Ubuntu would not reconize the disk, that makes no since since you said windows reconized it.
Without looking at the BIOS and motherboard, it is hard to tell exactly what the problem is.

---

### Post by SublimeHiPpOs on 2009-10-14
Thanks for the replies!

Originally the drive was formatted w/ a NTFS file system (was used for data backups.) Earlier on I tried reformatting and now it has no partitions.

When I boot the BIOS posts the drive as IDE1 MASTER.

For kicks I booted w/ my Windows 7 install DVD, the Windows installer found all three drives and listed this drive as drive 0.

I have a ASRock X58 Extreme motherboard which only has one IDE connection. I am using an IDE cable with only one plug (for a cleaner install since I'm only using one IDE drive.)

I tried making the IDE the first boot disk, then running the install, but I still got the same result.

All this is making me think it's an Ubuntu issue.

---

### Post by SublimeHiPpOs on 2009-10-14
No surprise, but when running Ubuntu from the cd, the IDE drive is not recognized. I also tried GParted to see if it could find the drive.

---

### Post by oni5115 on 2009-12-05
I assume that its because the board has merged its IDE controller with something else (firewire I think) and that linux doesn't have drivers for this funky merge yet.  Or something along those lines.  I saw something like that in a newegg review.

Kinda makes me sad because I can't seem to get a live CD to work and my SATA HD won't be in for 4 more days.

Going to try making a USB stick now.

Edit: Yeah check this thread - [http://ubuntuforums.org/showthread.php?t=1341264&highlight=ASRock+x58+extreme](http://ubuntuforums.org/showthread.php?t=1341264&highlight=ASRock+x58+extreme)

---

