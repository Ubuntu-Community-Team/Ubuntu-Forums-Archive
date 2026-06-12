---
title: "kernel doesn't see all my system's ram"
date: 2007-03-05
forum: Hardware &amp; Laptops
---

### Post by zojas on 2007-03-05
I see this problem in edgy and fiesty, with the generic kernel. (the server kernels don't have this problem).

my system has 4gb of ram, but the kernel only sees 3gb of ram!

from dmesg at boot:

```

Warning only 4GB will be used.
[    0.000000] Use a PAE enabled kernel.
[    0.000000] 3200MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.

```

but once running, 'free' reports this:

```

2:19pm0fizzion#free -m
             total       used       free     shared    buffers     cached
Mem:          2907       1405       1502          0        208        661
-/+ buffers/cache:        535       2371
Swap:         2055          0       2055

```

when I boot in the server kernel, or into suse, free reports something like 3900 mb instead of 2907. what's going on?

---

### Post by peabody on 2007-03-05
Does 'top' report the same?  If so, it's likely a kernel bug, file a bug report.

---

### Post by zojas on 2007-03-05
yes, top has the same number, and more importantly, so does /proc/meminfo.

---

