---
title: "Hard Drive Clone"
date: 2009-04-29
forum: Hardware
---

### Post by RealG187 on 2009-04-29
I am not sure if this should go here or in "Installation and Upgrades" but:

I have a 10 GB Hard drive in one of my older systems I am using for Ubuntu (I have a 120 GB for XP) and I am getting a 40 GB hard drive. Is there a way I can clone the 10 GB drive to the 40 GB drive? I have a Maxblast disk but it only works on Maxtor hard drives and I am not sure if it will read EXT formatted Linux partitions (it asks for what OS you want to use and bases the file system off that, and Linux isn't listed from what I remember).

---

### Post by damis648 on 2009-04-29
No problemo.
Just boot up the LiveCD and launch gparted. Select the first 10GB disk and right click the Ubuntu partition and select copy. Switch to the new drive and paste. :guitar: You will probably want to enlarge the partition and create a swap. Note that you will likely have to reinstall grub to the new volume, so just follow the guide [here]("http://ubuntuforums.org/showthread.php?t=224351") to do that, and make sure to use the new drive when you use (hdx,y). :popcorn:

---

### Post by RealG187 on 2009-04-29
GParted can be used to copy a drive? How come I would have to reinstall grub, wouldn't it get copied over?

Could this method be used to copy Windows or Linux partitions?

---

### Post by damis648 on 2009-04-29
> **RealG187 said:**
> GParted can be used to copy a drive? How come I would have to reinstall grub, wouldn't it get copied over?

Could this method be used to copy Windows or Linux partitions?

Yes, gparted can copy partitions from one drive to another (the equivalent of using dd but without such a large margin of error on the users part for creating incorrect sizes, etc). You would need to reinstall grub because although you copied the partitions over, grub is not installed to the MBR of the new drive. When the BIOS tries to boot the drive, no bootloader is found and thus cannot boot, so you need to reinstall grub to the MBR, which is what that guide is for.

This method could copy partition to any drive, NTFS, FAT, EXT3, etc. but note that for Windows you will also need to fix the MBR (unless the windows bootloader is already installed on the MBR of the drive and the partitions are the same order)and Windows will likely complain when trying to boot it, giving a Windows protection error. Windows doesn't like to be moved from computer to computer, much less from drive to drive.

---

### Post by RealG187 on 2009-04-29
Wouldn't it clone the MBR?

---

### Post by damis648 on 2009-04-30
> **RealG187 said:**
> Wouldn't it clone the MBR?

Gparted, as far as I know, can only copy individual partitions. So in copying the partition, the MBR would not be cloned.

---

### Post by AlecJ on 2009-04-30
I think you maybe better off with Clonezilla..

[http://clonezilla.org/](http://clonezilla.org/)

---

