---
title: "Gparted partitions are gone"
date: 2008-11-25
forum: General Help
---

### Post by High Chief on 2008-11-25
Ok so in gparted all of my partitions are gone. My entire hard drive is listed as unallocated. How do I fix this? I am running 64bit Intrepid if that means anything.

---

### Post by mikewhatever on 2008-11-25
What are you trying to do with GParted? 

sudo fdisk -l

---

### Post by slimjim8094 on 2008-11-25
Running gparted or any partitioning software from the working drive (your install drive) will have unexpected results. Especially if you're trying to change anything.

---

### Post by bodhi.zazen on 2008-11-25
Boot a live CD and run testdisk

Test disk is in the repos, but here is documentation.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by High Chief on 2008-11-25
I shrunk one partition to make a new one for a mandrake install. I screwed up the Mandrake installation so now I am trying to reformat the new partition.

sudo fdisk -l lists everything sda1 sda2 etc, gparted still only shows sda unallocated.

Edit let me try a live cd.

Edit #2 ok i'm set thanks for the help

---

