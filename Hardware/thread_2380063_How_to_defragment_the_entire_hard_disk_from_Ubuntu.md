---
title: "How to defragment the entire hard disk from Ubuntu"
date: 2017-12-12
forum: Hardware
---

### Post by rishirich on 2017-12-12
Hello there,
I have been planning to clean my laptop's HDD and reinstall Windows 10 and Ubuntu 14.04. Before doing so, i would like to format my entire harddisk, which i would be doing with the help of GParted Partition Master on a live ubuntu OS. Once the formatting is done, through the same live ubuntu OS, i would like to defrag my entire harddisk so that i can proceed to instaaling windows 10 and Ubuntu (dual boot).
I would like to know if there is any defragmenter software available for ubuntu. If YES, i would request you to name some best.
Thank you!

---

### Post by Yellow Pasque on 2017-12-12
If you are formatting partitions before/when you install the OS, you do not need to defrag.
In general, you use Windows to defrag your NTFS partition(s). ext4 is much better than NTFS in terms of not creating fragementation in the first place, but it does have a tool: [http://manpages.ubuntu.com/manpages/xenial/man8/e4defrag.8.html](http://manpages.ubuntu.com/manpages/xenial/man8/e4defrag.8.html)

---

