---
title: "Bad Sectors"
date: 2010-03-15
forum: Hardware
---

### Post by ferret man on 2010-03-15
My external hard drive has had some valuable data on it (credit card numbers), so I securely overwrote it using the command ```
sudo shred -v -c 4 /dev/sdb
```
That worked, and it overwrote, but some system software started sensing "bad sectors". It says that disk failure is sure to happen, however, I just bought this. Is there a way to get rid of this. I thought that maybe if I used ```
sudo shred -z -v -c0 /dev/sdb
``` would work, because instead of the disk being filled with random data, it would be filled with 0's. Could someone tell me if this will work, and if not, what to do?

---

