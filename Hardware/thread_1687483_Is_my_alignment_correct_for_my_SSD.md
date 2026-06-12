---
title: "Is my alignment correct for my SSD?"
date: 2011-02-13
forum: Hardware
---

### Post by cariyawa on 2011-02-13
I hope I am posting this in the correct place. I have a crucial C300 64GB SSD. I partitioned it in to a single partition and here is the information. I am really concerned about the alignment and I just want to know whether my alignment is right.

```

fdisk -l -u /dev/sda
Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003cd05

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   125044735    62521344   83  Linux


```

Thanks in advance!

---

### Post by cariyawa on 2011-02-16
I found the answer to my own question. Yes. it is aligned. Thanks for people who view the question.

---

### Post by Riot@ct on 2011-05-18
How you have aligned the Crucial?
Manually or have you following the normal way to install ubuntu?

---

