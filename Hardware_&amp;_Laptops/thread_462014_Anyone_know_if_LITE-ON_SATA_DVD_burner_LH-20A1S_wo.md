---
title: "Anyone know if LITE-ON SATA DVD burner LH-20A1S works?"
date: 2007-06-02
forum: Hardware &amp; Laptops
---

### Post by mkoyle on 2007-06-02
I just stumbled across the LITE-ON LH-20A1S)... I haven't found anyone complaining that it doesn't work, but I haven't found anyone saying it does work, either.

I am just wondering what someone does to update the firmware if they only have an Ubuntu box and if anyone is sure this will work.

Since all of the CD/DVD stuff seems to be based on SCSI drivers, I am guessing that the SATA interface is no problem.

--Matthew

---

### Post by askmo on 2007-06-30
its working fine for me ( Feisty ). I did have to go into fstab and modify the line for the drive. After I did that and ran mount -a, everything worked fine.
Hope this helps.

from:
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto 0 0

to:
/dev/sg0 /media/cdrom1 udf,iso9660 user,noauto 0 0

---

