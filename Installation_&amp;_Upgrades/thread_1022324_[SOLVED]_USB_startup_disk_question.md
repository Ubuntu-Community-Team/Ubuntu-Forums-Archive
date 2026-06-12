---
title: "[SOLVED] USB startup disk question"
date: 2008-12-26
forum: Installation &amp; Upgrades
---

### Post by linnuxnub on 2008-12-26
If I create a USB startup disk can I still use the USB drive as storage for other files as well?

---

### Post by C.S.Cameron on 2008-12-26
Yes,
You can make a folder inside filesystem / cdrom that you can access from both Windows and Linux.

---

### Post by linnuxnub on 2008-12-27
ok thanx.

---

### Post by linnuxnub on 2008-12-30
I am using the program "Create a USB Startup Disk" in 8.10 how exactly would I go about this?

---

### Post by C.S.Cameron on 2009-01-03
Sorry, my memory is getting a little unreliable.
It is in cdrom and not media where you can create an accessible folder.
From Windows you can just create a folder on the flash drive.
From Ubuntu use Alt-F2, gksu nautilus.
Go to File System, cdrom.
You should be able to right click to create a folder.
I don't know to change permissions from root as owner so contents are read only unless accessing with gksu nautilus.
I also have not figured out how to make a desktop link to this folder.
If you delete anything from this folder using Ubuntu, it will end up in .Trash-0 a hidden folder in cdrom also owned by root.

---

### Post by linnuxnub on 2009-01-03
To do this from Ubuntu do I have to be booted from the USB?

Another question, when I have booted from the USB there is only 1.5g of free space on the drive whereas there should be around 30g since that is the amount i set for persistence (its a 32g flash drive), and when I try and install things I run out of space, am I doing something wrong?

---

### Post by C.S.Cameron on 2009-01-03
I don't think it matters how you create a folder in cdrom, it is just the only place on a persistent thumbdrive I have found that is accessible to both Ubuntu and Windows.
Persistence is kept in a file named casper-rw.
I think there is a limit to file size depending on if you are formated FAT16 or FAT32. I'm not sure but 30 GB might be over that limit.
You can check in cdrom to see what size casper-rw actually is.

Using gparted you can shrink your current FAT partition, removing space from the right. next to this create a new ext3 partition and label it casper-rw, and next to this another ext3 partition and label it home-rw.
Using the gparted live cd seems to work best for me.
You can fine tune the sizes of these partitions later.
Casper-rw is used for installed applications etc and home for settings and downloads etc.
If your casper-rw file actually is 30 GB you will need to delete it before making the above partitions.

---

### Post by linnuxnub on 2009-01-03
Would it be better to do a full install on my thumb drive, if so do you have any tips?

---

### Post by C.S.Cameron on 2009-01-04
I prefer a full install and am running off one now.
I install the same way I do to internal HDD.

Tips:
Disable your internal drives before starting, you can add them as a boot option on the thumb drive later if you wish.
Use manual partitioning.
Make your first partition, (on the left hand side), FAT32 so you can access your drive from a Windows machine.
Make the next partition ext3 or reiserfs and set mount point as /home.
Make the next partition ext3 or reiserfs and set mount point as /.
I am not currently using swap space but leaving a little might be useful if you are plugging into machines lacking adequate RAM, I figure most of these do not have BIOS to boot USB anyway.

---

### Post by linnuxnub on 2009-01-04
Are you sure 32g is enough for a full install?

And as for my problem with the usb startup disk persistence, I found out that FAT32 partitions have a limit of 4gb, so I guess you can't have 30gb of space for persistence.

---

### Post by C.S.Cameron on 2009-01-05
I am using an 8 GB stick and have had Windows installed on Virtual box on it, running Autocad, SketchUp and Rhino 3D, (not much room left over).
At this moment I am using about 1 GB for home and about 2.5 GB for root.
I am sticking files and stuff that would normally go into home on a separate flash drive, My Windows virtual machine has its own flash drive also.
I don't have that many applications installed, Sketchup 7, DVD shrink and DVD Decrypter are the only things I am running under wine.
I use Cruft Remover quite often

I've been using this 8 GB for about 3 months now, 32 GB should last you quite a while if you don't go too wild.

---

### Post by linnuxnub on 2009-01-07
I found this useful tutorial on how to make a usb startup disk that is persistent and that allows you to access your home folder from windows it is very detailed.

[http://www.guywithcable.com/main/linux-lessons/104-persistent-portable-usb-ubuntu-installation-with-windows-accessible-home-folder](http://www.guywithcable.com/main/linux-lessons/104-persistent-portable-usb-ubuntu-installation-with-windows-accessible-home-folder)

---

