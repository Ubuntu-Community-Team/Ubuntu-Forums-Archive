---
title: "Cloning HDD with dual boot"
date: 2009-05-05
forum: Hardware
---

### Post by Crowder on 2009-05-05
I'm thinking about buying a Seagate Momentus 320GB 7200 rpm drive for my laptop. 

I'm wondering if anyone know a good method/app for cloning the hard drive (with my dual boot xp).

any help would be greatly appreciated.

---

### Post by logos34 on 2009-05-05
[Clonezilla]("http://clonezilla.org/") seems to be the most popular way these days.  

Either that or dd command (which is easier, but it copies EVERYTHING, even unused sectors.  So it's slower)

---

### Post by Crowder on 2009-05-06
so if i used clonezilla i could just boot up with either OS and all of my apps intact? no data lost at all? would GRUB be intact or should i back it up?

thanks for the link. i wasnt sure what was the best cloning app to use.

---

### Post by logos34 on 2009-05-06
if you clone the *entire* drive, no need to separately backup grub (on the mbr).

If you do it a partition at a time, then either backup the mbr or install grub on the target drive using the live cd (or while booted into another linux installation)

---

### Post by Crowder on 2009-05-07
that makes sense

thanks a lot

---

### Post by dalexnagy on 2009-09-05
Be sure to define the partitions on your new drive in the same order and with the same types as your source drive so Clonezilla works successfully.  The new partitions also have to be at least the same size or larger.

Good luck!

---

