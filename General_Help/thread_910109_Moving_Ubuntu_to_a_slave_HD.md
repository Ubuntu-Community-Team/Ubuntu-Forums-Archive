---
title: "Moving Ubuntu to a slave HD"
date: 2008-09-04
forum: General Help
---

### Post by aqui_c on 2008-09-04
Hi All!
I'm using Ubuntu in a partition of the Master HD (shared with Windows.)
I want to install a HD just for Ubuntu, but it will be a slave HD, right?
So, how can I move the installation to a secondary drive?

Thanks!

---

### Post by caljohnsmith on 2008-09-04
I assume your slave HDD is at least as big as your master HDD? If so, you can copy over a byte-per-byte clone of your master HDD to your slave with the following (assuming sda is master and sdb is slave):
```
sudo dd if=/dev/sda of=/dev/sdb bs=32256
```
That also copies the MBR. If you slave is larger than your master (not identical in size), you may have to then go into gparted or similar to resize your partitions to fill the whole space if you don't want to lose the extra space. Let me know how it goes.

---

### Post by eggdeng on 2008-09-04
> how can I move the installation to a secondary drive
You should be able to do this using the gparted live CD [http://gparted.sourceforge.net/download.php]("http://gparted.sourceforge.net/download.php") or even the version of gparted on the Ubuntu live CD. How-to at [http://gparted.sourceforge.net/larry/move/move.htm]("http://gparted.sourceforge.net/larry/move/move.htm")
The problems will come if you delete your original Ubuntu partition as, depending on how you did the install, GRUB will have at least some of its files on the Ubuntu partition & you will be left with an unbootable system. So you will need to look carefully in advance at ways of restoring the GRUB bootloader.

---

