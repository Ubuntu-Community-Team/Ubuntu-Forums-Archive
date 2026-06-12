---
title: "[SOLVED] Used parts of unused partition ??"
date: 2008-11-25
forum: General Help
---

### Post by thelugnut on 2008-11-25
I have a partition on my hard disk,formatted with ext3, that I use for various things like looking at a new distribution and such.

At this time it is suppose to be "empty".
But it shows the following information:
Partition total space = 46.87 GB
Unused = 45.96 GB
Used = 933.14 MB.

What is this, almost 1 GB of data (?), suppose to be, and why is it still there, even though I format the partition?

:confused:

---

### Post by kpkeerthi on 2008-11-25
After you format, a portion of the disk space will be used to keep filesystem metadata, journal information etc.

---

### Post by thelugnut on 2008-11-25
Thanks for the reply, kpkeerthi.

I understand what you are saying, but nearly one gigabyte seems like an awful lot of space to me. Don't you agree, or is this normal?

Does a program exist that can wipe that partition, and only that partition?
Something similar to Secure Delete? I know I have a lot of space here, but it aggravates me to have a gigsbyte to store stuff used for whatever.

---

### Post by Junkieman on 2008-11-25
hi, it seems like ext3 has a 5-8% overhead for journaling, and about 5% is also [kept for root use.]("http://ubuntuforums.org/showthread.php?t=215177") yours does seem to take a bit extra... i wouldnt be too worried about it though.

the bigger the partition the bigger the overhead, its a ratio. i use ext2 on my storage drive, or you can [use reiserfs]("http://mybroadband.co.za/vb/showthread.php?t=34219") if you really want that extra space :)

---

### Post by Bucky Ball on 2008-11-25
Normal. Next time you buy a brand new hard drive, format it and check the difference.

---

### Post by thelugnut on 2008-11-25
Okie dokie guys..I have plenty of space, so it isn't a problem, but I still think that's excessive.:(

Thank you all for the replies.
:guitar:

---

