---
title: "Install Ubuntu Without CD Drive From OS X"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by linuxgeekery on 2009-01-19
Due to some stupid human error on my part, my MacBook Pro's CD drive is broken and needs repair.  However, I need to install Ubuntu and I can't use my CD drive to burn/install from.  Is there any way to install Ubuntu from an ISO on the hard drive directly to the hard drive?

---

### Post by zwygart on 2009-01-19
Sure,
You can install from CD, harddrive and flash drive.
You said hard drive. So make a partition with minimum 800M and extract the content of the ISO there. (mount -loop /your/iso or something).
Assuming you already have installed grub, you only have to add the entry to boot from your copied iso in the file /boot/grub/menu.lst. If not only install grub. 

The entry you have to add is ```

title Ubuntu LiveCD
root (hdX,Y)
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper
initrd /casper/initrd.gz quiet splash --
```
Replace X and Y with the number of the partition (GRUB numbering).

If you don't know wich number post the output of fdisk -l

---

### Post by linuxgeekery on 2009-01-20
Sounds great, except I'm not too sure how to install Grub from OS X.  I have no Linux install on the hard drive.

> **zwygart said:**
> Sure,
You can install from CD, harddrive and flash drive.
You said hard drive. So make a partition with minimum 800M and extract the content of the ISO there. (mount -loop /your/iso or something).
Assuming you already have installed grub, you only have to add the entry to boot from your copied iso in the file /boot/grub/menu.lst. If not only install grub. 

The entry you have to add is ```

title Ubuntu LiveCD
root (hdX,Y)
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper
initrd /casper/initrd.gz quiet splash --
```
Replace X and Y with the number of the partition (GRUB numbering).

If you don't know wich number post the output of fdisk -l

---

### Post by zwygart on 2009-01-20
OK, I newer really worked with OS X, so I don't know what is possible to do. You may try the previous methode on a flash drive. You may find answer at [http://wiki.osdev.org/GRUB](http://wiki.osdev.org/GRUB) . Another way is to pass trough a emulator. This are some glues but now your are exceding my habilities. It's your turn to make some research. So search for installing GRUB on USB, emulating. 

Instead off GRUB on USB you may try syslinux.

Oh I found something that may interest you. On mac you have a command called dd. This command is to copy disk images. ISO is a kind off disk image. So copy your iso to a USB or a partition with dd. It may not work with a partition. dd if=yourISO of=/media/yourUSB ore something.
To boot USB choose from the boot option. Please post how it works. This will help me also.

---

### Post by ViperByte on 2009-01-20
> **linuxgeekery said:**
> Due to some stupid human error on my part, my MacBook Pro's CD drive is broken and needs repair.  However, I need to install Ubuntu and I can't use my CD drive to burn/install from.  Is there any way to install Ubuntu from an ISO on the hard drive directly to the hard drive?


Try ToastMount, or if you can, try an ISO/Image mounter for Macs. It MIGHT work...

---

