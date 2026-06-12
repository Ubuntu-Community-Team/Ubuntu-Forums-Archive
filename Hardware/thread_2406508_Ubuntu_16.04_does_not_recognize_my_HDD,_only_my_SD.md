---
title: "Ubuntu 16.04 does not recognize my HDD, only my SDD."
date: 2018-11-21
forum: Hardware
---

### Post by nat4533 on 2018-11-21
I've bought my laptop 2 days ago (Dell Inspiron 15 5570 128GB SSD + 1TB HDD )  and I've noticed that Ubuntu does not recognize my hard disk and uses only my ssd. I have no idea how to fix it, so if anyone could've help me I would be grateful. :KS

---

### Post by 23dornot23d on 2018-11-21
It could be related to the Main partition being NTFS

[http://manpages.ubuntu.com/manpages/xenial/man8/ntfs-3g.8.html](http://manpages.ubuntu.com/manpages/xenial/man8/ntfs-3g.8.html)

Someone else could maybe help you on this - as I only use Linux Systems nowadays ........... but the fact that the two pictures you
showed at least know the drives are there .......... but on the gparted one it seems not to recognize the filesystem - so possibly just
missing a couple of needed programs.

$ sudo apt install ntfs-3g

is possibly one .......... may be better waiting for someone else just to confirm what is needed now on newer systems.

---

### Post by nat4533 on 2018-11-22
I don't know if I did wrong but I click on format partition and choose to be Compatible with Linux systems(ext4) and now I can move my files there.

---

