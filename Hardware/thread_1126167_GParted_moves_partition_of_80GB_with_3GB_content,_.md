---
title: "GParted moves partition of 80GB with 3GB content, by moving all 80GB"
date: 2009-04-15
forum: Hardware
---

### Post by tg1w on 2009-04-15
Hello

I had to resize and move (to the right) a partition, in order to make space for another. GParted is very useful, but... also very inefficient at this. The partition is 80GB long and contains 3GB of data. GParted is "moving" all 80GB, meaning also 77GB of empty blocks.

Anyone knows how to perform these kind of operations more easily? Better tools, improvements to GParted?

Thank you very much

---

### Post by night_fox on 2009-04-15
Could you shrink it to 3GB, move it and then expand it?

---

### Post by tg1w on 2009-04-15
> **night_fox said:**
> Could you shrink it to 3GB, move it and then expand it?

Too late now. I thought it would have been an easy process.

What is interesting, is that after doing something with the 80GB, it copied around 10 blocks of 16MB and than it started copying again the 80GB. 

Totally unoptimised operation that got cancelled now.


Thank you. I will try your alternative

---

### Post by Bucky Ball on 2009-04-15
Kinda what I was thinking. You could also back up the data to another device (cd, usb dongle, external hard drive) and partition the way you want.

Do you have a Ubuntu install already on another partition? Got a spare 3Gb in there? /home perhaps?

---

### Post by tg1w on 2009-04-15
> **Bucky Ball said:**
> Kinda what I was thinking. You could also back up the data to another device (cd, usb dongle, external hard drive) and partition the way you want.

Do you have a Ubuntu install already on another partition? Got a spare 3Gb in there? /home perhaps?

The primary Ubuntu partition is also the first on the drive. When I partitioned the drive, I didn't leave it enough "slack", so now that I have to enlarge it, I have to move all partitions before it, to the right.

So, even if I would put the "3GB" (I checked again and they are 7) on a pendrive, I would still need to shift the other partitions.


Thank you very much for the advice, and given a different situation, I would have enacted it.

---

### Post by tg1w on 2009-04-15
Is anyone using a better partitioning tool?

---

### Post by mlentink on 2009-04-15
Actually I think you've got the terminology wrong. GParted is very efficient in repartioning and moving partitions. Off hand, I wouldn't know of a better tool with the same ease of use.
But moving partitions around is not exactly the same as moving filesystems and data around. If it is the latter you want, copy the data with Clonezilla, repartition, and write the data back.

---

### Post by Bucky Ball on 2009-04-15
Exactly. GParted is the one to use. mlentink +1

---

### Post by tg1w on 2009-04-15
> **mlentink said:**
> Actually I think you've got the terminology wrong. GParted is very efficient in repartioning and moving partitions. Off hand, I wouldn't know of a better tool with the same ease of use.
But moving partitions around is not exactly the same as moving filesystems and data around. If it is the latter you want, copy the data with Clonezilla, repartition, and write the data back.

Thank you mlentink

The situation was this: I have 7 partitions on my drive, out of which, the first is a bootable Ubuntu (/). The last partition was a 87GB, but due to diminishing disk space on the Ubuntu one, the last partition had to be shrinked and then all partitions in between the two, moved to the right. This finally will make space for the first partition. 

I haven't used Clonezilla, and probably an improvement could be obtained. What I was saying was that GParted is indeed terribly inefficient at moving partitions, in the way it manages their data. If the partition had only 7GB of data, why would it copy all 87GB, and twice?

It is very good for most of the operation and very-very useful. In this case though, Partition Magic might be better.


Thank you all

---

### Post by Windsurfer619 on 2009-04-15
I like this behavior in gparted as I had an encrypted partition that I needed to copy. Gparted couldn't read the contents (it said it was empty) but it copied everything truthfully, bit for bit.

---

### Post by tg1w on 2009-04-15
> **Windsurfer619 said:**
> I like this behavior in gparted as I had an encrypted partition that I needed to copy. Gparted couldn't read the contents (it said it was empty) but it copied everything truthfully, bit for bit.

Yeap, this sounds as a good scenario. Maybe if they would allow you to chose which behaviour to run, it would be perfect. 

Thank you all

---

