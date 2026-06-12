---
title: "Auto mount works on WD MyBook but not on WD Elements"
date: 2014-05-02
forum: Hardware
---

### Post by andreas-fischl on 2014-05-02
I got two external HDs:
[LIST]
[*]A approx two year old Western Digital "My Book Essential" (2TB) 
[*]A brand new Western Digital "Elements" (2TB) 
[/LIST]

While the old WD MyBook gets automatically mounted on my desktop (Unity, Ubuntu 13.10 Saucy Salamander) since the time I have bought it, but the new WD Elements stubbornly fails to mount automatically. I can mount it manually though ([FONT=courier new]sudo mount /dev/sdd1 /mnt[/FONT] as well as [FONT=courier new]udisks --mount /dev/sdd1[/FONT]).

I tried reformatting (ext3 and ext4), creating a new MSDOS parition table with gparted, and even reformatting it with NTFS in Windows.

I attached the dmsg output when plugging in of both drives if that is of any help.

Has anybody an idea what's the matter with the new external HD?

---

