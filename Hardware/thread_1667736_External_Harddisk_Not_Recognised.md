---
title: "External Harddisk Not Recognised"
date: 2011-01-15
forum: Hardware
---

### Post by LinDoc on 2011-01-15
I have a Maxtor OneTouch External Harddisk 160gb that i purchased recently. At first my Ubuntu 10.10 could not mount it. I opened disk utility which recognized it but with no filesystem. I proceeded to try formatting it but this error popped up 


[INDENT]*Error creating partition table: helper exited with exit code 1: Error calling fsync(2)    on /dev/sdb: Input/output error *[/INDENT]


I resorted to Gparted. Things turned worse; it wasn't even listed in the list of devices. Does anyone have a solution to this problem? Any help is appreciated.

---

### Post by LinDoc on 2011-01-15
It looks like i should create a new partition table. I am not experienced in editing partition tables. I know fdisk can do that but, strangely, whenever i try using fdisk on that drive, am told that [INDENT][INDENT]Unable to read /dev/sdb
[/INDENT][/INDENT]. Anyone with any suggestions?

---

### Post by LinDoc on 2011-01-15
Or which other programs are available that are used to create/edit partition tables?

---

