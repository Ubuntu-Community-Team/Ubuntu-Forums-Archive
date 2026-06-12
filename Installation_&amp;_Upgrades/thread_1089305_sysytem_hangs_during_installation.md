---
title: "sysytem hangs during installation"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by makhaucrazy on 2009-03-07
during installation after setting the partition 750 MB to swap area and 19gb to "\" it displays the xubuntu desktop and then my laptop stops responding. I have 246Mb RAM 1.6GHz processor speed. I also want to set up dual boot with win xp.

---

### Post by raulozzi on 2009-03-07
I had this same problem while I was installing Ubuntu 8.10. I noticed though that i would work when I would press CTRL and hold it down.

---

### Post by makhaucrazy on 2009-03-07
and how do I setup dual boot?

---

### Post by martrn on 2009-03-07
> **makhaucrazy said:**
> and how do I setup dual boot?

To set up dual boot you would need to install Grub to the master boot record. GRUB is the GRand Unified Bootloader.  There is more information about GRUB at **[http://www.gnu.org/software/grub/]("http://www.gnu.org/software/grub/")**.  Grub is a boot loader which loads your linux operating system (ubuntu) or chain-loads your windoze operating system so that it can boot.

On your GNU/Linux or Ubuntu file-system you will have a directory located at /boot/grub/ which contains the file menu.lst plus the second stage of the boot loading sequence for boot-loading or boot-strapping your Gnu/Linux or Ubuntu system.

Your /boot/grub/menu.lst should instruct grub on which operating systems are bootable on your computer.

---

### Post by makhaucrazy on 2009-03-07
I also wanted to use XFS file system as I read it was a lot faster ext3. however while using that it displays an error message that the boot loader hangs on XFS file system. I would be a lot of help if you could guide me on the partition sizes in manual aprtition options. I have 20 GB of Hard disk space left after my first xp partition

---

### Post by martrn on 2009-03-07
> **makhaucrazy said:**
> I also wanted to use XFS file system as I read it was a lot faster ext3. however while using that it displays an error message that the boot loader hangs on XFS file system. I would be a lot of help if you could guide me on the partition sizes in manual aprtition options. I have 20 GB of Hard disk space left after my first xp partition

An XFS file system can not be booted using GRUB.  You would need to install a dos based grub or boot using the windows boot loader, or else partition your hard disk to have a small fat32 based file system for your /boot directory and mount it separately.  Not exactly a beginners topic.  Also an XFS file system can't be repartitioned or moved you either delete the whole thing if you need to get rid of it or leave it there.

If you are using an ext2 or ext3 you can partition your hard drives either using the Ubuntu live cd or using [gparted]("http://gparted.sourceforge.net/") where you can get an usb or cd image to partition your hard drive or move partitions.

---

