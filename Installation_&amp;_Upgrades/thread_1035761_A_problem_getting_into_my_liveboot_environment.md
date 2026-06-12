---
title: "A problem getting into my liveboot environment"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by Darael on 2009-01-10
I've been trying for a very long time to get Ubuntu onto my machine.  It doesn't want to boot off a CD, but eventually I managed to get into a live USB drive.  However, while I know that I have an amd64 architecture processor, I can't get into - well, anything - when using a usb drive made live with any of the amd64 architecture cds.  I've tried with both the desktop live and the alternate ISOs.  

  When I boot from the usb stick, I can get to the disc menu and even reach the loading/splash screen when I choose to install.  However, after that I get a series of terminal messages, advancing at a snail's pace, but even after leaving it for several hours, I don't get anywhere.  

  It works with the i386 version, but I'd like to make the best use of my system that I can.  Can anyone give any suggestions?
If I'm not likely to get it working in the forseeable future, that's OK and I'll just install a 32-bit system, but until I'm sure of that I'd like to keep trying.

---

### Post by kranny on 2009-01-10
Which version you are trying to install.Did you inculde the amd64 installer on the USBDrive?

---

### Post by Darael on 2009-01-10
I'm trying to install intrepid.  The usb drive was set up with unetbootin and the amd64 versions of the install cd ISOs - I've tried both the live and the alternate versions and I get the same result.

---

### Post by kranny on 2009-01-10
dd the drive to zero out the partition table on the usb stick, repartition it,and try again

To zero out the partition table you just need to know what your usb stick is called (e.g. /dev/sdb,sdc.....). You can find this by doing ```
sudo fdisk -l
```. Once you know what it is make sure it's unmounted. Then, if, for example, it was /dev/sdb, you would do the following:

```
sudo dd if=/dev/zero of=/dev/sdb bs=512 count=1
```

Takes about a second. Pull out the stick and then reinsert it and partition it with gparted.

---

### Post by Darael on 2009-01-10
There's one problem with that - I'm stuck in Windows until I can get the drive working...
I've got another machine somewhere that loads a live CD fine - I'll find it, try what you suggested, and get back.

---

### Post by Darael on 2009-01-11
OK, I got into my install disk.  Now I find that the 64-bit environment reports my system memory as 2.9GB, where the 32-bit one reported it as 3GB and the actual value is 4.  I also found that after I tried to activate the proprietary driver for my graphics card, I became restricted to a 640x480 screen resolution, and that this restriction persisted after I deactivated the driver again.  Something strange is going on with my computer.

---

