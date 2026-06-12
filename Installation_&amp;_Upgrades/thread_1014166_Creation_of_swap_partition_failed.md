---
title: "Creation of swap partition failed"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by malderhout on 2008-12-17
When i install ubuntu 8.04 or 8.10 i get the following error during format:

"The creation of swap space in partition #5 of SCSIl (0,0,0) (sda) failed"

further info laptop:
compaq nw8480
Dual core T7600
100G scsi disc?

Orginally Windows was installed with a locked HDD? Is this the problem. I expect that i can overwrite the hdd. I want to remove Windows. 

Greets
Maikel

---

### Post by taurus on 2008-12-17
How many partitions do you have on your harddrive?  From the LiveCD, open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

