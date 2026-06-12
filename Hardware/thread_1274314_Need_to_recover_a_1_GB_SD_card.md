---
title: "Need to recover a 1 GB SD card"
date: 2009-09-24
forum: Hardware
---

### Post by epicoder on 2009-09-24
I have a 1 GB SD card my friend tried to put Linux on, and now my system can't detect it. Whenever I try to manually mount it or do anything like that, I get, for example, 'mount: /dev/sdb: unknown device'. The only thing I can think of that might help you is that my sd card reader is /dev/sdb.

---

### Post by amingv on 2009-09-24
The installation process may have done many partitions on it (accessible as sdb1, sdb2, etc; try to tab-complete them to see if they come up).
Additionally you can try to reformat the drive with gparted.

If all fails the drive may have been damaged, try running ```
dmesg
```
after plugging it to see if it's loaded or even recognized.

---

