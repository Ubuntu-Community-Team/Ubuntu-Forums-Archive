---
title: "Hardware Performance"
date: 2010-09-10
forum: Hardware
---

### Post by ash369 on 2010-09-10
Could someone please explain to me about the cpu and memory usage in this picture? I don't understand it. After adding up the values in the table i get that the three running applications are using about 170% of the CPU and using about 25% of the memory. I'm assuming the 170% is out of 200% because there are 2 CPU cores.

Yet above it, it says its using 80% of the CPU and almost all of the memory with only about 17MB free.

Whats going on?

Dedicated server specs

```
Processor: 2.8GHz Dual Core
CPU Cores: 2
Hard drive: 500GB SATA
RAM: 2GB

Connection: 100Mbps
Bandwidth: Unlimited
IP Addresses: 2

Operating System: Ubuntu 9 64-Bit
```

Image

[IMG]http://img831.imageshack.us/img831/7945/overload.jpg[/IMG]

---

### Post by kidders on 2010-09-11
Hi there,

What aspect of the stats are you having trouble with? I'm not sure how much help this'll be, since it's all just arithmetic, but here goes. Suffice it to say, the numbers *do* add up ...


**CPU usage**
Breakdown by process: 97% + 37% + 29% = 163%
Breakdown by class: (79.1 x 2)% + (2.0 x 2)% + (0.3 x 2)% = 162.8%

Seems to add up. What's missing here is the per-core CPU usage, which you could have displayed by hitting '1'.

**Memory usage**
_Approximate_ total usage by running processes: 208MiB + 110MiB + 132MiB = 450MiB
This figure is approximate (possibly *very* approximate!) for two reasons:[LIST=1]
[*]Since you didn't post a screenshot with the processes ordered by memory usage, we aren't seeing a complete breakdown. It's very unlikely that there are only four processes using any RAM.
[*]Adding up resident memory allocations like this isn't strictly valid, since some memory will get counted twice, and other memory won't get counted at all.
[/LIST]

Anyhow, that approximation gives a total RAM usage of around ...
1138.29 (MiB caches) + 229.23 (MiB buffers) + 450 (MiB processes) =  1804.07 to 1817.52 MiB. The uncertainty is due to the fact that up to 13.45MiB of the memory allocated to caches could be swapped.

The total usage given by top is 1871.31MiB, so given how rough my numbers are, that adds up quite well. It means, your box has 16.63MiB of free (ie wasted) RAM, and up to 1.11GiB of easily free*able* RAM at its disposal, before it would have to go out of its way to find memory to allocate to something new ... pretty healthy numbers.

I hope that's at least *some* help ... Your query is pretty general!

---

### Post by ash369 on 2010-09-11
Thanks for taking the time to reply kidders it makes a lot more sense now. I am running three source dedicated servers on this machine and i am just trying to make sure everything can run correctly, lag free. I think running two servers is the max with this set-up.

---

