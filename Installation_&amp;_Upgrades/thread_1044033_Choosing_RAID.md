---
title: "Choosing RAID"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by masa77 on 2009-01-19
Hi,

I'm doing a fresh install with ubuntu 8.10 my main computer. I currently have two 250GB sataII drives and I have purchased two 640GB sataII drives, the latter are faster than the smaller. Can anyone give me a suggestion how I would set this up so that I have data redundancy and best possible performance. I was first thinking of putting 2x250GB in RAID1 and 2x640GB in RAID1 separately. However, would it work and would be a good idea putting all four drives in RAID10? RAID5? I'm going to use software RAID, I'm asking this because the disks are of different sizes.

Thanks/Mattias

---

### Post by Pumalite on 2009-01-19
[http://www.pcworld.com/article/132877/how_to_set_up_raid_on_your_pc.html](http://www.pcworld.com/article/132877/how_to_set_up_raid_on_your_pc.html)

---

### Post by stefangr1 on 2009-01-19
RAID 5 and RAID 10 is not suitable for you, since your disks differ in size.

2 different RAID 1 arrays would work just fine.

---

### Post by masa77 on 2009-01-19
Hi,

thanks for your reply. What I'm really wondering is if it's recommended to mix different harddrives in e.g. raid 1+0. That is, if I mirrored the two 250GB harddrives and then mirrored the two 640GB drives, would be of any benefit striping them performance-wise than keeping them separate.

/Mattias

---

### Post by masa77 on 2009-01-19
@stefangr1: Can you explain why I shouldn't use RAID10? I.e. why is it not a good idea if sizes differ.

/Mattias

---

### Post by stefangr1 on 2009-01-19
You could do it by making a 250GB and a 390GB partition on each 640GB disk, and them make a raid 1+0 array of the 4 250GB disks and partitions, and a raid 1 array from the 2 390GB partitions. This would give you better performance when only the raid 1+0 array is used, but performance is very much harmed when both arrays are used simultaneously.

I think a setup like that would not increase the security risk higher then just a regular 1+0 array.

---

### Post by masa77 on 2009-01-19
Ok, well that sounds like an overkill, I will go for two RAID1. Thank you.

---

