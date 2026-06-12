---
title: "Dual boot, lost partitions?"
date: 2009-05-21
forum: Installation &amp; Upgrades
---

### Post by flatpack on 2009-05-21
I have been using and eeepc for a year and decided that it was time to try Linux on my desktop as a dual boot with Win XP. I've been using a persistent install on a pendrive for a couple of weeks and decided that I ubuntu was what Iwanted to install.
I had already set up several partitons on the hard drive a few months back in preparation

I had
primary partition
win
spare space incase windows needs more later
Logical partiton
partition for ubuntu
partition where all of my documents were
spare space

In the install I selected the ubuntu partition for the install and set up  a swap partition at the end of the hard drive
Now when I boot up either system I can only see the Win XP partition and the Ubuntu partition. No sign of the storage partition or the swap partition.
I have tried following instructions elswhere in the forums with no luck so far.
testdisk that I download would not extract correctly even though I have tried several different downloads.
I've boted of the flash drive so that I can unmount any partitons if needed.[INDENT]rick@rick-desktop:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 61512822, Id= 7, bootable
/dev/sda2 : start=103908420, size=872859645, Id= f
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=103924485, size= 41977845, Id=83
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=312560577, Id= 7, bootable
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
# partition table of /dev/sdc
unit: sectors

/dev/sdc1 : start=       63, size=  3910977, Id= 6, bootable
/dev/sdc2 : start=        0, size=        0, Id= 0
/dev/sdc3 : start=        0, size=        0, Id= 0
/dev/sdc4 : start=        0, size=        0, Id= 0

[/INDENT]There should be sda7 storage about 280Gb
and sda8 4gb swap

What do I need to do to find these missing partitions?
Could it be a problem with NTFS, which I have used for the Win xp and storage partitions?

Thanks for any help in advance

Rick

---

### Post by presence1960 on 2009-05-21
you can open Partition Editor. If not already installed you can open a terminal and run ```
sudo apt-get install gparted
```
You will get something like this with your partitions on it.

---

### Post by flatpack on 2009-05-21
I've checked the partitions using Gparted and It only shows the 2 partitions that are working. I have noted down all of the details as they should help me to find the next partition on the drive, the most important one for me to restore.
I can't see a way for Gparted to help me find the partitons though.
I used testdisk as it suggested in help to find the maiin partitons and to save a new partition table.
Things are much worse now.....
The computer reports a grub error 17
It will not boot from a win xp disk, it says inspecting hardware then just hangs
I can't get it to boot from a usb thumbdrive

---

### Post by presence1960 on 2009-05-21
> **flatpack said:**
> I've checked the partitions using Gparted and It only shows the 2 partitions that are working. I have noted down all of the details as they should help me to find the next partition on the drive, the most important one for me to restore.
I can't see a way for Gparted to help me find the partitons though.
I used testdisk as it suggested in help to find the maiin partitons and to save a new partition table.
Things are much worse now.....
The computer reports a grub error 17
It will not boot from a win xp disk, it says inspecting hardware then just hangs
I can't get it to boot from a usb thumbdrive

gparted will show any and all partitions on your drive(s). if they arent shown in gparted or by sudo fdisk -l then they don't exist.

---

