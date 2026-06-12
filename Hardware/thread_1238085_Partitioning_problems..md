---
title: "Partitioning problems."
date: 2009-08-12
forum: Hardware
---

### Post by Johndo1 on 2009-08-12
I had ubuntu on an old desktop computer but I recently duel booted it with windows vista. I am on a compaq presario c700us. Everything works fine but it won't allow me to increase the size of the filesystem witch is preventing me from installing updates. The Filesystem partition is very small and only has 114 megabytes left on it. I have gparted and it won't allow me to partition this section. I suspect it is because it is currently running ubuntu on it. :( Any help would be greatly appriciated.

---

### Post by Tclarkie on 2009-08-12
if you boot from cd and install gparted (without mounting anything), it should work

---

### Post by Johndo1 on 2009-08-12
I was able to resize my NTFS portion of the drive but the Ubuntu dev/sda section seems to have a maximum size limit. I was looking around and I've heard a lot of people create another partition and somehow link it with their filesystem or something. Thank you for replying. I am now able to partition the ubuntu section but the problem is making the max size increase. Now I just have a blank portion on the hard drive... Any help would be appreciated.

---

### Post by drs305 on 2009-08-12
First, is this a normal Ubuntu install or a Wubi installation within Windows?

I have a few links that may be of interest. "Expand /" tells you how to expand your / partition. Although the reason for writing the guide doesn't apply to your situation, how to do it does. 

Also, if you can't expand the partition for some reason, "DiskSpace" will show you how to find things taking up space that you may need for other other things. You might also make sure you empty the trash (your's and root's): "Trash".

The links are in my signature line.

---

### Post by Johndo1 on 2009-08-12
I feel close to figuring it out but I followed a guide and it seems it went wrong somewere. I increased the size of the drive but an error occured during the process. When I look at my filesystem it sais it has the same amount of memery as when I started. Also when I look at Gparted the 2.5GiB drive that was nearly full and I was trying to increase is now 33GiB and is full. How did it fill itself up? Anyways please help.

---

### Post by Johndo1 on 2009-08-12
I'm thinking about reinstalling ubuntu and just creating it with a partition vs. the duel boot. Any thoughts on this? Also if there is not a screen to select witch OS to start at the computers startup how do you start ubuntu?

---

### Post by Johndo1 on 2009-08-12
> **drs305 said:**
> First, is this a normal Ubuntu install or a Wubi installation within Windows?

It's normal

---

