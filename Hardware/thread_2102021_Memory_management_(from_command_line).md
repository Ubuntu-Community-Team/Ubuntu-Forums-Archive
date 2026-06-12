---
title: "Memory management (from command line)"
date: 2013-01-06
forum: Hardware
---

### Post by Dubslow on 2013-01-06
Hello everyone!

Recently I acquired a headless box meant for solely for number crunching and web hosting. As such the first thing I did was install 12.04 server. Being a headless crunching machine, the only storage is a 40 GB SSD, so (with advice from the previous owner) I installed the OS without any swap set up.

Now, it has 8 GiB of RAM installed; I had been running four instances (one for each core) of a number cruncher that's advertised at up to 2 GB per instance, though I believe it rarely tops 1. Then, I started hosting a Minecraft server, and that's when I was starting to wonder how exactly things were coping. 

For a couple of days things worked relatively okay; some people reported some lag (where everyone's computers and my server were physically within 50 feet of each other), but it was minor enough that I wrote it off to a bit of fussing over the available memory. Then it got worse; eventually I took to shutting down the number crunchers when people were on the MC server, but despite that the lag kept getting worse. (To be honest, I haven't really solved that issue, or even located a cause, but this post is a tangent to that original issue.) So I tried to look at the memory in use with `top` -- and that's when I got really confused.

```
Tasks: 109 total,   2 running, 107 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.4%us,  0.1%sy,  3.2%ni, 92.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   8120712k total,  1908188k used,  6212524k free,   174008k buffers
Swap:        0k total,        0k used,        0k free,   657176k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 1683 bill      20   0 7922m 800m  12m S   42 10.1   1907:22 java
    1 root      20   0 24340 2300 1356 S    0  0.0   0:00.88 init

```
That's a recent (few minutes ago) snapshot; I've left the number crunchers off for the last week or so until I get these issues sorted through (and I've been more interested in other problems anyways).  First thing I did of course was look at the [top man page]("http://linux.die.net/man/1/top"). It claims that the VIRT number is the total mem footprint, including swapped out pages (I had to go look up what those two words meant as well), while RES is actual physical usage. So here's the problem: there's no swap space on this install (and I confirmed that with `swapon -s`). So where in the blazes is the "missing" 7122 MB (VIRT-RES) of virtual memory? Why isn't it using more of the physical memory if 75% of it is still available (going by the top headers before the proc list)?

Should I add swap space? Would that encourage the kernel to use more physical memory? (I'm going to upgrade that as well sometime soon, though that won't help if the kernel won't use it.) What's going on here?

Thanks for reading to the bottom, and double thanks for any tips :P

(PS On a completely unrelated note: With those number crunchers enabled, on logging in I get the "System info disabled due to load > 4.0" warning; can I somehow override that and get sys info regardless of load?)

---

### Post by Doug S on 2013-01-06
It might be important to consider that VIRT also includes "pages that have been mapped but not used". If a program asks for a bunch of memory, it will not show as RES until it is actually used.
 
As a demonstration example, consider a program that calls malloc for some huge amount of memory. It will show immediately under "VIRT" but not under "RES" until it is used. It also will not show as used in the top memory summary line, until it is actually used. Example:```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
24094 doug      20   0 4772m  356  276 S    0  0.0   0:00.00 testm  [COLOR=red]<<< Memory has been asked for, but not used yet[/COLOR]
 
24094 doug      20   0 4772m 3.4g  340 R   99 22.4   0:06.77 testm  [COLOR=red]<<< Memory part way through being used. Note CPU working.[/COLOR]
 
24094 doug      20   0 4772m 4.7g  340 S    0 30.5   0:09.21 testm  [COLOR=red]<<< All memory used[/COLOR]

```For your P.S. question, please see [this old forum thread]("http://ubuntuforums.org/showthread.php?t=2000524").

---

### Post by Yellow Pasque on 2013-01-06
You probably don't want to make swap space on your SSD if you use a ton of memory (it'll eat up a lot of read/write cycles for the SSD). Given that 8 or 16GB USB Flash drives are <=$10, I'd rather use those if I wanted a cheap, fast swap space (or just lay out $50 for a 320GB hard disk).

---

### Post by Dubslow on 2013-01-06
> **Doug S said:**
> It might be important to consider that VIRT also includes "pages that have been mapped but not used". If a program asks for a bunch of memory, it will not show as RES until it is actually used.
 
As a demonstration example, consider a program that calls malloc for some huge amount of memory. It will show immediately under "VIRT" but not under "RES" until it is used. It also will not show as used in the top memory summary line, until it is actually used. Example:```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
24094 doug      20   0 4772m  356  276 S    0  0.0   0:00.00 testm  [COLOR=red]<<< Memory has been asked for, but not used yet[/COLOR]
 
24094 doug      20   0 4772m 3.4g  340 R   99 22.4   0:06.77 testm  [COLOR=red]<<< Memory part way through being used. Note CPU working.[/COLOR]
 
24094 doug      20   0 4772m 4.7g  340 S    0 30.5   0:09.21 testm  [COLOR=red]<<< All memory used[/COLOR]

```For your P.S. question, please see [this old forum thread]("http://ubuntuforums.org/showthread.php?t=2000524").

Ah, thanks. So, if you (e.g.) did `void* ptr = malloc(1024*1024*1024); // 1 GiB`, then that wouldn't show up in RES, but then if I did `memset(ptr, 0, 1024*1024*1024); // access memory` then it would show up in RES?

> **Temüjin said:**
> You probably don't want to make swap space on your SSD if you use a ton of memory (it'll eat up a lot of read/write cycles for the SSD). Given that 8 or 16GB USB Flash drives are <=$10, I'd rather use those if I wanted a cheap, fast swap space (or just lay out $50 for a 320GB hard disk).

I'm not convinced I actually need a swap space though, since the physical memory used is still only %25 of 8 GiB. Thanks for the flash drive idea though.

---

### Post by Doug S on 2013-01-07
> Ah, thanks. So, if you (e.g.) did `void* ptr = malloc(1024*1024*1024); // 1 GiB`, then that wouldn't show up in RES, but then if I did `memset(ptr, 0, 1024*1024*1024); // access memory` then it would show up in RES?
Yes.

---

