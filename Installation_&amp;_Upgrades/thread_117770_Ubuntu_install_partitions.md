---
title: "Ubuntu install partitions"
date: 2006-01-15
forum: Installation &amp; Upgrades
---

### Post by isandir on 2006-01-15
Hi guys, this isn't so much a problem with my install but i am curious about the partitioning of the install.  I told ubuntu to partition ubuntu for a multi user computer and its up and running fine, but when i was looking at the partitions ubuntu wanted to make it confused me.  

I saw one primary partition set to /   and then about 5 other partitions for /tmp /usr /home  and what not.  What i dont understand is that these were all logical partitions.  What confuses me is that i saw no extended partition.  It's my understanding that you need an extended partition to define the logical partitions.  Does the install partition tool just not show this partition or am i confused about something.  Thanks for any info you can give me.

-Isandir

---

### Post by Herman on 2006-01-15
Hello there, isander, it seems to me that the Ubuntu installer's partitioner always makes the extended partition automatically, but just doesn't bother mentioning it in the partitions list it gives. Your extended partition will be there alright.
If you want to see it, try out the latest GParted live CD, there's a new stable version that has just come out, it's great! Try it! :D (Herman)
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by isandir on 2006-01-15
I guess I was all worried over nothing, although it would be nice to see it in the installer.  I figured it had to be in there since all my logical volumes did work! Thanks for the quick reply!

-Isandir

---

