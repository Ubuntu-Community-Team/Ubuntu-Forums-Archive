---
title: "Failed to create paritition - on install"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by Str0k3r on 2009-04-16
I have been trying to dual boot install Linux on my desktop pc with XP installed. The same issue has been occuring with my Ubuntu or my Mint installs and only on this pc. This seems to occur whether I manually define my partitions during the install or even if I boot a gparted live cd, define/format partitions and then try to run install afterwards. Partitions are on second half of my hdd.

15gb /
3gb /var
3gb /swap

When the linux install gets to the partition stage all looks good, choose manual, my partitions are defined, install process begins, gets to 15% then stays there for a few minutes. I will then get the error "failed to create partition" and install takes me back to partition manager, but its all greyed out.


Windows XP runs fine on this pc, my HDD checks all come out ok. any ideas? Is there some sort of HDD setting in the bios I am missing, I see no compatibility mode or anything. My install disks work fine in other pc's so I know its something with this one.  Im sooooo frustrated,,,help!

Asus Pq5pro
Maxtor Sata 500gb

---

### Post by unutbu on 2009-04-16
Please post the output of 
```

sudo fdisk -l
```

Have you checked the integrity of your partition table using testdisk?

---

