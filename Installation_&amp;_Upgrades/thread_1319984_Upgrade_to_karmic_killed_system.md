---
title: "Upgrade to karmic killed system"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by usaar33 on 2009-11-08
After upgrading to karmic from jaunty, I cannot boot my computer up.

I get the error 'ALERT! /dev/disk/by-uuid/some_number does not exist.  Dropping to shell.

In the busy box shell, I do not have a /dev/disk/by-uuid directory.  There are by-id and by-path subdirectories with correct symlinks to /dev/sda*.  

How can I fix this?  I would like to get back to using my computer...

---

### Post by AndreLeComte on 2009-11-08
usaar33, I have the same error posted two threads below this. Are you able to boot by selecting older kernels from the grub menu?

---

### Post by usaar33 on 2009-11-08
Nope, I'm droped to the maintenance console.

---

### Post by AndreLeComte on 2009-11-08
I tried replacing 'some_number' with '/dev/sdb1' in my /boot/grub/menu.lst file, but it didn't fix anything. The fact that I can boot the 2.6.28 kernel has me stumped.

---

### Post by AndreLeComte on 2009-11-09
This basically solved the issue for me:
> **arekku said:**
> [Here](http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html)

Replace your nonworking initrd file with a previous version. For you Andre all you need to do is (just in case you are new)

cd /boot
sudo mv initrd.img-2.6.31-14-generic backup
sudo cp initrd.img-2.6.28-16-generic initrd.img-2.6.31-14-generic

---

### Post by usaar33 on 2009-11-09
Thanks Andre for the top, but there seems to be no /boot directory accessible in busybox.  I'm not as fortunate as you in that I have no working kernels and due to a defective cd-rom drive, I can't use a live cd.

---

