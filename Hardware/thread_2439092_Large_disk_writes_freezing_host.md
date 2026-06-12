---
title: "Large disk writes freezing host"
date: 2020-03-22
forum: Hardware
---

### Post by fragged on 2020-03-22
I'm having an ongoing issue where writing a large amount to disk effectively freezing my system for periods of time (30 seconds or more). I believe this is caused by dirty writes filling memory cache and flushing to disk while blocking all other kernel IO ( [https://www.kernel.org/doc/Documentation/sysctl/vm.txt](https://www.kernel.org/doc/Documentation/sysctl/vm.txt) ).

System details:
6 Core Intel i7 Processor
64GB DDR4
1TB nVME SSD
Ubuntu 19.10

I've set the following options in sysctl.conf and have verified that they take effect:

```

vm.dirty_background_ratio = 1 # 1% of memory ~650mb, default is 10%
vm.dirty_ratio = 2 # , default is 20%
vm.dirty_writeback_centisecs = 200 # hundredths of second, 3000 default

```

This has resulted in the system freezing more often, but for less time which is to be expected. 

Optimally, not having the system freeze at all would be nice. Is there any functionality which will achieve non-blocking writes?

---

### Post by fragged on 2020-03-25
Bump

---

### Post by fragged on 2020-04-17
Bump

---

