---
title: "Can't resize /home partition"
date: 2014-03-20
forum: Hardware
---

### Post by LuigiMazzini on 2014-03-20
Hello,
I'm trying to add unallocated space to /home partition, using Gparted on Ubuntu 12.04. I can't resize the partition, even though I boot from LiveUSB so the partition is not mounted. How can I do it?
Here's my partition scheme (/home is on /dev/sda7):
[IMG]http://i1273.photobucket.com/albums/y416/LuigiMazzini/partitions_zpsea46efaa.jpg[/IMG]

---

### Post by Bashing-om on 2014-03-20
LuigiMazzini: Hi !

See the key emblems to the left of "extended" and "linux-swap" -> means the partition(s) is locked. 
To unlock the partition in GParted turn swap off, This will release the swap partition, and once swap is released the "extended" partition containing swap will also be released.

Then I expect you will be able to manipulate the partition.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by LuigiMazzini on 2014-03-20
Hi Bashing-om,
thanks for helping.
Releasing the partition didn't  help although it was necessary. I had tried it before. However I found  the solution: firstly, I had to resize /dev/sda3 and after that I could  resize /dev/sda7, just like I wanted. :)

---

### Post by Bashing-om on 2014-03-20
LuigiMazzini; Great !

Pleased you got it sorted out .

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

