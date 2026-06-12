---
title: "DVD Drive not mounting"
date: 2011-03-27
forum: Hardware
---

### Post by Loki*PI on 2011-03-27
I've been reading the forum for three hours, I know there are a lot DVD mounting threads but nothing seems relevant or didn't work.

10.04 upgrade. DVD drive has been working for mouths, no problem.

Boot up today and the DVD drive will not mount. Get the: "mount: special device /dev/scd0 does not exist" message. Everything else seems normal.

fstab has line:
/dev/scd0   /media/cdrom0   udf,iso9660 user,noauto     0       0

This has been working until today. Something get changed?  System is current with updates.

Thanks everyone.

---

### Post by Loki*PI on 2011-04-05
I've had so much trouble with Ubuntu and DVD drives that I assumed the problem was OS. Turn out to be a hardware issue. Pulling the cables and reseating resolved it. However a couple days later the hd went, don't know as there is a connection.

---

