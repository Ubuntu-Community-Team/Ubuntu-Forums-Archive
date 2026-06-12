---
title: "wrong used space after resizing partition"
date: 2008-11-14
forum: General Help
---

### Post by Farhadi on 2008-11-14
At first, I had a 230GB ext3 partition with 17GB used space.
I used gparted to resize this partition to 25GB and created two other ext3 partitions in new unallocated space, one with 25GB and another 180GB.
when operation finished I saw that my first partition that had at first 17GB used space, now has about 14GB used space.
and I saw another two new partitions one with 170MB and another with 3GB used space that I expected to be empty. but when I browsed these two new partitions I saw nothing except an empty "lost+found" folder.
I rebooted the system and anything works well just like there is no any problem and it seems that nothing is lost and all of my files exists. but reports of used spaces are wrong. I used gparted, system monitor and df command. all of them report wrong used spaces.

What happened? 

What should I do to fix them?

---

### Post by Farhadi on 2008-11-14
I guess I found it.
total usable space of an empty ext3 partition is about 98.4% of total space used by that partition.
In other words, when you create a new ext3 partition, 1.6% of its space will be reserved for ext3 itself initially.
So, when I create a 180GB ext3 partition, only about 177GB of it will be available for use and remaining 3GB of it is used by ext3 at creation time.

Is there anyone who can confirm this?

---

