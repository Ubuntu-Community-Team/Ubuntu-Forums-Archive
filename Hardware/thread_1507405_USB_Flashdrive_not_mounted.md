---
title: "USB Flashdrive not mounted"
date: 2010-06-11
forum: Hardware
---

### Post by Sh4wn on 2010-06-11
Hi,

I've installed Ubuntu 10.04 on my dad's computer, to prove Linux is ****ing awesome. He's quite happy, there's only thing that annoys him a lot: USB harddrives/flashsticks don't work properly. In some rare occasions an USB stick mounts itself automaticly, but in most cases it just doesn't do anything. They do show up when using the lsusb command, they don't show up in nautlis under locations.

When using the fdisk -l, it shows the partition table of the main harddisk, then the program takes a coffeebreak, and after a few minutes he finally gives /dev/sdb1 as the USB flashdrive.

When trying to mount it manually, using mount /dev/sdb1 it takes a few minutes and after a while it gives the error:
Error mounting: mount: /dev/sdb1: can't read superblock

Things I tried:
Installing pmount and libpmount0.0, I think this actually did improve the situation a bit, as it now actually gives an error message, and sometimes a usb flashdrive actually does get mounted.

I also removed HAL, but nothing changed. I've also checked if floppy drive was enabled in BIOS, but couldn't find anything that would lead to such setting..

And now, I'm stuck. Is it a hardware problem? I've connected an USB mouse and keyboard, and they both work properly, and my USB connected printer also.. What could be the problem?

---

### Post by lenny45 on 2010-06-11
i have the same problem except i'm trying a USB drive in my laptop. my usb mouse works fine also.

---

### Post by garvinrick4 on 2010-06-11
Give the drive a label in disk utility or gparted and lets say karmic for a label, use what you want. And the partition is sdb1. Use your own again.

last letter small L
```
sudo fdisk -l 
```second letter small L gives you label names
```
sudo blkid 
``````
sudo mkdir /media/karmic
``````
sudo mount /dev/sdb1 /media/karmic
``````
sudo umount /media/karmic
```Should now mount after mount command, to automount. Make sure in Configuration editor.
Go to apps to nautilus to preferences and make sure media auto mount is checked.
If cannot find. Will be Under Applications/System Tools
```
sudo apt-get install gconf-editor 
```Hope this helps you.

---

### Post by Sh4wn on 2010-06-12
> **garvinrick4 said:**
> Give the drive a label in disk utility or gparted and lets say karmic for a label, use what you want. And the partition is sdb1. Use your own again.

last letter small L
```
sudo fdisk -l 
```second letter small L gives you label names
```
sudo blkid 
``````
sudo mkdir /media/karmic
``````
sudo mount /dev/sdb1 /media/karmic
``````
sudo umount /media/karmic
```Should now mount after mount command, to automount. Make sure in Configuration editor.
Go to apps to nautilus to preferences and make sure media auto mount is checked.
If cannot find. Will be Under Applications/System Tools
```
sudo apt-get install gconf-editor 
```Hope this helps you.

I already tried most of these things, mounting doesn't work, it takes some time, and then gives an error, although there's one USB stick I formatted with ubuntu, which actually does get recognized by nautilus (it shows up under locations), and when I click on it, it mounts. But all other USB disks don't work. And I don't want to format all USB sticks first. 

The configuration of nautilus is also OK.

---

### Post by garvinrick4 on 2010-06-12
All my USB flash drives are formatted in Fat32. Windows and Linux can read them both.
If you even want a partition that both can read use Fat32 will show up in windows as a F: drive or some letter and will show up as what you label it in Linux say DATA or something like that. If you dual boot between the two nice to have a partition to hold items you want to have in both installs. Can exist as logical inside of a extended so do not have to take up a primary.

---

### Post by Sh4wn on 2010-06-13
Yeah I know, fat32 is supported by ubuntu, but somehow they don't want to mount, they do show up at fdisk -l, lsusb, but mounting: not a chance. When I connect my HTC Hero Phone (the sd card partitioned as ext2 + fat32 (used for apps2sd)), nothing happens. It shows up at lsusb, but this time, even fdisk -l doesn't show the sd card partitions. And nautilus doesn't show any location to the phone..

---

