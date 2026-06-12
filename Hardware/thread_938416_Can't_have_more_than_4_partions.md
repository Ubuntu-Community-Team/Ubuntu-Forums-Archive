---
title: "Can't have more than 4 partions?"
date: 2008-10-04
forum: Hardware
---

### Post by DivinityX on 2008-10-04
I have a Dell XPS M1530 that comes with UBUNTU. I'm trying to install windows on here as as second OS. I resized the Ubuntu Partion but it's Unallocated. It won't give me the option to format it because i can't have more than 4 primary partions. My HDD has four partions that came with it...

1)fat16       -   94.1MB
2)fat32       -   3.00GB
3)ext3        - 241.62GB    //This is where Ubuntu is runing
--Unallocated -     50GB    //Where I want windows
4)extended    -   3.38GB
--linux-swap  -   3.38GB

can someone tell me why i'm seeing these other partions, and do i need them? they don't ever seem to be mounted, i can't see them under the places menu...why are they put there? is it safe for me to delete them?

---

### Post by gpsmikey on 2008-10-04
> **DivinityX said:**
> I have a Dell XPS M1530 that comes with UBUNTU. I'm trying to install windows on here as as second OS. I resized the Ubuntu Partion but it's Unallocated. It won't give me the option to format it because i can't have more than 4 primary partions. My HDD has four partions that came with it...

1)fat16       -   94.1MB
2)fat32       -   3.00GB
3)ext3        - 241.62GB    //This is where Ubuntu is runing
--Unallocated -     50GB    //Where I want windows
4)extended    -   3.38GB
--linux-swap  -   3.38GB

can someone tell me why i'm seeing these other partions, and do i need them? they don't ever seem to be mounted, i can't see them under the places menu...why are they put there? is it safe for me to delete them?

Not sure on what they are, I would expect (based on other Dell's with windows installed) that the first one is some sort of Dell utilities/recovery type partition.  You are correct in that a normal disk can only have 4 primary partitions, HOWEVER, you can make one of them an "extended" (as #4 is) and put additional partitions inside that "extended" partition.  I would assume you can do what you want with gparted from a live CD - I am more familiar with BING from Terabyteinc for my partitioning work.  What I would do is resize the extended partition to include the "unallocated" space .... thinking ... actually, I don't think windows can boot from an extended partiton although Linux can.  I think the simplest solution would involve moving it to a second hard drive !!  put the linux ext3 and swap partitions inside an extended partition, adjust grub to point to the right partition then you would have a spare primary partition for windows.  Sigh - started out thinking this was fairly easy - hopefully someone else here with more experience has a better idea since, somehow, you need to end up with windows in a primary partition if I remember correctly (at least for XP).  Also, check out some of the articles around here on dual booting windows and Linux.

mikey

---

### Post by DivinityX on 2008-10-04
thanks for your help, i'll look into this...^_^

---

### Post by Sef on 2008-10-05
If you want to partition, the Live and Alternate both have GParted as a partitioner.   Also you can download a more recent version of [GParted]("http://gparted.sourceforge.net") from its website.

---

