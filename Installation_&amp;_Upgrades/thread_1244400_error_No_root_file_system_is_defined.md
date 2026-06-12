---
title: "error: No root file system is defined"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by liberty821 on 2009-08-19
Installing Ubuntu 9.04 on a brand new 250GB laptop drive, and there's a problem with the partitioning.

I made three partitions: 75G, 75G, 100G (all fat32)

when I click 'forward' it says:
 "No root file system is defined
Please correct this from the partitioning menu"

a bit puzzling since I chose fat32 for the file system...

How do I move on to format the partitions?

Appreciate your help, thanks.

---

### Post by SlugSlug on 2009-08-19
I would change all your partitions
first one 
2GB swap
then 
/ 10GB ext4
the the rest on 
/home ext4

---

### Post by liberty821 on 2009-08-19
But I plan on installing windows on here too... can I still do fat32 partition?

---

### Post by liberty821 on 2009-08-19
So I did 
2GB swap
20GB / ext4
120GB /home ext4
rest on /windows fat32 

works now, thanks

---

