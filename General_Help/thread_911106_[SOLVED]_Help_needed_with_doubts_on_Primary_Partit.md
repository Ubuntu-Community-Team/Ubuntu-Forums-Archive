---
title: "[SOLVED] Help needed with doubts on Primary Partitions"
date: 2008-09-05
forum: General Help
---

### Post by ragflan on 2008-09-05
Hi, I'm helping my uncle install Ubuntu with Vista. I need some clarifications. There can only be 4 primary partitions on one hard disk, correct? So if I can only create 2 partitions should I go with: 

1.) Creating one for / mount point and one for /home? (not having swap) OR
2.) Creating one for / mount point and one for /swap (putting / and /home on same partition)

He already has 2 partitions used up with Windows that he cannot get rid of. And he has a lot of empty space. Is there a way he can have more than 4 primary partitions such that:

1 and 2 for Windows.
3 for / mount point
4 for /home 
5 for SWAP

He has 1 GB Ram.

---

### Post by dodle on 2008-09-05
What about using an extended partition for "/" and "/home"?  Also do you prefer not having "/" and "/home" on the same partition?

---

### Post by ragflan on 2008-09-05
I read somewhere that it's good to have your Home directory on a separate partition with a whole list of advantages. My system is partition that way.

---

### Post by Rocket2DMn on 2008-09-05
For your partitions, I would proceed like so:
-1 and 2 - keep existing partitions
-3 - your root partition
-4 - an extended partition
--5 - /home in a logical partition inside this extended partition.
Then if you ever have to create new partitions, you can resize the /home partition and place the new partition at 
--6 - new partition inside the extended partition

---

### Post by ragflan on 2008-09-05
Yup! That's what I was thinking. Root filesystem on a primary partitions and /home and SWAP on 2 logical partitions on one extended partition. Thanks for the quick responses!

---

### Post by Rocket2DMn on 2008-09-05
Ah yeah, swap, hehe.  How could I forget - definitely have a swap partition, and yes, it's fine under the extended partition.

---

### Post by ragflan on 2008-09-05
Yup Yup Yup! Thanks for the quick responses!

---

