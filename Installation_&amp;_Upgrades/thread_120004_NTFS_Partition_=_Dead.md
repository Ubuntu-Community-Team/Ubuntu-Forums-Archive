---
title: "NTFS Partition = Dead"
date: 2006-01-20
forum: Installation &amp; Upgrades
---

### Post by KSean on 2006-01-20
I recently tried installing Ubuntu, and it got stuck at 6% and crashed. I rebooted, and when it got to loading Windows XP, it said "Error loading operating system". I insterted my XP disk and tried to fix it, but it seems that made it worse :S. Now when I try to boot, my PC asks to insert a system disk then press enter. ATM, I'm using an Ubuntu live CD I downloaded a few weeks ago.

So is there any way to fix this?

---

### Post by Ocxic on 2006-01-20
sounds like you may have accidenly messed up partitioning the disks, linux reformats what ever disk you install it to, to ext3 format so it can use it (linux doesn't use NTFS).
you iether didn't relize this or, the partitioner you used messed up.
when it asked you to partiton th disks what did you tell it to do?

---

### Post by hillbilly on 2006-01-20
one of my friends had a same problem with his ubuntu installation. The problem was the cd was bad. 
And now since you cant load your other OS, Iam  assuming that the incomplete installation must have corrupted your mbr. I guess your best bet would be to try to get another ubuntu cd and complete the ubuntu installation. That would setup the mbr properly and you should be able to boot into both OS. 


P.S: You are not installing ubuntu on ntfs are you ? It should be installed on an ext3 partition.

---

### Post by KSean on 2006-01-20
I asked it to use the avaliable free space. I resized the NTFS partition with PartitionMagic beforehand, and it worked then :S

EDIT: hillbilly, would this 6.04 live CD I'm using help fix it?

---

### Post by dueY on 2006-01-20
Do you have your Windows CD handy?

---

