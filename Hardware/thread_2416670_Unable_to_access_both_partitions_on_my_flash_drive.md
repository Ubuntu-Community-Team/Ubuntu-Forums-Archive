---
title: "Unable to access both partitions on my flash drive. Ubuntu 18.04 gnome."
date: 2019-04-13
forum: Hardware
---

### Post by jjc55 on 2019-04-13
I set up my 32GB flash drive with two partitions(16/16Gb roughly)  , but neither Ubuntu nor Windows 10 wants to recognize the second partition. In Ubuntu I had to manually mount the flash drive to get it to recognize it at all. On the first partition I flashed a Windows rescue drive, which Ubuntu also sees, but I'd like to use the other partition for perhaps Kali, or just to keep a backup ISO of Ubuntu, as well as random data storage. Luckily, I'm able to stack data along side the Windows rescue drive but I don't want this. I also don't know if its going to interfere with the bootable Windows ISO and I'm not willing to try it. Reason being is; the last time I accidentally let my Laptop start with the rescue drive in, I had to snatch it out before it got going and it completely trashed Windows, locked me out and deleted a ton of my files. I also know that Windows plays hell with grub2 and I don't want those problems all over again. Any ideas out there that will get at least Ubuntu to recognize both partitions? Thanks a bunch.

---

### Post by yancek on 2019-04-13
Microsoft decided that it was not necessary for it's operating systems to be able to view more than one (the first) partition on a usb drive.  No windows system I am aware of will recognize any but the first partition on a flash drive.  What filesystem is on the second  partition.  You don't mount drives, you mount filesystems on the drives which should be on a partition. 

You should be able to copy the Ubuntu iso or a Kali iso to the 2nd partition.  Not sure what you've tried or what your result was or what your intentions are for the iso files?  Do you want to be able to boot from them on the 2nd drive of that partition?  Should be able to but not a simple process.

You could also use the 2nd partition for data although it would need to be copied there from Ubuntu or Linux since windows won't recognize it.

---

### Post by jjc55 on 2019-04-13
The first partition was converted to NTFS and  the second should be FAT32. I'd like to flash Kali to the second as well as an Ubuntu ISO for backup, or use it for modifications such as grub repair, gparted, etc (I know gparted can be used in other ways but I feel like running it from a live session is just easier and safer) .... As far as Kali goes; I pretty much just want to get in there and start fooling around with it. I heard some pretty cool stuff about it that is very intrigueing to me and I'd like to see what all the hype is about. I'd also like to slap some files and maybe a bootable antivirus or two somewhere on the partution as well.
 I want the first partition to contain a Windows rescue drive only, and I'd prefer to keep it that way. For now i have some random files on there with it that I want in a different location.
 As it stands right now,  I already have my laptop set up to dual boot with Ubuntu 18.04.2 and Windows 10, so I know what I'm trying to achieve is going to be complicated. Ubuntu is of course set first in the grub2 order. I can easily swap the grub order if that would make booting and other things happen a little smoother when I finally get things situated the way I want. 
To be completely honest with you I haven't gotten any further than partitioning the flash drive, converting the first partition to NTFS and putting Windows rescue drive on it. I didn't want to continue on until I got some second opinions or ideas. To further complicate things, I have a sneaking suspicion that I'm going to have to install grub2 on my flash drive and possibly make one or two more small partitions to get any of this to work. So, any thoughts on that, as well as the rest of this mess? I just want this thing to work.  I'm fairly certain that I can do this with a little effort and elbow grease.

---

### Post by yancek on 2019-04-14
If you want Ubuntu, Kali and GParted on the flash drive, you can simply copy the respective iso files of each to that partition.  You will need to install Grub2 to the flash drive, probably using Legacy/MBR will be simpler.  You won't be able to do any auto-update of Grub so you will need to manually install Grub2 and create your own grub.cfg file with the respective menuentries.  Lots of tutorials on the internet about this.  It doesn't matter what filesystem type the partition if formatted as as the iso files of each will be iso9660 format.  Booting the iso directly in this manner will be a Live system and nothing can be changed and nothing will be saved.  You could create a 3rd partition and you would be able to save data there but that would require manually creating a mount point each boot and mounting the partition.

If you have a current Ubuntu on your hard drive with Grub2, you could avoid installing Grub to the flash drive and create menuentries in the grub.cfg of the installed Ubuntu to boot the iso files on the flash.  This will require familiarity with Linux drive/partition naming conventions as well as Grub naming conventions for drives/partitions.  THe Ubuntu site below gives an explanation and examples of booting an iso file directly from Grub2.  THis is not going to happen with a few mouse clicks so if you want it, it is possible but will take some effort.

Bear in mind that unless you have Windows 10 v1703 or higher, you will NOT be able to access the 2nd partition on the flash drive from windows, regardless of the filesystem format type.

---

