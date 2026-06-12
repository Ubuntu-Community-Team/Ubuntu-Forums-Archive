---
title: "Cannot boot windows"
date: 2012-04-06
forum: Hardware
---

### Post by furmada on 2012-04-06
I boot a ubuntu 11.10 32 bit release off my HP SimpleSave External HDD.
I did this in order to be able to run my ubuntu on any pc.
However, I realized that after booting off the external hdd, Windows (originally on the pc), would not boot! Instead, the BIOS shows a message saying:
could not find device *really long set of letters and numbers*
grub_rescue>
Please help, I am getting this on both pcs I tried it on!
Thanks

---

### Post by oldfred on 2012-04-06
Welcome to the forums.

You probably used one of the auto install choices and with multiple drives you have to use manual install or Something else to get a choice on which drive's MBR to install the grub2 boot loader.

You need to reinstall a Windows boot loader to the internal drive's  MBR  and install the grub2 boot loader to the MBR of the external. Grub2 also remembers where to reinstall on a major update to grub, so you need to fix that or sometime later it may happen again. Then in BIOS set to boot from external drive when you want Ubuntu.

Boot Problems:Computer does not boot without external drive
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

If you want to just install boot loaders, reinstall grub2's boot loader first or else you will have to use liveCD:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc
#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by furmada on 2012-04-07
Thank You, I will try this.

---

### Post by furmada on 2012-04-07
Thank you so much!
It works perfectly.

---

### Post by RJARRRPCGP on 2012-04-07
> **furmada said:**
> Instead, the BIOS shows a message saying:

Not a BIOS error. Your GRUB is broken. :(

---

