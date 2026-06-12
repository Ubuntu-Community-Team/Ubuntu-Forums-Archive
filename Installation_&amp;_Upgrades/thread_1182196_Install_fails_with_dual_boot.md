---
title: "Install fails with dual boot"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by spoorf on 2009-06-08
I am installing UBUNTU 8.10 on several PCs. The problem occurs on a system with a SATA controller with drive 0 powered off via BIOS and drive 1 active. the partitioning chooses a USB drive for the install and seems to proceed normally. However, the dual boot flashes across the screen too fast to read and the XP system has some damage, also the UBUNTU system cannot be booted. When I bring up GPARTED I see drive 0 partitions. How does it know what the partitions look like on a powered off drive? Also, the partitioning left my Norton Ghost backups on the USB drive unusable.  I have an extra SATA drive that I can replace the bad drive with and move the XP drive to slot 0. Will that fix the problem? (I have recovered the USB drive and will give UBUNTU its own SATA drive)
 
:) S.

---

### Post by dstew on 2009-06-09
I doubt that your BIOS really disconnects the power from the SATA drive. It probably just bypasses it, or doesn't register it as active. When Linux boots, it ignores the BIOS and accesses the hardware directly, so it will see the drive, even if the BIOS has it "turned off".

Regarding the boot menu going by too fast, this can be fixed. It usually happens because the Ubuntu installation process did not recognize the Windows system as an operating system, and so it tries to boot Ubuntu directly without giving you the choice of operation systems that you usually would see. Try hitting 'esc' over and over during the attempted boot and see if you get a menu. Otherwise, you can boot a Live CD and edit the /boot/grub/menu.lst file that was installed on your hard disk. That is a bit tricky, because you have to mount the hard disk and navigate to the file, but it can be done.

If you re-partitioned a disk, any files on it will no longer be accessible, so your Norton backups are probably gone. There are ways to try to recover deleted partitons, but it is not simple.

As far as moving disks around, you should install Ubuntu into the system with it configured exactly as you want it to be when you use Ubuntu. Do not try to "protect" your drives by unplugging them, or removing them. This will result in a mis-configured Ubuntu install. You should leave the disks in, bad disk and all.

---

