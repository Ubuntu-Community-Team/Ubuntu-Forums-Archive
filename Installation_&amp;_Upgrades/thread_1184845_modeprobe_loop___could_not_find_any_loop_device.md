---
title: "modeprobe loop   could not find any loop device"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by [3w`Sparky] on 2009-06-11
Hi All, 

I am looking to try and mount an encrypted squashfs and boot the O/S image inside it , I have got the file encrypted using luks the file is decryptable using a live O/S and running the cryptsetup luksOpen `losetup -s -f /cdrom/casper/filesystem.squashfs` decrypt 

However when i boot the pc with the tweaked initrd.gz config it complains stating the following:

losetup: could not find any loop device. Maybe this kernel does not know about the loop device? (if so, recomplie or `modprobe loop`.)

if i do a modprobe loop from the initramfs it seems to take it but not fix anything.

so the question is , how do i get the kernel to be aware of this ?

not done kernel compiling before so if you know your have to talk VERY LOUDLY AND SLOWLY 



thanks 
Terry

---

