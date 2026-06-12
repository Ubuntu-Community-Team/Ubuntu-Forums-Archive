---
title: "/dev/sda: unrecognised disk label"
date: 2014-07-01
forum: Hardware
---

### Post by tom94 on 2014-07-01
Hello there! I'm trying to install xubuntu on an old computer with a live usb. Neater the system nor gparted seams to make this hd work. Previously (i mean, couple of hours ago) this disk had a dual partition and was running windows xp. Then in between a couple of reboot from usb to win, the system stated that the usb needed to check the partition, and i shut it down, worried it could ruin the usb partition. Then i started again with the live usb, but i then realized the system couldn't handle the hard disk. Trying to start windows now gives a partition error, so it's clear the partition has been damaged someway? Running gparted the hard disk seamed lacking the partition table, but every time i try to make gparted build the partition table, it simply fails (doing nothing at all) or gives the error above ( /dev/sda: unrecognised disk label ). Tryed fdisk by terminal with no results. 

I don't know how to handle this since i have to make this pc work, and i can't possibly make a bootable cd or boot the pc with a different os. Please, could somebody give me some clues or help? Thank you very much!

---

### Post by yancek on 2014-07-01
So you are still able to boot Xubuntu from the flash, correct?
If you can, do that and open a terminal and copy/paste the following command and post the output here:  sudo fdisk -l
You might also go to the site below and read the instructions in the Description box on that page then download and run the script.  You will get an output file named results.txt which you can post.  It should contain enough details on your system so that someone can help or at least point you in the right direction:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

