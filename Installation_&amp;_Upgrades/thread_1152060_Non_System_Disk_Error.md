---
title: "Non System Disk Error"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by bcmorr2 on 2009-05-07
Hello everyone,

     I recently installed ubuntu for the first time.  My setup is a dual boot system with Windows XP on my main drive and then on my secondary I have installed ubuntu.  I choose which disk to book off of using my bios option to select my boot drive.  The error I ran into is after installing ubuntu(Standard install though I chose not to install the boot loader since I accomplish it's goal through my bios)and try to boot off the ubuntu hard disk it claims it's a non system-disk and halts there.  Any suggestions on how to make ubuntu work?

Thanks

---

### Post by maxbur on 2009-05-07
Try reinstalling Ubuntu, including GRUB, to your second hard disk. You need a boot loader such as Grub, to start Ubuntu. 

Your BIOS can only point to a boot sector. It doesn't actually supply files for booting, which are supplied by the operating system. Search Google or Wikipedia if you want to know more about the boot process.

If Ubuntu is installed as a standalone on a separate drive, Grub shouldn't alter the Windows Master Boot Record on the other drive. The MBR is what starts a Windows boot. Grub is what starts a Linux boot.

Good luck with Ubuntu.

---

### Post by Bartender on 2009-05-07
The Ubuntu HDD is secondary, right?  The Windows HDD is the primary disk?
On the very last page of the installation procedure, just before you tell the installer to go ahead, there's an "Advanced" button.  Go into that and tell it to install GRUB to hd1.  The default is hd0.

---

