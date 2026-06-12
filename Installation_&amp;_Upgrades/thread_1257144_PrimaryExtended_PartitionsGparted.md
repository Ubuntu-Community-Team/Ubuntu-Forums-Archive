---
title: "Primary/Extended Partitions/Gparted"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by okayneil on 2009-09-03
Hey guys, 

I wanted to split my HDD into numerous parts/partitions like music docs etc but just realised when using gparted that you cant have more than 4 primary partitions. GParted then goes on to tell me to create an extended partition which can contain multiple partitions within. 

Thing is, GParted wont let me create the extended partition, the option is not availavle. 

Screenshot of how my HDD is split up...

[IMG]http://imgur.com/xaaKB.png[/IMG]

Any ideas as to what i should do?

---

### Post by presence1960 on 2009-09-03
you already have an extended partition sda2 which contains swap. So right click on sda2 and choose resize. Then when the graphic appears grab the left border of sda2 with your pointer and drag it to the left until you have the amount of space you want to add to sda2. Click apply. When done you will have unallocated space within sda2 to create more logical partitions within sda2.

You can only have one extended partition per disk. But you can create as many partitions within that extended partition as space available will permit.

---

### Post by okayneil on 2009-09-03
> **presence1960 said:**
> you already have an extended partition sda2 which contains swap. So right click on sda2 and choose resize. Then when the graphic appears grab the left border of sda2 with your pointer and drag it to the left until you have the amount of space you want to add to sda2. Click apply. When done you will have unallocated space within sda2 to create more logical partitions within sda2.

You can only have one extended partition per disk. But you can create as many partitions within that extended partition as space available will permit.

Thanks for the help...i did this but windows os is not seeing these partitons? Any ideas?

---

### Post by okayneil on 2009-09-03
Will windows be able to recognize the extra partitions if they are inside the extended partition?

---

### Post by presence1960 on 2009-09-03
windows will only recognize NTFS ot FAT partitions. If one of those is inside the extended partition windows will recognize & access it.

---

### Post by okayneil on 2009-09-03
Cheers guys, work a treat :)

---

