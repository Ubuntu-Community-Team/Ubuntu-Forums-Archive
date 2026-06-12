---
title: "intensive disk read/writes are prioritized"
date: 2011-10-16
forum: Hardware
---

### Post by superpisto on 2011-10-16
Did you notice it too? it seems that disk utilization changed from 11.04: when copying big files or doing other disk intensive operation (e.g. create a new VDI with static allocation in virtualbox), OS seems to give high priority to this task, starving almost every other read/write requests. This gives more speed to disk intensive tasks indeed (I get 30 instead of 24 MB/s in copy between partitions), but almost blocks any other application.

Can I tune this thing? The extra speed is good, but I'd like to make the setting less "aggressive".

---

