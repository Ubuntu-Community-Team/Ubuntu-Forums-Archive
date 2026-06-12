---
title: "HOWTO: Compaq v3000 install"
date: 2006-11-26
forum: Hardware &amp; Laptops
---

### Post by danieljay on 2006-11-26
The last couple days I have been setting up my new Compaq v3000z laptop. Wanting to keep my Windows install for some other tasks(and some games), trying to use Partition Magic does not seem to function. HP/Compaq has some very interesting partitioning which includes:
1 10GB recovery partition
1 1GB partition(which I have yet to look at)

The laptop includes a Windows as the main partition, Windows XP embedded for their quickplay multimedia functions, then Windows NT for their recovery program. 

When trying to run partition magic you will get: "983 Too many errors"

To get around this just run a chkdsk /f
Then reboot back into Windows and run partition magic to change your partitions.

Hope this helps somebody.

---

### Post by mastapsi on 2006-12-09
The 1 GB partition is the quickplay partition.

---

