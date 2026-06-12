---
title: "How to use an empty HDD partition?"
date: 2005-02-27
forum: Hardware &amp; Laptops
---

### Post by siDDis on 2005-02-27
Whenever I use nautilus to browse through my files it says its only 2GB left. I have another partition on my disk which have 50GB free. How do I set ubuntu to use this free space?

Its already formatted with QTparted.

---

### Post by alastair on 2005-02-27
Formatted? With a filesystem made or just a partition tag? Linux is different to DOS.

Assuming device /dev/hda - and partitiion X is the unused one

First list your partitions :

sudo fdisk -l /dev/hda

Look at partition X - is it "type" Linux?

If so, if it does NOT have data on it, make a new filesystem (this will DESTROY DATA on this partition) :

mkfs.ext3 /dev/hdaX

Make a new place to mount it :

mkdir /mnt/newdata

mount it :

mount /dev/hdaX /mnt/newdata

chmod 777 /mnt/newdata
or
chown <yourname>.<yourgroup> /mnt/newdata

---

### Post by siDDis on 2005-02-27
thanks :)

---

