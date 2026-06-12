---
title: "Problem Partitioning"
date: 2009-07-12
forum: Installation &amp; Upgrades
---

### Post by caat91 on 2009-07-12
Hello, well this is my first post and is about how to install ubuntu on my PC, the problem that i am having right now is that on the step number 4, when it is supossed to be creating a partition, i just wait, and wait , and wait, and after liek and hour it gives me an error, the error is that there were some troubles resizing the disk, and that the operation can not be completed. I have tried using the manual partitioning, and the guided one, but nothing changes :S 

how can I solve this?

---

### Post by merlinus on 2009-07-12
Are you trying to set up a dual-boot with windows?  What version?  On one hdd?

---

### Post by caat91 on 2009-07-12
Yes, both are supposed to be on the same HDD.

 i am using windows Vista. and i am trying to install UBUNTU 8.10

---

### Post by merlinus on 2009-07-12
You need to use vista's disk management tool to resize its partition.  Defrag several times first.

Then you can install ubuntu into the freed-up space.

---

### Post by Ekeluo on 2009-07-12
You should use "shrink" on the hard disk from inside Vista's disk management tool as mentioned in the post above. Ensures that Vista will survive. Don't forget to defrag, especially if the hard disk is more than 50% full.


N.B. Backup your data!!! Backup your data!!! Backup your data!!!

---

### Post by caat91 on 2009-07-16
I did what u said, but it keeps telling me the same thing... and if i Try the manual instalation in the partition that i created, it ask were is the ROOT, and i dont have idea how to solve that either... it says that i have to select it in the Menu of the partition, but there is nothing like that, and I tried every single option, and nothing happened... :S

---

### Post by merlinus on 2009-07-16
Try right-clicking on the partition.  It should give you a dropdown menu where you can select mountpoints.

---

### Post by caat91 on 2009-07-17
and what should i select in that menu, it shows me a lot of options but i dont know which one is the right one?

---

### Post by merlinus on 2009-07-17
Use as ext3, format, mountpoint / (root).

---

