---
title: "question about primary &amp; logical partitions"
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by raymondvillain on 2009-06-22
Just installed 64 bit Jaunty from the live CD.

Chose the "manual" option for partitioning the single hard drive.

Selected "new partition table" at first.  When that was done, I had the whole hard drive available as "free space".

Then I filled up the free space with several logical partitions, and all went well.  At the end everything worked as expected.

But I was expecting to have to create one primary partition and THEN create the logical partitions within it.

Does this mean that there are no primary partitions on my hard drive?  Or did partition editor automatically create a primary partition when I selected "new partition table" at the very first step?

---

### Post by Soul-Sing on 2009-06-22
A harddisk can only contain 4 primairy partitions. So make an extended partition, which can contain unlimited logical partitions.
linux can be installed on logical and primairy partitions....
Then you need a tool to partition: the gparted iso, burn it, and it runs like a live-cd!
1) make an extended primairy partition which you divide into the deisired number of logical partitions.
Logical partitions begins with the 5 number, because the first 4 are reserved for the primairy partitions.
You need 1 swap for all linux systems.
BSD systems and windows can only be installed on primairy partitions!!

---

### Post by Herman on 2009-06-22
I basically agree with leoquant.

There is a thing called a 'partition table' in your hard disk's 'Master Boot Record', which is in the first sector of your hard disk.
The partition table contains four spaces of sixteen bytes each where details of the partitions are recorded. 
This is why there can only be four 'primary' partitions, there is only enough space allowed there for four.
Only one of these primary partitions is allowed to be special, it can contain an 'extended' primary partition.
The 'extended' primary partition may contain a string of 'logical' partitions as long as they are 'contiguous', (linked in a series - not interrupted by any primary partition in between any of the logical ones).

The installer's partitioner would have automatically created the 'extended' partition when it made the first logical partition.

Ubuntu can boot and run just as well from logical partitions as it can from primary partitions. Some operating systems prefer to boot from primary partitions.

Regards, Herman :)

---

