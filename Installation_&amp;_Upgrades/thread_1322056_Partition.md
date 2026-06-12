---
title: "Partition"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by dertdamb on 2009-11-10
About how long should it take to re-partition the hard drive when you install Ubuntu? I have Vista already and am doing a dual boot with Ubuntu. There are 4 total partitions the computer needs to make. One is a few megabytes that cannot be removed, another is for restoring Vista (about 9GB), another is for Vista itself (about 80GB), and the last is Ubuntu (about 140GB, probably will be reduced later). Any thoughts?

---

### Post by raymondh on 2009-11-10
> **dertdamb said:**
> About how long should it take to re-partition the hard drive when you install Ubuntu? I have Vista already and am doing a dual boot with Ubuntu. There are 4 total partitions the computer needs to make. One is a few megabytes that cannot be removed, another is for restoring Vista (about 9GB), another is for Vista itself (about 80GB), and the last is Ubuntu (about 140GB, probably will be reduced later). Any thoughts?

You have the 4-rule to think about.  4 PRIMARY partitions or 3 PRIMARY + 1 EXTENDED (which can contain as much logical partitions as you wish).

By default, unless you decide otherwise, Ubuntu will require 2 partitions ....... root and swap.  Deciding otherwise means you decide not to have swap.  Nevertheless, I suggest you make the last partition an EXTENDED partition and then make ubuntu root and swap logical partitions residing inside the extended.

Partitioning using gparted is fast (subjectively ... for me).  I have a 320GB HD and it seems to just take at most 20 minutes to create partitions.

Defrag Vista (2x is you have the time) if you are taking space away from it to create for Ubuntu.  Also, you can use Vista's disk management tool to shrink Vista appropriately.  Afterwards, you can use gparted to create the specific partitions and manually install unto them.  Or, you can just choose to install in "largest continuos space" but I am not sure whether ubiquity (the installer) will automatically create the extended/logical partitions for you.

When using gparted to create the partitions, I suggest you uncheck the "round to cylinder" box.

Have a working back-up of your files.

Those are my thoughts :)

---

