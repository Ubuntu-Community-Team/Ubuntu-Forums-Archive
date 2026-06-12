---
title: "Automatically format and partitioning"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by jason.chia on 2009-11-11
Hi guys / gals,

Was wondering if anyone knows how or what to use to format and partition a HDD automatically.

I have usually just use the live CD but that installs Ubuntu as well.

I have tried gparted but I have to set the partition myself (which I am trying to avoid).

Is there a software / program that I can use to get the HDD ready with partitions (automatically just like the live CD does) without having to install Ubuntu.

I'm trying to clone Ubuntu machine with a standard build basically and I know with partimage you could put into any machine as long as the HDD is smaller than the image.

Or if you know how to build a build server or where to find a guide for it, your help is very much appreciated.

Thanks in advance.

---

### Post by presence1960 on 2009-11-11
if you use the Live CD and choose "try ubuntu without any changes" when the desktop loads open a terminal and run ```
gksu gparted
```
That will bring up gparted. You can partition your disk(s), exit the Live CD without installing Ubuntu.

There are gparted Live CD, partedmagic and other free partitioning utilies that you can use without installing any OS.

P.S. If the HDD is smaller than the image, how is it going to fit on the HDD?

---

### Post by jason.chia on 2009-11-11
Hi presence1960,

Sorry my mistake there.
It should be the other way round. The image smaller than the HDD size.

With gparted, I have to assign the size of each partition myself don't I? That is what I'm trying to avoid. Any ideas if that can be done automatically?

---

### Post by presence1960 on 2009-11-11
> **jason.chia said:**
> Hi presence1960,

Sorry my mistake there.
It should be the other way round. The image smaller than the HDD size.

With gparted, I have to assign the size of each partition myself don't I? That is what I'm trying to avoid. Any ideas if that can be done automatically?
Now how in the world is the partitioning utility to know how much to assign to each partition without input from you? if you don't want to do the partitioning then you are probably out of your league and should get someone else to do it for you. Not trying to be mean just honest.

---

### Post by efflandt on 2009-11-12
No program is going to know what size you want partitions or how many unless it is for something specific or creating a partition to use all unpartitioned space.  You could simply make the entire disk one partition, and after the image is installed, shrink that partition down with gparted if you want to create more partitions.  Or if you know what size the system was for the disk image, you could make a partition about that size and leave the rest unpartitioned until you figure out what you want to do.

If just want to run gparted, there is an iso available for bootable gparted-live CD.

---

### Post by jason.chia on 2009-11-12
Sometimes being mean is good but I understand you point. :)

However, if you were to install the Ubuntu from the Live-CD it ask if you would like to use Guided or the Whole partition or manually set the partition no?

That is what I'm trying to get. Have whatever program it is to automatically set whatever it deem suitable with the entire HDD just like the Live-CD. What I do not need is for it to install Ubuntu yet as I will be using partimage (or whichever is better) to put Ubuntu on.

Hope I am clear, I did not get enough sleep so there might be some mistake in what I am typing. My apologies.

---

