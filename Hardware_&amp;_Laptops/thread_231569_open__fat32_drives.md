---
title: "open  fat32 drives"
date: 2006-08-07
forum: Hardware &amp; Laptops
---

### Post by somi38 on 2006-08-07
what is mounted tree.
how can i mount my drives.
where these commands are written
please help me 
i use linux first time

---

### Post by GoLoGo on 2006-08-08
you can mount drives using the command in the terminal:

sudo mount <device> <mounting point>

for example:

sudo mount /dev/hb5 /media/music

drives are labeled as follows

hda
hdb
hdc ect... and usually have a number next to them... hda1 hda2, telling you the # of the partition on the partition table.

---

