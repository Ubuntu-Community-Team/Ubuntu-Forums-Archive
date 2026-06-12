---
title: "Install bootloader after the fact?"
date: 2008-09-18
forum: General Help
---

### Post by DJitalis on 2008-09-18
For reasons I can only classify as insanity I set up my computer with 2 500gig drives one with ubuntu and one with windows xp (For gaming). I would switch the booted disk within BIOS. Is there a way for me to install a boot loader now? What would be a good plan of attack? 

Thanks in advance.

---

### Post by LowSky on 2008-09-18
Suber Grub CD, [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) the answer to your questions. May I suggest that yu make your Linux drive the primary boot disk, this way you Windows can still boot without Grub in case of an emergency

---

### Post by mb_webguy on 2008-09-18
+1

Also, am I correct in my understanding that you installed Windows to an entire 500GB drive, and Ubuntu to an entire 500GB drive?  Wow.  That's a lot of wasted space.  If you installed Windows to a a 15GB (for XP) or 25GB (for Vista) partition, Ubuntu root to an 8GB partition, and Ubuntu home to a <1GB partition, you would have 965GB+ to use for file storage, shared between both operating systems...

---

### Post by TeXtonyx on 2008-09-18
[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
C:\ubuntu.bin="Ubuntu"
c:\bootsect.lnx="Linux"
--------------------------------------

This shows Windows as first drive, primary/master, sda. It does not have grub written to the MBR, rather "Ubuntu" was installed to the first sector of its boot partition. "Linux" is installed on the slave drive, sdb, to the first sector of its boot  partition. One can do this from Windows and write to boot.ini automatically with BootPart. And Windows can always boot standalone because it has no grub in the MBR. The second drive, sdb, with Linux installed, is a logical partition and boots without a problem.
[http://tennessee.ubuntuforums.com/showthread.php?t=739540](http://tennessee.ubuntuforums.com/showthread.php?t=739540) (Super Grub works)
setup (hd1,1) this example installs to the second hard drive, first (boot) partition, as the first drive is located at hd0. That's if you want a boot.ini using 1st sector,  boot partition. Afterwards, BootPart can automatically write the 512 boot sector to C:\ and make the boot.ini entry for you.

---

