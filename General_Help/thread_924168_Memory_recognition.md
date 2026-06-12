---
title: "Memory recognition"
date: 2008-09-19
forum: General Help
---

### Post by bach on 2008-09-19
I have a Quad Core computer which has an Intel D975XBX2 motherboard. I increased the memory from 4 GB to 8GB (DDR2). The new memory was recognized by the bios but not bu Ubuntu 8.04 (32 bit). See below. 

What should I do? Thanks. 


cribari@edgeworth:~$ cat /proc/meminfo 
MemTotal:      3367832 kB
MemFree:       2526996 kB
Buffers:         18540 kB
Cached:         353932 kB
SwapCached:          0 kB
Active:         400924 kB
Inactive:       280500 kB
HighTotal:     2488276 kB
HighFree:      1809960 kB
LowTotal:       879556 kB
LowFree:        717036 kB
SwapTotal:     9863868 kB
SwapFree:      9863868 kB
Dirty:              48 kB
Writeback:           0 kB
AnonPages:      308952 kB
Mapped:          80724 kB
Slab:            20872 kB
SReclaimable:    11568 kB
SUnreclaim:       9304 kB
PageTables:       2476 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:  11547784 kB
Committed_AS:   854700 kB
VmallocTotal:   114680 kB
VmallocUsed:     23416 kB
VmallocChunk:    91192 kB
cribari@edgeworth:~$

---

### Post by iaculallad on 2008-09-19
An excerpt from [launchpad]("https://answers.launchpad.net/ubuntu/+question/40205"):

> An operating system can only support as much memory as the hardware can. A 32-bit system has an address space of 0-(2^32 - 1) so it can only support upto ~4 gigabytes of memory. This constraint applies to any operating system running on 32-bit hardware---linux, windows, or mac.

To answer your question, it depends on what type of hardware you have. If you have a 32-bit system, then ~4 gigabytes. If you have a 64-bit system, you can use more ram than you can afford.

---

### Post by anotherdisciple on 2008-09-19
Yes sir... 32 bit can only support 4 Gigs... that's a lot anyways... 4 gigs should be way more than enough for ubuntu...

However... if you want to make sure the extra RAM wasn't wasted money... try the 64 bit version

---

### Post by hyper_ch on 2008-09-19
you can just enable PAE in the kernel, then you can use up to 64GB ram on a 32 (or rather 34) bit system.

---

### Post by anotherdisciple on 2008-09-19
> **hyper_ch said:**
> you can just enable PAE in the kernel, then you can use up to 64GB ram on a 32 (or rather 34) bit system.

what?!?! How do you do that?

---

### Post by bach on 2008-09-19
Would installing the ubuntu server (32 bit) kernel be a quick solution? I would like to avoid having to compile the kernel. Thanks.

---

### Post by Vivaldi Gloria on 2008-09-19
> **bach said:**
> Would installing the ubuntu server (32 bit) kernel be a quick solution? 

Yes. See [[COLOR="Sienna"]this[/COLOR]]("http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel") for the differences between the desktop and server kernels.

---

### Post by hyper_ch on 2008-09-20
options are
(a) install server kernel which has PAE enabled by default
or
(b) compile your custom kernel with PAE enabled.

---

