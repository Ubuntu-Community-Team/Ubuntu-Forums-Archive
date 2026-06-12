---
title: "USB Drive not mounting"
date: 2010-01-24
forum: Hardware
---

### Post by mullinsn2000 on 2010-01-24
I have a netbook which I bought used.  The netbook originally had the Mie OS/interface.  The person I bought it from installed XP on it.  I didn't like how slow it was with XP so I installed Ubuntu from the USB drive.  Now it is recognizing the USB drive as a CD-ROM drive and is unable to mount it.  How do I fix this problem?  Thanks!

Ubuntu 8.04
Sandisk Cruzer Micro 8GB (removed the U3 software)

---

### Post by mullinsn2000 on 2010-01-24
IS there a way for me to chnge how it sees the USB drive?  I have a file I need to put on this USB drive to take to a class.

---

### Post by jbiggs12 on 2010-01-24
If you've flashed a usb drive from a .iso file or any other disk image file, then it should appear as a read-only disk. If that's the case, then you can try right-clicking the disk and clicking "Format..." I'd recommend formatting it as FAT32, you can name it whatever you want :D

---

### Post by mullinsn2000 on 2010-01-24
I have formatted it using a Windows 7 computer, Windows XP computer, and using gpart (or whatever it is called) on the Ubuntu 8.04 computer. The problem is the Ubuntu computer is seeing the drive as a CDROM so I am unable to mount it.  I have already removed the U3 software from the device and formatted it again.  I need to find out how to get Ubuntu to see it as a USB Drive and not as a CDROM.  The computer recognizes it, but it see it as CDROM and I can not mount it.  It was formatted to FAT32.

---

### Post by mullinsn2000 on 2010-01-24
Got it working!

For others that have same problem:

sudo gedit /etc/fstab

Remove the line about the cdrom0, save and reboot.  If the drive doesn't automount, then mount it and it should be working.

---

