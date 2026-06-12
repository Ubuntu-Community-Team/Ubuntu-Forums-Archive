---
title: "Multiple Partitions and Encryption on a USB drive"
date: 2012-12-11
forum: Hardware
---

### Post by doomgiver on 2012-12-11
**[COLOR="Navy"]Hello!![/COLOR]**

I am trying to make a USB drive with multiple partitions, with encryption.
somewhat like this : 
================
[img]http://i.imgur.com/2EgdJ.jpg[/img]
================

Initially, both partitions will be encrypted.

**_1._** on windows, the green program would have to be run by the user.
it will auth the user and allow access to just the red partition.
blue (ubuntu) partition will still remain hidden

my idea here is to "compartmentalize" the data. hiding ubuntu from windows and the red partition from other users (until auth'd with the green program

_**2.**_ on linux
at splash screen, the credentials input will unlock the red portion. allowing it to be used normally as a usb drive.


I am following steps for multiple partitions from **here** : [http://agnipulse.com/2011/11/partition-usb-flash-drive/](http://agnipulse.com/2011/11/partition-usb-flash-drive/)
and i've successfully managed to make the partitions.

Now, im stumped at the "**installing**" part, ie, how to install Ubuntu to one of the partitions.
And i mean "install". im not trying to create a installer here. i want a **full fledged OS** (think persistence with changes, like a **portable OS**)

So, is there any linux command for doing this? ( I think i remember someone saying _dd_ could write data to devices, but what about making it **bootable**?)

Also, the normal methods (like unetbootin, LiLo), will they work? or will they use up the entire usb drive instead of a single partition?


also, if anyone can help me figure out the _encryption part_, please do so!!!

thanks a lot, and thats all for my maiden thread.
**prays to sudo that thread is in correct section**

---

### Post by doomgiver on 2012-12-12
bump... any solution?

---

### Post by sudodus on 2012-12-12
Welcome to the Ubuntu Forums, doomgiver,

I have done most of the things you want to do, and it is not too difficult.

Look at these links

[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1958073[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1958073")

[[COLOR="red"]http://ubuntuforums.org/showpost.php?p=11546560&postcount=5[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11546560&postcount=5")

So you can install Ubuntu (or even better Lubuntu or Xubuntu, that are smaller and therefore faster from a USB pendrive). Select encrypted home directory during the installation!

An alternative is to install it to a HDD or SSD without any proprietary drivers, and when it works properly simply clone it to a USB pendrive. If you clone the whole drive, it will also include the boot sector. You will need to repair the partition table, because the sizes of the drive are different, but it should not be too difficult.

If you make the first partition readable by Windows (for example with the FAT32 or NTFS filesystem) and use the second partition for Ubuntu (and possibly a third partition for swap), it will work. Then you need some tool to unlock the hidden partition, directory or files, that works in Windows and Linux. If "only" a directory with files, you can use ***gpg***. I don't know if ***truecrypt*** is available for Windows.

---

