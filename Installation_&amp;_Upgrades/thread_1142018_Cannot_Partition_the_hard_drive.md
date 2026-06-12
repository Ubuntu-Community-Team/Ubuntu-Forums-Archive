---
title: "Cannot Partition the hard drive"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by hellocatfood on 2009-04-28
I ordered a Hardy CD from Ubuntu which I'm using to try and do a dual boot on my laptop, which is an Asus F5SL. Using the built in partitioner I try and give Ubuntu 80GB and then when I press partition it stays stuck on 0%. The computer doesn't freeze as I can still move around the windows and click on things, but even after an hour it still stays on 0%. 

I've also tried partitioning it using Parted Magic to no avail.

A friend has suggested that I use Vista's built in partition tool but I'm wary of using it. Can anyone offer any advice?

---

### Post by upchucky on 2009-04-28
cant use vista to set up ubuntu partition, a better option is to download the standalone live cd partitioners, partedit and gparted.

I have had to use one or the other when partitioning failed.

since u have windows on the drive make sure u run a defrag on it a couple of times, this is because windows tends to write stuff willy nilly allover the drive, the less fragmented it is the better. if it is a large drive, doing partition management can take a very long time.

make sure to only do one partition task at a time, the partitioner can get confused if trying to do multiple operations at a time, such as shrink, grow, and move all in one step. this could be a disaster.

---

### Post by Mark Phelps on 2009-04-28
> **hellocatfood said:**
> A friend has suggested that I use Vista's built in partition tool but I'm wary of using it. Can anyone offer any advice?
Yeah -- unless you want to risk trashing Vista, you MUST use Vista's builtin Disk Management utility to shrink the Vista partition.  Using Gparted runs the risk of corrupting the Vista OS partition, which can be fixed by booting into a Vista DVD and running startup repair.  But if you don't have such a DVD, then you run the risk of leaving Vista in an unbootable state.

---

