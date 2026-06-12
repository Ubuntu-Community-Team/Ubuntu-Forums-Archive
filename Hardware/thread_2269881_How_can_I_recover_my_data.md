---
title: "How can I recover my data"
date: 2015-03-18
forum: Hardware
---

### Post by Fertech on 2015-03-18
I running a live cd Ubuntu 14.04.1LTS on my desktop and have plug in a 200gb hard drive but I can't seem to open my hard drive. I have 2 partitions, a /dev/sda1 ntfs 8503mb system windows recovery environment (loader)
 The second partition is /dev/sda1 ntfs 191543 system unknown
How can I open my hard drive and recover the data?

---

### Post by TheFu on 2015-03-18
Just a guess - boot into Windows and be certain it actually closes the file system during shutdown. This is a well-known issue with Win8+ - it doesn't actually properly close file systems at shutdown ON PURPOSE. This is the Windows DEFAULT now and screws with partitions we want to mount from Linux. Sorry - I don't remember the MSFT name for it.

---

