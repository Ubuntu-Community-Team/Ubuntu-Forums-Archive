---
title: "Ubuntu thinks my Sandisk micro usb drive is a cd rom"
date: 2007-03-26
forum: Hardware &amp; Laptops
---

### Post by monaleilani on 2007-03-26
I can't get my 2gb usb drive to work. I am very new to Ubuntu, just installed EE.  I have tried mounting it and every time it tells me that the medium can't be found. I've heard talk of something called "plugdev" and I have no clue what that is.
It is showing up as "CD-ROM disc" on my desktop. When I do "lsusb", however, it gives me the correct name of the drive. I know it is showing up in /dev/ as /sda. Can anyone help?

---

### Post by s0cket on 2007-03-26
My experance with Ubuntu and USB drives and SD card readers has been very good.  I'm inclinded to believe your key has a weird controller on it or one thats not very well tested in Linux.  If Ubuntu doesn't support (or treats it badly) it then most likely no Linux distro will like it.

Also what file system is the key formatted with?  That might have something to do with it however unlikely.

---

### Post by monaleilani on 2007-03-26
My drive is one that has a software called U3 installed on it. When the drive is put into a windows drive, it does two things: creates a virtual CD-ROM drive with the U3 software on it, and then creates the removable drive with the majority of the space on it. I suspect that software might be the problem - the Sandisk site says drives with U3 on it simply work as flash drives when plugged into a linux system, but since all I'm getting is a "cd-rom disc" when I plug the drive into Ubuntu, I wonder if the U3 software is interfering somehow. The drive is formatted as Fat.

---

### Post by s0cket on 2007-03-26
It is the U3 software.  You can remove it in Windows easily.  I have a Sandisk U3 as well. =)

EDIT:  They use a sneaky trick with their controller and key firmware to make the drive look like a CDROM so they can use the autorun in Windows for their crappy U3 software.  There is an option in their software to remove that virtual drive... but it only runs in Windows.  I would not trust fdisk to properly delete that drive since it's accomplished with a firmware trick.

---

