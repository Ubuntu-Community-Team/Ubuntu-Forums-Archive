---
title: "Mounting a FAT32 partition the correct way"
date: 2005-06-05
forum: Hardware &amp; Laptops
---

### Post by henriette_holm on 2005-06-05
Hi.
What's the correct way of mounting a FAT32 partition when I have files on the partition with names containing special caracters - like æ, ø and å ?

Right now I get: "<name of file> (invalid encoding)"

-Henriette

---

### Post by Strife on 2005-06-05
I've never had any strange issues with that. I've always only had to just simply mount the partition.

However, with those types of characters, I'm not sure if you can do that or not... It may require some special kernel support or something. I've never used any characters beyond the regular alphanumeric and the occasioanly "special" character (punctuation basically).

---

### Post by rwabel on 2005-06-05
[QUOTE=henriette_holm]Hi.
What's the correct way of mounting a FAT32 partition when I have files on the partition with names containing special caracters - like æ, ø and å ?

Right now I get: "<name of file> (invalid encoding)"

-Henriette[/QUOTE]
 do u have the uft8 option added to fstab?
for example
user,rw,exec,auto,umask=000,utf8
same for cdrom!

---

