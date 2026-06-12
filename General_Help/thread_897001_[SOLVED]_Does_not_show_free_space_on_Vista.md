---
title: "[SOLVED] Does not show free space on Vista"
date: 2008-08-21
forum: General Help
---

### Post by sharat87 on 2008-08-21
Hello, I am not sure if this is the right category for posting my problem. I am sorry if that's the case. :)

I have Hardy installed on my Vista as a windows application as I did not have time to make partitions and then install it on my new laptop. I have two partitions shown in vista... 72GB and 1.5GB.

The problem is that ubuntu says there is no space left on its root partition... only 20MB. But when I check the two partitions in Vista, the free space left in them is 30GB and 1.15GB respectively. But then why isn't ubuntu using this space?

Please help as soon as possible as I am not able to do anything on my ubuntu. Any help appreciated.

Thank you,
sharat87

---

### Post by WRDN on 2008-08-21
What are the contents of the 2 partitions you are viewing in Vista? If you are using a [modern] laptop, i'm guessing the 2 partitions are the NTFS partition containing Vista, and the recovery partition. To view the Ubuntu partition in Vista, you must install the [FS-Driver]("http://www.fs-driver.org/").

---

### Post by sharat87 on 2008-08-21
The bigger partition is the Vista's system directory and the smaller one, my guess is that it contains the windows boot-loader... i never touched it. As for the recovery partition, i removed it before installing ubuntu.

I just discovered another thing. The free space is 19MB when I check in the root directory and it shows 23GB (=free space left in my C: drive) when I check it in the /host directory. For information, I just learnt that the /host directory contains the contents of my C: drive.

I'm totally puzzled...

Thank you
sharat87

---

### Post by sharat87 on 2008-11-28
I found the answer myself anyway... I feel so stupid!!

I am telling hoping it might help someone else... O:)
the C: drive is mounted at /host and there is where all the free space is! :)

---

