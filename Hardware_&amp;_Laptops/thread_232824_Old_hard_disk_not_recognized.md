---
title: "Old hard disk not recognized"
date: 2006-08-09
forum: Hardware &amp; Laptops
---

### Post by pwilbert on 2006-08-09
I need to rescue some files from an old hard disk but it is not being recognized by Ubuntu. During the boot the bios show its model ST32351A (it is a SEAGATE with 2.5 GB) but when I try to list it with fdisk -l (under root) I  can only see my other two hard disks. My Ubuntu version is 6.06 LTS - the Dapper Drake - released in June 2006.

Any directions?

Rgds, 

Paulo.

---

### Post by bscbrit on 2006-08-09
Any idea on how the hard drive is formatted?

Has it got the correct master / slave jumper set?

Are you using a live disk and, if not, have you tried using one?  If you have, can you try using an installed copy of Dapper?

[You can probably guess that I am clutching at straws, in other words, I don't know.  But I am always curious....]

---

### Post by pwilbert on 2006-08-09
The drive is fat16. I tried all possibilities (slave, cable select, master). I tried to connect it in my SATA controler and in my IDE controler. Only when connected in SATA contrtoler is that BIOS shows the nodel information. When connected to IDE controler no BIOS info is showed. I am using a live disk. Probably the disk has crushed.

---

