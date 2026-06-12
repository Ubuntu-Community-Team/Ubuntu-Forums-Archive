---
title: "Performance problem using SATA"
date: 2015-09-16
forum: Hardware
---

### Post by sariel2 on 2015-09-16
Hi *,
i have a performance problem when i'm trying to write to my NAND SATA flash.
from my understanding when using SATA I communication, my average write speed should be ~1.5Gb/s --> ~150MB/s.
i'm trying to measure my write throughput using the following "dd" command:
[COLOR=#000000][FONT=monospace]"dd bs=100M count=10 if=/dev/zero of=/tmp/test conv=fdatasync"
according to the output i see write speed of ~40MB/sec....!?

what do i miss? is there any kernel configuration which limit the speed? do i use correct the dd command?

p.s: i use x-ubuntu - 10.04 -- 2.6.32.21

Thanks in advance,
Sariel[/FONT][/COLOR]

---

### Post by weatherman2 on 2015-09-16
What are the specs of the SSD you are using?  What is the maximum write speed?

Xubuntu 10.04 support ended some time ago.  You should at least boot a newer version of Ubuntu live and try it.  Maybe a newer kernel has better drivers - you can try.

When I run that dd command on my laptop with a Crucial M500 480GB SSD (Sata II), I get 93 MB/s, even though "sustained sequential write" is spec'ed at up to 400MB/s.

---

### Post by sariel2 on 2015-09-16
according to the DS, the SSD support SATA-II, i really expect better performance...
currently i can't upgrade my dis to a newer one, sorry :(

can it be related to my libATA configuration in some way?
according to this lib there is some options to force SATA speed....

---

### Post by tgalati4 on 2015-09-16
Try 1M and 10M block size, perhaps the flash controller is having problems with large (100M) block sizes.  I wouldn't use dd to measure speed.  Use real file transfers, afterall that is the workload you are trying to simulate.

---

