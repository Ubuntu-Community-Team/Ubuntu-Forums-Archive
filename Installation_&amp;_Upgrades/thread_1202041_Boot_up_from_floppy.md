---
title: "Boot up from floppy"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by healee on 2009-07-01
In view of the problem I reported on [http://ubuntuforums.org/showthread.php?t=1198067](http://ubuntuforums.org/showthread.php?t=1198067), I have re-installed my Windows servers and so lost the access to the ubuntu partition.  I am thinking of booting up the ubuntu with a floppy instead of reinstalling ubuntu and risking the loss of the Window server partitions.  However, the installation process does not give me an option to create a floppy disk to boot the system.  How could I get a boot up floppy?

---

### Post by oldfred on 2009-07-01
SuperGrub will allow you to create floppy or USB boot disks.
[http://www.supergrubdisk.org/index.php?pid=6](http://www.supergrubdisk.org/index.php?pid=6)
Ubuntu has gotten too big to fit on a floppy. If you are willing to use GRUB to multiboot you can boot all your Windows and Ubuntu from one Grub boot menu. Another forum has info on how to boot from 145 systems. 
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)
I am using chain booting to boot WindowsXP, 32 bit Ubuntu and 64 bit Ubuntu, with space for at least one more to experiment with.

---

### Post by healee on 2009-07-05
Thanks!  The SuperGrub not only booted into ubuntu for me but installed the Grub which saw all my partitions including the two Windows severs unlike the Grub loader that came with the ubuntu which did not see the two Windows servers.

---

