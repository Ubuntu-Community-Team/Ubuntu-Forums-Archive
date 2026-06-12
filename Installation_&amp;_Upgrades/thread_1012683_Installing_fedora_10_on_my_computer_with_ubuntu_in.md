---
title: "Installing fedora 10 on my computer with ubuntu in it."
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by ajay_rawat on 2008-12-16
HOW CAN I INSTALL FEDORA 10, I HAVE Fedora-10-i386-DVD.ISO AVAILABLE WITH ME.

rawat@rawat-desktop:~$ sudo /sbin/fdisk -l
sudo: unable to resolve host rawat-desktop
[sudo] password for rawat: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24df24de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       14207    62918572+   5  Extended
/dev/sda3           14208       22040    62918572+   7  HPFS/NTFS
/dev/sda4           22041       30401    67159732+   7  HPFS/NTFS
/dev/sda5           14086       14207      979965   82  Linux swap / Solaris
/dev/sda6            6375        8806    19534977   83  Linux
/dev/sda7            8807       14084    42395503+  83  Linux

Partition table entries are not in disk ordeR
 PLEASE SEE THE ATTACHMENT BELOW

---

### Post by em4r1z on 2008-12-16
1. Backup and delete sda7.
2. Grow sda6 (it's an almost full GNU/Linux system.) Now you can install Fedora within a virtual machine or... 
3. Create a new 5-8 Gb Ext3 partition in the space left within sda6 and sda5. Install Fedora here.


Yours is a weird partition scheme, you should consider logical volume management in the future.
Learn how to label your partitions.

In general, you'd want this:
1. A 5-8 Gb partition for each GNU/Linux system.
2. A separate partition for your documents and settings (/home.) This can be safely shared across different GNU/Linux systems by using different usernames for each.
3. A 1 Gb swap partition if you have up to 1 Gb of RAM, or no swap partition if you have more. If you use the hibernation feature, create a swap partition about 5-10% bigger than your total RAM.

---

