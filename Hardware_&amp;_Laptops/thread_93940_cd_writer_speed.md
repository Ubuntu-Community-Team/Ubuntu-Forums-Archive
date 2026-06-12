---
title: "cd writer speed"
date: 2005-11-23
forum: Hardware &amp; Laptops
---

### Post by hil on 2005-11-23
How can I decide my CDROM Writer speed? My CDROM is "matshita ujda720". From [http://database.vso-software.fr/view_cdwriter.php?UnitID=MATSHITA+UJDA720+DVD%2FCDRW&PHPSESSID=d240563ca94dbe5bf98519a5b09d8932]("http://database.vso-software.fr/view_cdwriter.php?UnitID=MATSHITA+UJDA720+DVD%2FCDRW&PHPSESSID=d240563ca94dbe5bf98519a5b09d8932") I can see the write speed="8x" but how can I get the speed information in ubuntu? Although K3b prompted "8x" which was the correct suggestion but how did K3b figure out "8x" when it first started in the determining speed dialogue?

---

### Post by az on 2005-11-23
cdrecord dev=/dev/hdb -prcap


You can do this with cdrdao (as well as other applications, I think)

---

