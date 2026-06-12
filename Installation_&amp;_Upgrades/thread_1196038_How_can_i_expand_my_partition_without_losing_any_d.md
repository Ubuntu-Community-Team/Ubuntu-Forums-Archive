---
title: "How can i expand my partition without losing any data?"
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by stimpak on 2009-06-24
Hi imba  ubuntu community! here's my question:

I have a 1.5TB hdd witch i sliced it like this : partition.A = 1.2TBs, partition.B = 150GBs . Partition.A is my /home mount. :D

Now i want to ask if there's anyway to **expand** partition.a over partition.b **without losing any data** from A. So effectively the whole hdd to be only one partition, which it will be my /home

Is there any way to accomplish that ( e.g. with a live cd)???:confused:

---

### Post by PureLoneWolf on 2009-06-24
Hi there

I would copy over any data from partition b to partition a - Then boot up from the live CD - Run the partition editor - Delete partition b and then resize partition a.

I went through a similar process yesterday and it worked without issue.

Hope that helps

---

### Post by presence1960 on 2009-06-24
**_back up always, which you should be doing on a regular basis anyway_**. There are no guarantees during any partitioning operation. Anything can happen at any moment! Although the partitioning process in Partition Editor (gparted)and the gparted Live CD works almost flawlessly most of the time don't take a chance with your data. Don't be the one on here playing the world's smallest violin singing the tune "I lost my data"

---

### Post by stimpak on 2009-06-24
> **presence1960 said:**
> **_back up always, which you should be doing on a regular basis anyway_**. There are no guarantees during any partitioning operation. Anything can happen at any moment! Although the partitioning process in Partition Editor (gparted)and the gparted Live CD works almost flawlessly most of the time don't take a chance with your data. Don't be the one on here playing the world's smallest violin singing the tune "I lost my data"

I know, and if it was possible i would, but its hard to almost impossible to back up 600GB of data. Its not as simple anymore as writing them on a dvd or a blu-ray disk. Thankfully i had the sense of mounting the /(root) to another disk whatsoever

---

### Post by presence1960 on 2009-06-24
> **stimpak said:**
> I know, and if it was possible i would, but its hard to almost impossible to back up 600GB of data. Its not as simple anymore as writing them on a dvd or a blu-ray disk. Thankfully i had the sense of mounting the /(root) to another disk whatsoever

I always make sure I have a back up medium at least as large as my data. I use rsync every weekend to do an incremental back up. I learned the hard way a long time ago when a hard disk died. I lost all my data. That was the only hard disk that ever died on me and it was the only non-Seagate HDD I have ever used.

Well at least you didn't lose your data, I know that would be painful.

---

