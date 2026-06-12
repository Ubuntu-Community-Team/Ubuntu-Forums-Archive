---
title: "ext3 &gt;2TB unusable"
date: 2009-09-28
forum: Hardware
---

### Post by Tha Ra on 2009-09-28
Hello,
I'm using Ubuntu 9.04 64bit and I've got an +/- 1800GB (2 TB) ext3 data-partition on a RAID5 set. It's almost filled with data.
Using GParted I extended the partition matching +/- 2750GB (3 TB)
But after that GParted says that the partition is only +/- 746GB, and the remaining space (exactly 2 TiB) on the array is labelled as free space.
The file browser claima that the partition is +/- 2750GB with files with a total of +/- 1800GB on it.
When I look at the partitions' properties using the file explorer it says There are only 628GB of files. With the note that some content is unreadable.
I ran e2fsck, but I only get the message that the super block is unreadable.
Is there any way to make my partition usable again?

p.s. I'm sorry for my bad english, I hope it's clear

Thanks,

Tha Ra

---

