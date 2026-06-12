---
title: "reformat a new USB Drive?"
date: 2009-04-09
forum: Hardware
---

### Post by tabarnackle on 2009-04-09
i just picked up a 4 GIG sandisk that i will eventually use to create a backup on in case. the inevitable happens. 

how would i go about wiping it?
-dave

---

### Post by tea for one on 2009-04-09
I would use Gparted.

System - Administration - Partition Editor

Scan the drives
Identify and select the USB drive 
Delete all partition(s)
Create new partition(s)
Format to desired file system

Please be VERY careful because Gparted is a powerful utility and it is easy to lose data and partitions unexpectedly.

If you are unsure with any of the options, it is better to do some research rather than destroy important files.

---

### Post by tabarnackle on 2009-04-09
ok i have it wiped. thanks alot. (i left it without a file system for now)

---

