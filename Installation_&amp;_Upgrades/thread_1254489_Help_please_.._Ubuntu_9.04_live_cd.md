---
title: "Help please .. Ubuntu 9.04 live cd"
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by demon36 on 2009-08-31
Ive decided recently to install ubuntu 9.04 so  I freed up about 4.5 gb in a local disk for installation .. I had many problems with wubi so I decided to install it from live cd ..
after setting language in Installation I have three options :
-side by side installation
-entire disk
-specify drive manually
What i want is to install ubuntu on the 14 gb on a local disk with 4.5 gb free without any loss of data on it
SHould I use Side by side installation Or Lubi ?????????
Thnx at all

---

### Post by Bucky Ball on 2009-08-31
Manual installation. Are you dual booting or you have a partition with data? All Ubuntu partitions are EXT3 (or EXT4) and bear no resemblence to your other data partition (NTFS or FAT) so you will see them quite plainly when you hit the manual partition section. Just make sure you don't touch them and you should be fine. 4.5Gb is okay for Ubuntu itself but you are going to have a very small /home and /swap partitions. It should very basically look like this for partitions:

/ =         This is your 'root' partition.
/home  = This would be where your user lives and personal documents.
/swap      = A swap file.

You will find all this as defaults for setting up your partitions in the partitioner so it is pretty easy. Just post back if confused. If you have another computer online while you are doing it is always handy.

The OS will be faster with a hard drive install.

---

### Post by demon36 on 2009-08-31
Well , Im an absolute beginner
When I opened Install again Icannot see side by side installation
Ans also the 4.5 gb free space just disappeard
I dont know wut to do

---

### Post by Bucky Ball on 2009-08-31
I would take CD out, reboot computer and open the BIOS (hit delete or F1 at boot - there should be an option to 'Enter Setup' or BIOS that will tell you but it will flash by pretty quick!) and set your machine to boot from the CD, insert the CD then hit F10 to save changes and quit.

Are you trying to use Wubi inside Windows rather than what I described above?

---

### Post by demon36 on 2009-08-31
I Had many Problems with Wubi at first 
And I Think manual specification is kinda dangerous because of me being beginner 
So I think it will be good to use lubi

---

### Post by tal007 on 2009-08-31
Before you try to install make sure to read much hard drive space you need. If you don't have enough hard drive space,  the installation program will freeze in the middle of installation. Also, back up any files, drivers, applications you can not afford to loose. Ubuntu is a new phenomenon in the operating system world. Not mature yet. Anything can happen during installation.

As for installation, if you are not sure always use "Unused Continuous Free Space". In that that way you are not running the risk of accidentally deleting partitions that are owned by others ( e.g Xp, Vista etc ).

Don't try to delete any partitions if you are not sure. If you want to delete any partitions to free up space, meaning siting empty currently not being used, you can do so only from the Operating System that owns that partition. If Xp owns it, then you have to do it from Xp.  Xp will adjust its database such file system and partition table accordingly to reflect these changes. Otherewise, you will create a "Category 5" storm in the operating system world.  Xp will wake up next morning finding that its roof is mising.

Of course, there other ways too such as resizing.



  If you need space always resize it using the Ubuntu installation utility.

---

