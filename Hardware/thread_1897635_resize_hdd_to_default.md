---
title: "resize hdd to default"
date: 2011-12-19
forum: Hardware
---

### Post by densant on 2011-12-19
i was trying to install ubuntu on a external hard drive (500GB), and at the end i decided not to, now the it only has 232GB available as total size. question is how do i restore the hard drive's original size?
by the way it's a Western Digital 500GB.

---

### Post by dabl on 2011-12-19
You boot a Live CD or USB stick that has Gparted on it.  My favorite is the [[COLOR="SeaGreen"]**Parted Magic Live USB stick**[/COLOR]](http://partedmagic.com/doku.php?id=downloads).

Then you use GParted to change the partitioning back as you want it, including deleting the partition that Ubuntu made during installation.

Note that partitioning hard drives has the risk of data loss -- if you have valuable data on the hard drive, better back it up first.

---

