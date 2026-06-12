---
title: "Root trash always empty. Even when it shouldn't be."
date: 2008-07-19
forum: General Help
---

### Post by nick62 on 2008-07-19
Hi,

I was trying to work out where all my disk space has gone, so went to investigate the Root user's trash.

It's empty. Always. If I use ```
gksudo nautilus /root/.Trash/
``` I see the trash is empty, then if i navigate to elsewhere in that nautilus window and delete a file, then head back to trash it's empty.

When not using the root account things behave as they should (ie going into that user's trash).
 
According to QTparted my partition has 456.34GB used, but if i look at the size of the files that are visible as root they only come to 371.1GB. How do you lose 80ish GB?

Any help would be most welcome.

---

### Post by nick62 on 2008-07-19
well i've (almost) found the root of all my problems (yes that is a bad pun) 

using ```
df -h
```
showed that my disk was rather full as i suspected.
```

Filesystem Size  Used Avail Use% Mounted on
/dev/hdb1  459G  434G  2.2G 100% /home/disk2
```
 and then using 
```
du -h /home/disk2
```
i found this folder
```
du: `/home/disk2/.Trash-root': Permission denied
```
which when opened contained 60GB worth of files.

using df-h again
now i have a 459G partition, that's 372G full with 64G feee.

372+64 != 459      

where is the other 23GB?

---

### Post by mcduck on 2008-07-19
By default, 5% of disk space on Ext2/Ext3 partitions is reserved for root user only.

For a 459GB partition that would be 22,95GB. :)

The idea behind this is to make sure that normal users will never be able to fill the disk so full that the system wouldn't be able to boot correctly any more. If the partition is not your root, but someadditional storage partition instead, you could safely change this root-reserved space to smaller amount or to 0. The setting can be configured with the "tune2fs" command. see "man tune2fs" for more detailed instructions.

---

### Post by nick62 on 2008-07-19
thanks for the speedy reply.

ah the intricacies of linux. I don't think I would of ever been able to find that out on my own.

do you know if there's a way of stopping deleted files on that partition going into **/home/disk2/.Trash-<user>** and instead just going into one trash that only someone with root privilidges could empty?

---

### Post by mcduck on 2008-07-20
> **nick62 said:**
> 
do you know if there's a way of stopping deleted files on that partition going into **/home/disk2/.Trash-<user>** and instead just going into one trash that only someone with root privilidges could empty?
Sorry, I don't think that's possible. Or at least not very easy to dp. The problem is that for a normal user to be able to move files into a certain directory (trash, in this case) he'd need to have write access there. And if he has write access to that directory, he is automatically also able to remove the files from there.. So there's no easy way to create a system where user woul be able to add files into a certain directory while at the same time be unable to remove them form that directory again..

---

