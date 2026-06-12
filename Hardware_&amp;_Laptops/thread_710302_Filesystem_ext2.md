---
title: "Filesystem ext2"
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by MDKSIGN on 2008-02-28
I've f*cked up my mums laptop, I put Ubuntu on and she doesn't like it at all. Now I took Ubuntu off and tried to load windows back on using recovery disks but it says the filesystem is not ntfs (Its ext3). Theres no option to convert the filesystem type. Please help as its a new laptop she got recently and I feel really guilty as its not working at the min!

Any help much appreciated.

- matt

---

### Post by chrisdeckard on 2008-02-28
When reinstalling Windows, delete the partition before trying to install to it.

If, for some reason, the install set you have doesn't do that, load up your Ubuntu live CD, open a terminal and remove the partitions using fdisk.

-Chris

---

### Post by taurus on 2008-02-28
Or use gparted, System -> Administration, from the LiveCD and delete all the partitions.  Then, format the harddrive to ntfs.

---

