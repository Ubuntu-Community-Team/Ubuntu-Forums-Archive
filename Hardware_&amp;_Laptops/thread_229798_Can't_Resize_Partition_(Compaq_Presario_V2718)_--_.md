---
title: "Can't Resize Partition (Compaq Presario V2718) -- SOLVED"
date: 2006-08-04
forum: Hardware &amp; Laptops
---

### Post by malacandra on 2006-08-04
Tried installing Ubuntu 6.06 on a brand new Compaq Presario V2718 today and was told when trying to resize the partition that it failed to do so.

Looked around and tried the Ubunto "alternate" disk install (it's just the text mode, non graphical) and also tried using the GParted LiveCD. Nothing worked. 

In GParted, I simply couldn't even drag the partition to resize it.

So, here's what I did based on several posts and some digging.

Boot Windows. (Which means configuring it for first time use).

Open a DOS prompt and type: **chkdsk /f**

It may or may not work. Mine said it had to wait until a restart. Go ahead and restart. The chkdsk performs. Reboot into the Ubuntu CD or installer and it will work fine. 

For whatever reason, it seems the partitioner won't do anything until the ntfs partition has been checked, even on a brand new machine!

(And, fwiw, this is my daughters laptop and she elected to have Windows completely removed!)

Hope this helps the next person who has a similar problem.

---

