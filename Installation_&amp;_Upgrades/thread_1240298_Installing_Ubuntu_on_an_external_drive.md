---
title: "Installing Ubuntu on an external drive"
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by Liandri on 2009-08-14
Hi, I'm a little curious as to whether it's possible to install Ubuntu on an external hard drive and run it off that, but also be able to still use it for storage or backup with Windows.

---

### Post by AmerNewbieInDE on 2009-08-14
it really depends on how you partition the drive.

i am running ubuntu off an external sata connected by usb, just have to watch how hot the drive gets, but if you want to access it with windows, you need fat or ntfs filesystem. i can boot off usb so i put grub loader on the external and gave the whole drive to linux, but, if you want windows to access it for storage, try setting up a partition for linux and format the other in fat32 or ntfs.. linux read ntfs but windows doesnt read linux partitions...

---

### Post by presence1960 on 2009-08-14
Partition the drive just as you would an internal drive. Ubuntu will run off an external drive. You can create an Ubuntu partition(s) & data partition(s) on the external drive.

Installing Ubuntu to an external drive you may want to put GRUB on the MBR of the external drive. and then set your external drive ahead of your internal drive in BIOS boot order. This will give you the flexibility of booting without the external drive plugged in. Whatever bootloader (I am assuming Windows) is on MBR of your internal disk will boot without the external plugged in. This will also leave your windows bootloader intact. If you boot with the external drive plugged in then GRUB will take over.

If you install GRUB to MBR of your internal drive you will always have to have the external drive plugged in as GRUB will look for menu.lst on the external drive. If it is not plugged in you will not be able to boot and will get a GRUB error.

---

