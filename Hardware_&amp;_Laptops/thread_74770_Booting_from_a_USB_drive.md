---
title: "Booting from a USB drive"
date: 2005-10-12
forum: Hardware &amp; Laptops
---

### Post by stephane perennes on 2005-10-12
I want to boot from a USB hard drive. 

How to do that on the previous release was explained here 

[http://www.ubuntuforums.org/showthread.php?t=5151](http://www.ubuntuforums.org/showthread.php?t=5151)

Basically one needed to create a special boot image 
including usb modules and waiting long enough 
so that the root of the file system will be up and mounted. 

The procedure was : 

'nano /target/etc/mkinitrd/mkinitrd.conf'
EDIT the line that says DELAY=0 and change it to anything over 10 (i chose 15 to be safe).
chroot /target
mount -tproc none /proc
mkinitrd -o /boot/usbinitrd.img-(kernel version OPTIONAL)


etc ... 

In the current distribution mkinitrd do not exist, instead one find something that creates a ram image 

I don't know how to create a boot image that will be able to see the root file system.

Currently instalation works fine. disks are  detected lilo is instaled 
on the mbr of my usb hardisk but when it boots 
the init image tries to access the root of the file system before 
detection or mouting. 

I end up with a main root missing. 


Thanks for any help

---

### Post by Jurgen272 on 2005-10-13
I don't know if it helps but just follow this link [http://fuzzymunchkin.dyndns.org/tdot/usbkeyfob/index.php]("http://fuzzymunchkin.dyndns.org/tdot/usbkeyfob/index.php")
It's not Ubuntu but DSL (Damn Small Linux).

---

