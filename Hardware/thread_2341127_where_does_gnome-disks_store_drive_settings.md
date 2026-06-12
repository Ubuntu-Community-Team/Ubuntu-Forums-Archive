---
title: "where does gnome-disks store drive settings?"
date: 2016-10-25
forum: Hardware
---

### Post by hendrikwout on 2016-10-25
Hi,

I'm using the 'gnome-disks' program to control the drive settings, particularly the disk spin-down time. It seems to work well.

I have many disks, so I was wondering how I can modify these settings more quickly from commandline. Does anyone know where the drive settings of gnome-disks are stored in a text file in ubuntu (under etc)? I already checked '/etc/hdparm.conf', but I cannot find any changes by the 'gnome-disks' program there. Anyone has a clue?

Thanks in advance!
Hendrik

---

### Post by olejon on 2017-02-27
I would also like to know this!

---

### Post by olejon on 2017-02-27
Ah, found it! They are in **/etc/udisks2**. Need sudo/admin rights to open the files.

---

