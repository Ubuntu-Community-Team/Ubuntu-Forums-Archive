---
title: "Old PC and External HD"
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by peteswiftuk on 2009-09-02
I have an old PC with W2K on it and a spare USB External hard disk.
  As a new user to Linux I thought I would try Xubuntu on the external hardisk. I used the live CD and everything seemed ok.I then installed Xubuntu onto the external disk.
   
  The pc does not support booting form USB and I understand that only flash disks can be booted directly. The work around is to make a Cd that load a Kernel and the usb drivers to mount the usb hard disk. I followed the instructions here.
   
  [http://www.linuxsolutions.fr/how-to-make-a-usb-boot-cd-for-xubuntu-904/](http://www.linuxsolutions.fr/how-to-make-a-usb-boot-cd-for-xubuntu-904/)
   
  The result is that the kernel loads however it loops numerous times through the following :
  EXT3-fs: mounted filesysten with ordered data mode
  kjournald starting. Commit interval 5 seconds
   
  Then finally finishes with
  BusyBox v1.10.2 (ubuntu 1:1.0.2-2ubuntu7) built in shell (ash)
  Enter help for a list of built in commands
  (initramfs)
   
  I have had 2 attempts at making the CD but with the same results so I don’t think I have made a mistake.
   
  Has anyone any ideas of what to do next?

---

### Post by Mighty_Joe on 2009-09-02
I wouldn't recommend Ubuntu or its derivatives for an old computer.  Ubuntu is intended to be a feature-complete alternative for Windows Vista.  Would you try running Vista on the hardware in question?  Xubuntu is a good choice if a machine doesn't have much memory or has a slow video card.  If the machine has all that and a slow CPU, there's not much Ubuntu can do to make it fast.
There are other Linux distros that are targeted at lower hardware requirements, for example, [Puppy Linux]("http://www.puppylinux.org/"), that would be a better choice.
As for your immediate problem, is there some reason you aren't dual-booting Win2k and Xubuntu?  That seems like your only option as you can't boot from USB.
Personally, I'd junk the old PC.  PC's are cheap enough that it isn't worth working around the limitations of old hardware (time is money!).  Not to mention you probably won't be happy with the performance of the old hardware and blame it on Linux.

---

### Post by StuartN on 2009-09-02
Whatever operating system you decide to try, it will be necessary to install it on a partition on the internal hard disk for a reasonable boot up - if the hardware is not USB-bootable then no operating system will boot from the external drive. If you resize Windows to 10-15 Gb and create a 5-10 Gb partition for linux then you should be fine. If the external drive is formatted NTFS then it will be read/write compatible with both operating systems. (FAT is also compatible, but NTFS is better for large files and long filenames).

Obviously you can try Ubuntu first and then overwrite the partition with a low-fat linux if Ubuntu doesn't perform well enough.

---

### Post by peteswiftuk on 2009-09-08
The reason it didn’t work is that the location of the operating system has to be FAT32 or FAT16 it now boots ok.

But Xubuntu jaunty does not work in persistent mode so I will have to try another Distro

---

### Post by Jose Catre-Vandis on 2009-09-08
From the sound of it, you didn't actually install Xubuntu on the HDD, but did a USB Flsh Drive "Live" install. Try a proper install and let grub take over your PC's mbr. Should work then?

---

### Post by i.r.id10t on 2009-09-08
> **Mighty_Joe said:**
> I wouldn't recommend Ubuntu or its derivatives for an old computer.  

Shhh... don't tell my kiosk systems that!  Jaunty w/ gnome, firefox, flash, etc. on P2-450s w/ 384mb of ram....  No issues.


For the OP - resize the win2k partition to create a small (100mb should do) partition to use as /boot and have your / partition on your external drive.  Let grub take over the bootloader.

---

