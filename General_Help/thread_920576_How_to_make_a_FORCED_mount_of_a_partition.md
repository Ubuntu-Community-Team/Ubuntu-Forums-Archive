---
title: "How to make a FORCED mount of a partition?"
date: 2008-09-15
forum: General Help
---

### Post by andoo on 2008-09-15
hello everyone, i have this problem,  i had 3 partitions on my PC, 1-XP, 2-games and stuff, 3-programs like microsoft office antiviruses and stuff like that, first 2 are ntfs formats and the third is fat32, i deleted the first one and out of the free space created a partiton for Ubuntu and one for "swap" or something like that. Now after i installed Ubuntu i cant read the content of my 2nd and 3rd partitions, it gives me this kind of error "Cannot mount partition   /dev/sda5 is not a removable device"  ok now one of my friends that is using Ubuntu told me that i have to make a Forced mount but i have no ideea how to do that, maybe u can help me. Thank you.

---

### Post by vanadium on 2008-09-15
You should not force if you care for the data on that disk. Instead load Windows and have the ntfs partitions checked using the Windows tools. Before accessing Windows drives by Ubuntu, they shouldhave been properly disconnected in Windows, i.e. by fully shutting down Windows 9no hibernate).

---

