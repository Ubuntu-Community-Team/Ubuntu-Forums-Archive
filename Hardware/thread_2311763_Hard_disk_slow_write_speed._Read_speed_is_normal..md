---
title: "Hard disk slow write speed. Read speed is normal."
date: 2016-01-29
forum: Hardware
---

### Post by genian93 on 2016-01-29
I have 2 disks on my PC.

One is an 250 GB SSD with one partition for Ubuntu, one for Windows and one for storing files that should be read as fast as possible.

The second one is an 500 GB HDD with only one NTFS partition for storing files.

Some time ago I noticed that my write speed on HDD is very, very slow. It is always less than 100 kB/sec.
However, reading speed is ok, but when I am writing anything and trying to read something else at the same time, reading speed is also very slow.

On Windows the disk works normally.

[IMG]http://s10.postimg.org/caj2i6usp/Write_speed.png[/IMG]


Here is the output of "dstat -D hdb":
[IMG]http://s10.postimg.org/e3lz6ifzd/dstat.png[/IMG]

I see that the drive is always idle, even when it is writing.

I don't have any ideas what can be wrong...

---

### Post by weatherman2 on 2016-01-29
Could be several issues.

However, you should know that the "fuse" driver that lets Linux access NTFS partitions is not perfect.  Although it has been reliable for me (no corruption issues or anything), it seems to use a lot of CPU, especially on very large files, especially when writing them.   If your CPU is not very fast, your write could be very slow.

 Try writing the same 10.8GB file to your SSD, to the Windows NTFS partition, and see how the write speed compares.   (Compare to writing the same file to a Linux partition.)  If you have the same issues, then it is probably due to the fuse driver; but if the write speed is OK to the SSD's NTFS partition, then probably this isn't your issue.

---

### Post by genian93 on 2016-01-30
I didn't notice any problems with CPU while writing. Also, my PC was build for gaming, so CPU shouldn't be the reason.

I tried to write the same file to partitions on SSD, and there were no problems. The speed wasn't shown, but it took about 10 seconds to write 10 GB.

About 2 months ago I tried to control spin down time for HDD, using **hdparm** from this post:
[http://askubuntu.com/questions/39760/how-can-i-control-hdd-spin-down-time](http://askubuntu.com/questions/39760/how-can-i-control-hdd-spin-down-time)
That's the only cause when I did something to HDD, but it was ok until last week.

---

### Post by weatherman2 on 2016-01-30
Have you checked the S.M.A.R.T. health of the 500GB hard drive?  Run a test?  Perhaps the drive itself is starting to fail?

---

### Post by genian93 on 2016-01-30
The test says that it is ok.
Also, on Windows it works normally.

---

