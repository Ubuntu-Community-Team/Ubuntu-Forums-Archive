---
title: "Ideal Partitioning?"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by the.scarecrow on 2009-02-06
I'm thinking about how I can partition my laptop hard drive to get the best overall functionality into the future taking into consideration that:

1) Hate it, maybe but I can't live without Windows XP.
2) Need it, I can't do without Ubuntu LTS for its security and stability.
3) Love it, Ubuntu's latest release to play with all those fantastic new options.

So this is my plan for the 160GB hard drive:

Partition 1 = Windows XP NTFS 50GB
So this I can use for all those annoying things that I can't do in Ubuntu like my CanoScan LiDE 70, Reflex XTR Flight Sim etc.

Partition 2 = Ubuntu LTS 8.04 SW3 50GB including /home2

Partition 3 = Ubuntu Latest Version currently 8.10 SW3 50GB including /home3

Partition 4 = Swap used by both Ubuntu Installations 2GB

The way I plan to use the two Ubuntu versions is to alternate between the two installations. Say Partition 2 is completely stable I would use it for all my serious stuff while I play around getting Partition 3 to work properly. An advantage is that I can easily copy config files from the old install /home2 to the new /home3 to get my Apps setup the way I want them.

Eventually when I am happy with the Partition 3 version I will use it to do everything and copy all my data into this /home3 folder. Then when a new version of Ubuntu is released I do a fresh install into the partition that I'm not currently using e.g. Partition 2.

I think this would work very well but what do you think?

---

### Post by the.scarecrow on 2009-02-06
Bump

---

### Post by howefield on 2009-02-06
That would work fine, only thing I'd change is to make the partitions smaller and add another called /Data to keep all files for sharing between the 3 systems and easier backups.

---

### Post by the.scarecrow on 2009-02-06
> **howefield said:**
> That would work fine, only thing I'd change is to make the partitions smaller and add another called /Data to keep all files for sharing between the 3 systems and easier backups.

That's a good idea but I also have a 1TB external hard drive to keep backups and files that I don't need to access often. 

I tend to think the more partitions I have, the less efficient the disk space allocation is. E.g. I may be running low in space on the /Data partition but still have plenty of space in the two Ubuntu partitions. The Ubuntu partitions need to be big enough to contain many applications because I enjoy experimenting with them.

Still, I need to think about it further.

---

### Post by the.scarecrow on 2009-02-11
bump..

---

### Post by level7 on 2009-02-11
Your plan looks ok to me. You might want to consider installing LVM as well. Then you can resize your partitions (make 'em smaller and bigger).

---

### Post by the.scarecrow on 2009-02-11
> **level7 said:**
> Your plan looks ok to me. You might want to consider installing LVM as well. Then you can resize your partitions (make 'em smaller and bigger).

Well that sounds interesting. I never heard of LVM before so I will research it a bit to see if it would be a good plan for me.

Thanks for the tip.

---

