---
title: "Add a partition to a micro sd card"
date: 2008-04-05
forum: Hardware &amp; Laptops
---

### Post by mckenm1m on 2008-04-05
Please be gentle. I am trying to add a micro sd card to a mobile phone. It is a SanDisk 4 gb disc and a Samsung E570 phone. The disc was preformatted as FAT32 but the phone only supports FAT16. Tried reformatting as FAT16 but Windows (Vista HP) is not having it. This I now discover is because FAT16 can only be used up to 2 gb. Can I therefore add a partition to the disk, and if so how, as I have tried and the partitioning options in disk management are greyed out for no reason I can understand.

Sadly I am now at the outer limits of my technical competence, so could really use some patient help.

Thanks.

---

### Post by shak541 on 2008-04-05
use gnome partion editor or a gParted live cd and shrink the main partition of the card then make a new partition. Right click the new partition and click format to: fat 16. as for the problem with it being grayed out ..... unmount it first. or right click the partition and click unmount. :D hope this helps out.

---

