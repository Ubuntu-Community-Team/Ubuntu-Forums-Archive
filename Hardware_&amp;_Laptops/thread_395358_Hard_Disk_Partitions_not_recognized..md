---
title: "Hard Disk Partitions not recognized."
date: 2007-03-28
forum: Hardware &amp; Laptops
---

### Post by elcacique on 2007-03-28
Firstly, I'm new at this Linux game, so you'll understand if I appear totally clueless, :confused: please forgive me. 
 
I'll do my best to describe the problem:
I'm running Dapper Drake 6.06, with two hard drives installed. The second one was added after getting the basic installation up and running with the first drive.

This second hard drive was used for basic storage, accessible from other PCs on a Windows LAN. 

All of a sudden, things went from bad to worse; Ubuntu wouldn't boot (something about the Gnome desktop being inacessible), and other seemingly endless problems.

To cut a long story short, I thought I had done something wrong, but my nightmare turned out to be caused by defective memory! I wouldn't have expected this, never having experienced it before. After much grief, I ended up running the memory checker (MemTest) on the installation CD, and voila! Memory errors galore!!  

So I re-install Ubuntu from scratch, and now have the problem of the system not recognizing the partitions on the second hard drive. I have data on it I would like to retrieve/keep, so I don't want to do anything that might jeopardize losing it.

Can anyone recommend a procedure by which I could get Ubuntu to see the hard drive as before? I honestly don't remember what formatting (NTFS, or other) was used previously. 

Any help would be much appreciated.

Thanks,
David

---

### Post by tonym on 2007-03-28
Have you tried just manually mounting the partitions.  eg

mount /dev/hdb1 /mnt
ls /mnt

Repeat this for /hdb2,/hdb3 etc and see what happens.

Regards

Tony.

---

### Post by elcacique on 2007-03-28
Hi Tony:

Thanks for the reply. When I try 
```
mount /dev/hde /mnt
```
I get the response:
```
mount: you must specify the filesystem type
```

This is where the challenge is: what is the "filesystem type"?

Regards,
David

---

