---
title: "new user"
date: 2007-06-14
forum: Georgia Team - US
---

### Post by discover on 2007-06-14
hello
I am new to linux and got install UBUNTU on my system can anyone tell me how can I know on which partition of hdd current OS is installed.
thankin you

---

### Post by Stephen Howard on 2007-06-14
have a look at the text file /etc/fstab.  Find "/" in the mountpoint column, and the first entry of that row should say /dev/sdXX (or maybe /dev/hdXX) - that's the partition that the OS is using.

Note that there may be other partitions being used.  For instance, some people configure a separate partition for swap space, applications and their home directories.

---

