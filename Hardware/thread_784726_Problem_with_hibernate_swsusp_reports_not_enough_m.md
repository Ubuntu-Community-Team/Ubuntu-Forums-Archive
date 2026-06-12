---
title: "Problem with hibernate: swsusp reports not enough memory"
date: 2008-05-06
forum: Hardware
---

### Post by ewand on 2008-05-06
Here is the error I (almost always) get when trying to hibernate on hardy:
```

swsusp: Not enough free memory
Error -12 while creating image
```

This started right after I added ram to my machine. I assumed it had to do with the size of the swap partition, so I used gparted so that now my situation looks like this:

```

ewan@ewan-ubuntu:~$ cat /proc/meminfo 
[B]MemTotal:       968820 kB
MemFree:        447904 kB[/B]
Buffers:          3268 kB
Cached:          89976 kB
SwapCached:       5852 kB
Active:         372760 kB
Inactive:        21156 kB
HighTotal:       64000 kB
HighFree:          184 kB
LowTotal:       904820 kB
LowFree:        447720 kB
[B]SwapTotal:     2104472 kB
SwapFree:      2043496 kB[/B]
Dirty:              36 kB
Writeback:           0 kB
AnonPages:      298860 kB
Mapped:          83412 kB
Slab:            15036 kB
SReclaimable:     6364 kB
SUnreclaim:       8672 kB
PageTables:       2672 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   2588880 kB
Committed_AS:   739096 kB
VmallocTotal:   114680 kB
VmallocUsed:     20384 kB
VmallocChunk:    93492 kB

```

I have more than twice as much swap as ram and, at any rate, at the moment I have far more free swap than I need to write the contents of ram out to swap. It has worked once since adding ram (I might have done something special, but I don't remember anything) but this definitely never happened before I added ram. That might be a coincidence of course - so any thoughts are welcome.
--ewan

---

### Post by ewand on 2008-05-08
*bump*

---

### Post by Thingymebob on 2008-11-23
Also had this problem, it appears that my image size was to big ( cat /sys/power/image_size ) this apparently needs to be less than 50% of available memory

I have 1Gb of memory so did:
as root
```

echo $((400*1024*1024)) > /sys/power/image_size

```
and now my system successfully hibernates and resumes, although resume takes forever for the hard disk to stop thrashing.

---

### Post by casainho on 2012-05-13
> **Thingymebob said:**
> Also had this problem, it appears that my image size was to big ( cat /sys/power/image_size ) this apparently needs to be less than 50% of available memory

I have 1Gb of memory so did:
as root
```

echo $((400*1024*1024)) > /sys/power/image_size

```
and now my system successfully hibernates and resumes, although resume takes forever for the hard disk to stop thrashing.

This resolved my problem :-)

Hibernation was working perfectly (I always ibernate instead of shuting down) on Ubuntu 11.10 but after update to 12.04 hibernation failed with this error.

My /sys/power/image_size was to big!! I just echo MY_RAM_SIZE > /sys/power/image_size and it now works as expected, perfectly :-)

---

