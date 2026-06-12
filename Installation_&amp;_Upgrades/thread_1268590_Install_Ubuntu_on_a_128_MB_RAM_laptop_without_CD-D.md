---
title: "Install Ubuntu on a 128 MB RAM laptop without CD-Drive."
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by bharadwaj on 2009-09-17
Hi,

I have a very old laptop which comes with 128 MB memory 10 GB HDD No Floppy Drive, No CD Drive. 

Recently I had an OS crash and my OS was gone. I tried booting with external Drive but failed, I do not have a network to boot from network. I tried the below guide to boot from USB

[http://www.pendrivelinux.com/usb-kubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-kubuntu-904-persistent-install-windows/)

but nothing happens(may due to poor memory) I have a 32 GB USB pendrive, a desktop with windows/Linux. My Laptop supports USB FDD booting. Please help me through the process of getting my laptop up and running.

Thank You!

---

### Post by kerry_s on 2009-09-17
> 128 MB memory

:lolflag:
use unetbootin to make a bootable usb:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

finding a distro that works with so little ram is the hard part.

---

### Post by analoog on 2009-09-17
You might want to consider xubuntu on a laptop with those specs.

---

### Post by rob-ward on 2009-09-17
I think xubuntu may be overkill, you may want to try installiing ubuntu from the mini disk and installing lxde, that will be ligheter than ubuntu or xubuntu

---

### Post by wojox on 2009-09-17
Or maybe [Puppy Linux](http://www.puppylinux.org/)

---

### Post by mantelo on 2009-09-17
I have a laptop similar to yours (sony PCG-SR17). 128 MB, 20 GB, no cd.

The best I could come with was Puppy Linux (it works really nice).

For booting I used wingrub (my bios wouldn't take grub), which is a version of grub for windows systems with (I had win 2000). If your disk is using fat (win 95, 98 or me), you could use syslinux or grub4dos.

---

### Post by bharadwaj on 2009-09-18
> **mantelo said:**
> 
For booting I used wingrub (my bios wouldn't take grub), which is a version of grub for windows systems with (I had win 2000). If your disk is using fat (win 95, 98 or me), you could use syslinux or grub4dos.

My OS is corrupt so I can't do these!!

---

### Post by mantelo on 2009-09-20
If your pc boots from usb, you will only need to download puppy to the pen drive and boot it. From there you can perform the install  to the hard drive. If the system does not support usb boot, you will have to extract the hard drive and connect it to a different PC in order to format it and install puppy.


Good luck!

---

