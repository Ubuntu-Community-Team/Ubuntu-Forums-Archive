---
title: "Hitachi Deskstar  HDS722580VLAT20"
date: 2008-02-06
forum: Hardware &amp; Laptops
---

### Post by ILYA99 on 2008-02-06
Hi !

I got Hitachi Deskstar  HDS722580VLAT20 60G hard drive formated as FAT32 with valuable data on it.

Trying to add it as additional HD to XUBUNTU  running at old Pentium 3 system with Intel's mother board.
After I connected it to IDE bus the system boot notably extended.
At the end of the boot process i cannot see any new hard drives added to system.
The  ls /dev/hd* command returns only hda  & hdb(Cd-rom)  devices therefore i cannot mount it.

The Hard Disk worked fine with Windows XP on other machine, moreover
I booted  with KNOPPIX 3.7 on that particular system, the HD was identified as hdc and the data was accessible.

What should I do ?

Thanks to all.

---

### Post by ILYA99 on 2008-02-08
Hi  an  update about this one :

Solved by setting Plug & Play option in BIOS to NO :)

maybe its a bug ? :confused:

---

