---
title: "mdadm RAID-6 weird performance. Read speeds drop dramatically at 75%"
date: 2010-06-25
forum: Hardware
---

### Post by xlevus on 2010-06-25
So I recently put together a software/mdadm RAID-6 array with 6x2TB EARS drives (4k Sectors) and benchmarked it with palimpest.

[img]http://imgur.com/BEX05.png[/img]

Does this look right? The speeds are great, but the way it drops off dramatically at the 75% mark as opposed to smoothly curves down is a little unnerving.

I /think/ I got the partitions aligned properly I followed [this guide](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html#tools), gparted says the first sector on all the partitions is at 2048. Is there anything else I could have done wrong or a reason for this happening?

More benchmarks seem to indicate that it's a consistent problem, but at least writes are steady :D: [one](http://dl.dropbox.com/u/110192/Misc%20Images/mdbench/Screenshot-0%20%288.0%20TB%20RAID-6%20Array%29%20%E2%80%93%20Benchmark.png) [two](http://dl.dropbox.com/u/110192/Misc%20Images/mdbench/Screenshot-0%20%288.0%20TB%20RAID-6%20Array%29%20%E2%80%93%20Benchmark-1.png) [three](http://dl.dropbox.com/u/110192/Misc%20Images/mdbench/Screenshot-0%20%288.0%20TB%20RAID-6%20Array%29%20%E2%80%93%20Benchmark-2.png) [four](http://dl.dropbox.com/u/110192/Misc%20Images/mdbench/Screenshot-0%20%288.0%20TB%20RAID-6%20Array%29%20%E2%80%93%20Benchmark-3.png)

[edit] Just to note, CPU and memory were hardly touched when doing these benchmarks.

---

### Post by polhallen on 2011-06-08
dd if=/dev/zero of=/share/raid6/5Gb bs=1024 count=5000000
5000000+0 records in
5000000+0 records out
5120000000 bytes (5.1 GB) copied, 44.5956 s, 115 MB/s



Pol

---

