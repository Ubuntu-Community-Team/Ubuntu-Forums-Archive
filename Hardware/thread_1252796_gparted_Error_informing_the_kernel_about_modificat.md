---
title: "gparted Error informing the kernel about modifications to partition"
date: 2009-08-29
forum: Hardware
---

### Post by crabsody on 2009-08-29
&#919;ello everybody. I bought yesterday a usb hard drive (WD 320GB my passport). I used gparted to format it as an ext2 which I did with success. Then I changed my mind and decided to format it again using gparted. IMPOSSIBLE. gparted understands the drive but when I try to format it I get the above errors-warnings

> ======================
libparted : 1.8.8
======================
Error informing the kernel about modifications to partition /dev/sdc1p1 -- Invalid argument.  This means Linux won't know about any changes you made to /dev/sdc1p1 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
The kernel was unable to re-read the partition table on /dev/sdc1 (Invalid argument).  This means Linux won't know anything about the modifications you made until you reboot.  You should reboot your computer before doing anything with /dev/sdc1.
Could not stat device sdc1 - No such file or directory.

Of course I had rebooted since several times but nothing changes. Has anyone an idea what is happening??

---

### Post by dandnsmith on 2009-08-29
No idea what the cause of the error message might be, but, if that is the only partition on the hdd, you could zero out the first block (thus removing the existing partition table) and do the exercise effectively from scratch.

For blanking the first block (just in case you haven't had occasion to do it):

*dd if=/dev/zero of=/dev/sdc bs=512 count=1*

---

