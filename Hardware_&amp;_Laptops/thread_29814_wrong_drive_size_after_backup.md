---
title: "wrong drive size after backup"
date: 2005-04-26
forum: Hardware &amp; Laptops
---

### Post by demiurge on 2005-04-26
I changed hardisk and used driveimage 7 to copy my old 4G
partition to a new 6G partition. However ubuntu still thinks the
partition is only 4G! Even though it shows up as 6G in qtparted.
What's going on?

---

### Post by nad on 2005-04-26
Driveimage imaged only 4G of data. As it performed a low level write to your new partition your new partitions' file table shows only 4G of space.

---

### Post by demiurge on 2005-04-30
so is there any way to reclaim the space? I don't want to reinstall again.

---

### Post by nad on 2005-04-30
Use QTparted to resize your file system.

---

