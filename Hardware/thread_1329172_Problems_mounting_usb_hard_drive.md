---
title: "Problems mounting usb hard drive"
date: 2009-11-17
forum: Hardware
---

### Post by sbelz79 on 2009-11-17
I'm having difficulty mounting an external usb hard drive.  I've been having some problems with 9.04 (I'm pretty sure I caused them by installing buggy packages), so I decided I want to wipe the Hard Drive and do a fresh install.  I can't get it to even recognize a flash usb stick when I boot from the hard drive- hell, I can't even open Places>Computer- so I tried booting from the live CD.  

After booting Ubuntu 9.04 from CD, when I plug in the flash stick it shows up on my desktop automatically right away as "Kingston".  However, when I plug in my Western Digital Passport, I get the error message "Could not find "/media/My Passport".  Please check the spelling and try again."  Occasionally, the drive will click, and the same error message will pop up again.  Then, when I go to Places>Computer, My Passport is listed, but when I click on it I get the message "The folder contents could not be displayed.  "My Passport" could not be found.  Perhaps it has recently been deleted."

It doesn't matter whether I plug it into one of the USB ports built into my mobo or on the 5-port PCI card I installed, I can't get it to work.

When I boot my girlfriend's computer using the live cd (she runs Windows on her hard drive), the WD external HD comes up on the desktop automatically when I plug the drive into one of her frontside USB ports, and I have no problems accessing the files on it.  

Also, on my computer, I tried using the command line to mount the USB drive manually, without success.  I tried (as suggested on one website):

sudo mkdir /mnt/usbdrive
sudo mount /dev/sda1 /mnt/usbdrive

when I typed:

ls /mnt/usbdrive

It listed the contents of my root directory

Please help, because I'd really like to backup my media files before I nuke the HD.

---

### Post by Bon Dup on 2009-11-17
hi sbelz79,
i had a similar problem when i first connected my usb drive to linux.
your usb drive wont be under sda1. 

try this to list all your available partitions:

```
sudo fdisk -l
```if you could copy the results and reply back with them i might be able to help.

---

### Post by Bon Dup on 2009-11-17
i failed to mention you must have the device inserted and powered :s

---

### Post by sbelz79 on 2009-11-17
name@puter:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea1aa9c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29650   238163593+  83  Linux
/dev/sda2           29651       30401     6032407+   5  Extended
/dev/sda5           29651       30401     6032376   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c74ae42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    c  W95 FAT32 (LBA)

---

### Post by sbelz79 on 2009-11-17
I also decided to try removing my USB 2.0 PCI card from my system, booting with the 9.04 live CD, and plugging my external HD into the on-board USB port.  Lo and behold, it showed up on my desktop.  I created a folder within "My Passport", and tried to drag the folders I want to backup into it.  But here's what I got when I tried to drag the folder "Videos" into "backup":
"Error while copying.
There was an error creating the folder "Videos".
Error creating directory: Input/output error

When I used the command line to try to do the same:

ubuntu@ubuntu:/media/disk/home/sbelz$ cp Videos /media/My\ Passport/backup/
cp: omitting directory `Videos'

or for an individual file:

ubuntu@ubuntu:/media/disk/home/sbelz$ cp Videos/Movies/Predator.avi /media/My\ Passport/backup/
cp: cannot create regular file `/media/My Passport/backup/Predator.avi': Input/output error
ubuntu@ubuntu:/media/disk/home/sbelz$ 

Could the problem possibly be that I need a bigger power supply?  
I'm running one with a max output of 420 watts, which seems like it should be sufficient for my system with an AMD Athlon 2400, DVD-RW drive, and GeForce 6200 graphics card, and one 250GB hard drive (can't remember the speed, but nothing fancy)  I already thoroughly inspected the mobo for blown caps, and didn't find any.

---

### Post by sbelz79 on 2009-11-18
I confirmed that I was able successfully drag-and-drop files to the external drive with no problems when I connected it to my g/f's computer while running the Ubuntu 9.04 live cd.  So the drive definitely works.

---

### Post by sbelz79 on 2009-12-21
OK, I solved the problem, but in a totally unexpected way.  I opened up my case and noticed that there was quite a bit of dust built up between my CPU's heatsink and its fan.  After cleaning all the dust out, I booted from an Ubuntu 9.10 CD and it was able to auto-mount my USB drive without a problem.  I backed up my data and reinstalled Ubuntu and now everything works splendidly (well, except that I'm seeing signs that my HDD might be dying on me, but now that my data's backed up, I can get a new one and reinstall everything again if it craps out.)

---

