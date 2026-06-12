---
title: "Memory Size Error"
date: 2005-09-12
forum: Hardware &amp; Laptops
---

### Post by Ahriman on 2005-09-12
I have noticed in the week or two that I have been using Ubuntu that it doesn't apparently see all of my RAM. I have 1.5GB RAM, but in System Monitor (and an X-Chat sysinfo script), it says there is only 883MB of memory in total.

Is that the maximum it can display, or do I need to set something so that it looks for all my memory?

I did ```
cat /proc/meminfo
``` and it says:

```

mark@mushtir:-$ cat /proc/meminfo
MemTotal:	906660 kB
MemFree:	33156 kB
Buffers:	95608 kB
Cached:		457504 kB
SwapCached:	0 kB
Active:		334532 kB
Inactive:	349428 kB
HighTotal:	0 kB
HighFree:	0 kB
LowTotal:	906660 kB
LowFree:	33156 kB
SwapTotal:	1020116 kB
SwapFree:	1020116 kB
Dirty:		484 kB
Writeback:	0 kB
Mapped:		168816 kB
Slab:		167844 kB
CommitLimitL	1473444 kB
Committed_AS:	470044 kB
PageTables:	1868 kB
VmallocTotal:	122800 kB
VmallocUsed:	14812 kB
VmallocChunk:	107432 kB
mark@mushtir:-$

```

Cheers :-)

- Ahriman

---

### Post by Ahriman on 2005-09-12
*bump*

---

### Post by Ahriman on 2005-09-13
*bump* again

---

### Post by Ahriman on 2005-09-14
*BUMP* Yet Again

---

### Post by doclivingston on 2005-09-14
The 386 kernel doesn't support more memory than that - installing either the 686(intel) or k7(amd) kernel should fix it. The package you need to install is either linux-686 or linux-k7.

---

### Post by Ahriman on 2005-09-14
Thanks, doclivingston, that fixed the problem quite nicely. :)

---

