---
title: "Need advice re: installing/partitioning..."
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by odoreater on 2009-05-11
Hey all,
Going to try out Ubuntu, but still need to have windows XP around, so interested in using some kind of multi-booting option.
I've got two separate HD's, the first, a 640GB drive with XP installed on the only partition, the second HD is 300 GB's, which is basically all free space.
Would like to install Ubuntu on a partition of the second HD (maybe about 100GB's), as I'd like to have some storage on the 2nd HD available to XP, but would prefer not to use Wubi to do the installation.  I'm not familiar with grub and not all too familiar with the intricacies of partitioning, but does anyone have some ideas as to the best way of proceeding?
Thanks,
Abe

---

### Post by gamblor01 on 2009-05-11
The Ubuntu installer should make it very easy for you.  A few steps into the installation process you can choose how to partition.  Alternatively you can boot up into the live cd and then use a utility like cdfisk to partition the second drive.  Assuming it is truly the second disk (/dev/sdb), meaning you haven't told BIOS to swap the order or anything like that then it would be done like so:

```

sudo cfdisk /dev/sdb

```If you want, boot up with the Ubuntu live CD and then paste the output of the following command:

```

sudo fdisk -l

```That will show us how your drives are setup and we can go from there.

You could also use a utility like gparted.  I have never used it myself but I have only heard wonderful things about it.  I tend to just use cfdisk myself.

---

