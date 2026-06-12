---
title: "Partitioning Hard Drive"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by illieas19 on 2009-04-29
I have tried to partition my hard drive to have both XP and Ubuntu Studio 9.04 on my HP Media Center.... its old but and a WD250 GB HD. Anyway everytime I try to partition with the "Guided Partition Resizing Current Hard Drive" and the screen keeps showing me an error that keeps me from paritioning my hard drive no matter how big I make my parition. What should I do to keep XP and resize my hard drive to allow for US to be on the HD?

P.S. How big should the partition be?

---

### Post by aquavitae on 2009-04-29
It would help if you could post the exact errror message you're getting. 

A hint though: you should defrag your windows drive before resizing.  I've know that to cause problems somtimes.  As to how large the partitions should be, I'd recommend an absolute min of 10G each for XP and Ubuntu.  Then you'll also need a swap partition of about 1G.

---

### Post by illieas19 on 2009-04-29
Okay, thanks. So now the question is that since I finally got a partition using EASEUS Partition Master 3.5. and a 1GB drive for the swap the error is reading "No root file system defined. Correct the from the partitioning menu!" then forcing me back to the partitioning menu. I have tried to define [by manually assigning the partitions] the 1 GB partition as the swap and the others as drives but apparently I don't know what to do past the partitioning part. So far the XP partition and recovery partitions are primary and the 1 GB Swap and 50 GB Partition are logical partitions. What should I do?

Also what format should the Swap and 50 GB partition be in?

---

### Post by aquavitae on 2009-04-29
Swap should be formated as swap. Your ubuntu drive can be whatever linux filesystem  you want - I prefer ext3, but you could also use reiserfs, ext2 or ext4 (if you have it available).  These are the common ones. You then need to set mount points for each partition, except the swap.  I don't remember exactly what you need to click on to do it, but when you find a text box called "Mount Point" you're in the right place. In case you don't know, the mount point is the place in the linux filesystem where that partition will be accessed, so for the ubuntu partition, it needs to be set to "/". I.e. it will mount it as the root filesystem. You don't really need to set a mount point for windows, but you can if you want. I like mounting mine at "/mnt/windows" so I always know exactly where it is, but you could just as easily leave it blank at left ubuntu manage it for you.

---

### Post by illieas19 on 2009-04-30
Thanks... that fixed that problem. Also I found out that the DVD I was using was corrupted so I burnt a new DVD of 8.04 thinking that 8.04 would lack the partitioning problem that I encountered in the 9.04, after which I could upgrade. But now the problem is that the 8.04 disc is stating that the partition could not mount the second partition (my XP partition) and repeatedly failed no matter what I did. What should I do? (Apparently Ubuntu Studio hates me :)

---

### Post by aquavitae on 2009-05-02
Its possible that windows crashed or something so that it didn't cleanly unmount the drive.  The easiest way to test this is probably to boot into windows and shut down, then try ubuntu again.  If that doesn't work you can also try the command ```
sudo ntfsfix /dev/...
``` replacing /dev/... with the appropriate device for you windows partition.  If you still can't mount it, then post the exact error message and the output of ```
sudo fdisk -l
```

---

### Post by illieas19 on 2009-05-19
Thanks. That worked.

---

### Post by rajiv_jjj on 2009-05-23
thankyou aquavitae!!!! that was really helpful

---

