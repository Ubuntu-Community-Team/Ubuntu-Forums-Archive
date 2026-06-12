---
title: "Best Way to Backup Data On Ubuntu?"
date: 2008-11-03
forum: Hardware
---

### Post by DocHolliday2006 on 2008-11-03
Hi. I need a better way than DVDs to back up data. 

I'd like to buy a portable hard drive with 120-300 gigs. I'm thinking about the Western Digital Passport.

I just wanted to make sure that this would work on Ubuntu out of the box? 

Are there other Ubuntu-ready external backup hard drives available?

Any advice welcome.

Thanks,

-Andrew

---

### Post by jamescox84 on 2008-11-03
Any external hard USB disk would work. Just plug it in and the icon will appear on your desktop. I'd recommend formatting it with a Unix file system though (like ext3) or you will loose permission's on your files and folders. This is a particularly a problem with FAT32, and I also believe NTFS as well. This doesn't mean the data will be lost, only the file permissions.

Partitioning with GParted:
```
sudo apt-get install gparted
```

---

### Post by ajgreeny on 2008-11-03
I think jamescox84 is right except that I seem to remember some seagate drives did present a problem as they went to a suspend mode after a while and were difficult to awake.  It may be that the problem is easily surmountable, but I'm not certain.  I have an iomega 250GB USB desktop drive, not the fastest in the world, but it does a great job.  I formatted as ext3 and use grsync to backup my home folder. Dead easy!

---

### Post by crash0 on 2008-11-03
western digital drives work perfectly with ubuntu, i have 2 terabytes of them and they all work great... my advice is to format it with fat32 for simplicity, so you can access it from a windows OS without installing additional software for ext filesystem recognition...

---

