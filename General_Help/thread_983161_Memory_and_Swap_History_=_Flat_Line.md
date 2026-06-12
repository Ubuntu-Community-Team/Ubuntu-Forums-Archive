---
title: "Memory and Swap History = Flat Line"
date: 2008-11-15
forum: General Help
---

### Post by moon2js on 2008-11-15
I have an older system, Athlon/1200MHz circa 2001, that usually works well enough for general web browsing, not much more.

What I've noticed on all recent versions of Ubuntu, including the current Intrepid is that on the System Monitor, memory and swap history are always a flat line.

Disk use spikes normally, CPU hovers in the top quarter, often maxing out in the 90+ percentile, but memory always stays around 56~57% usage and swap is around 46%. That means my computer is using 433mb out of available RAM of 755.5?

Is there a reason why the system never uses much more than half available RAM? I've such little RAM that I can't imagine why the system wouldn't put more use to it. Or is this just a reporting glitch?

```
$ /proc/meminfo
MemTotal:       773664 kB
MemFree:        133248 kB
Buffers:         12696 kB
Cached:         186520 kB
SwapCached:      28692 kB
Active:         424796 kB
Inactive:       164868 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       773664 kB
LowFree:        133248 kB
SwapTotal:      313228 kB
SwapFree:       262408 kB
Dirty:              20 kB
Writeback:           0 kB
AnonPages:      378388 kB
Mapped:          68260 kB
Slab:            23272 kB
SReclaimable:     9132 kB
SUnreclaim:      14140 kB
PageTables:       3448 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
WritebackTmp:        0 kB
CommitLimit:    700060 kB
Committed_AS:  1058824 kB
VmallocTotal:   241656 kB
VmallocUsed:      8952 kB
VmallocChunk:   231660 kB
HugePages_Total:     0
HugePages_Free:      0
HugePages_Rsvd:      0
HugePages_Surp:      0
Hugepagesize:     4096 kB
DirectMap4k:     36736 kB
DirectMap4M:    749568 kB
```

---

### Post by sdennie on 2008-11-15
That seems normal to me.  If you aren't opening more apps, why would you use more memory?  If the swapping is annoying, one thing you could do to potentially improve performance is to tell the kernel to prefer main memory.  Add the following to /etc/sysctl.conf:

```

vm.swappiness = 0

```

Then run:

```

sudo sysctl -p

```

After doing that, your swap usage will drop dramatically while your memory usage will increase.  Though, if you are already using swap, you won't notice this change until you reboot (or turn the swap off and then on but, that might not work if your total memory usage + swap is greater than the available memory).

---

### Post by moon2js on 2008-11-16
Wait, so memory usage like that is normal? I've tried running lots of applications -- web browser, video, tuxracer, etc., and still the system won't touch that top third of RAMspace. Isn't unused RAM kinda a waste, though? Or is my machine's bottleneck the proc?

I had a Mac (apples and oranges?) and on its System Monitor, general web browsing rarely ties up less than 512mb and given enough time, it would engulf the memory usage pie chart, so that's why I'm a little surprised this machine doesn't want to use everything it's got. Is Linux a bit more dilligent in freeing up inactive memory stuff?

Is there a reason why the system is using the swap at all when there's so much memory free? And is there a downside to forcing it to use memory instead of the swap?

---

