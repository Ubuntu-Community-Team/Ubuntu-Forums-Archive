---
title: "SATA RAID0 swap problem"
date: 2005-06-07
forum: Hardware &amp; Laptops
---

### Post by Antiparadigm on 2005-06-07
Hey all,

To begin my machine specs:
AMD Athlon XP (Throughbred) 2600+
1 GB Corsair XMS DDR400 Duel channel
Gigabyte K7-N400 Pro mobo
2x Segate Berracuda SATA disks (80 GB each)
1x Maxtor 80GB IDE HD
Nvidia Geforce 5600 w/ 256MB

The Sata raid controller is SIL 3112 and runs as a software raid.  

Everything works fine in ubuntu, except for my swap area.  I get messages saying something like:
```
VFS:  Can't find ext3 FS on device MD1
``` 

I am in a rush so I can't get the exact message right now.  I'll comeback and edit this when I get home from work.

I guess my question right now is, can you handle raid setups like a regular device?

Like would I be able to format /dev/md1 as swap then swapon /dev/md1?

Thank you for your help.

---

