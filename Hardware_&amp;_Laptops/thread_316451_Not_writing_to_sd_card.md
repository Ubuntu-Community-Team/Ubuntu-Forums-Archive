---
title: "Not writing to sd card"
date: 2006-12-10
forum: Hardware &amp; Laptops
---

### Post by ChronoStriker1 on 2006-12-10
I have a Averatec 1050 and with edgy I have been able to read from my built in sd card reader.  The only problem Im having is that it wont write to it.  It looks like it does with small files but when you unmount it and then remount it the files are gone and if you copy larger files (and by larger I mean 10 - 30mb) it ends up erroring its an I/O error.  I was wondering if its just the reader isnt fully supported or Im not doing something correct.

---

### Post by ChronoStriker1 on 2006-12-20
Since no one answered me i had to look into it myself some more.  I found that as much as /media/mmcdisk/ said I had ownership of it didnt.  I had to sudo chown myusername:myusername /media/mmcdisk/ that made it work.  Only one problem if un mount it, when I remount it I need to type the command again.  Is there anyway to automatically gain ownership of disk when it mounts?

---

