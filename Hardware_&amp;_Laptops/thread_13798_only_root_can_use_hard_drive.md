---
title: "only root can use hard drive"
date: 2005-02-02
forum: Hardware &amp; Laptops
---

### Post by ogami1972 on 2005-02-02
so far, kinda good- nice install, everything peachy, but...
i can not use my storage drive ( 80 gig fat32)- unless i log in as root!
i chose "keep and use data", and have set the mount point to /dos-
 as user, i can see the contents, but as "footprint" icons... not realy files- but root can access these files just fine
 :confused: 
any ideas?

---

### Post by ogami1972 on 2005-02-02
never mind... added this to fstab
/dev/hdb1       /media/mymedia  vfat    umask=000        0
(also made the /mymedia directory)
then rebooted-
nice job ubuntu!

---

### Post by Sepero on 2005-02-02
How were you mounting the drive previously?

---

