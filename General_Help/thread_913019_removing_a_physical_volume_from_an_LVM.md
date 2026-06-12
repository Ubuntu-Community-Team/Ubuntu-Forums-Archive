---
title: "removing a physical volume from an LVM"
date: 2008-09-07
forum: General Help
---

### Post by boast on 2008-09-07
how can I remove a physical volume that is not formatted as an LVM from an LVM. I used lvextend to extend a logical volume with a physical volume that wasn't formatted and still had its old files. 

Now when removing the physical volume, I cannot because it states there are no extends to allocate the data.

---

### Post by beaver29 on 2008-09-07
i just worked thru a problem last week with a disk that had an LVM partition.  i found this site helpful:

[http://www.howtoforge.com/linux_lvm]("http://www.howtoforge.com/linux_lvm")

---

