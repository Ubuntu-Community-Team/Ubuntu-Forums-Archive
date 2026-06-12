---
title: "Ramtmp"
date: 2012-01-08
forum: Hardware
---

### Post by Theredbaron1834 on 2012-01-08
I have been running my tmp on ram via
> none /tmp tmpfs nr_inodes=200k,mode=01777,nosuid,nodev,size=2G 0 0The problem is that it seems to corrupt the ram upon restarting. I have to dual boot dows, for many reasons, and reboot at least once a day. If I want to restart, I have to shut down and let the ram clear, before booting.

Now I know that it doesn't give much, if any, speed improvement, but I don't have much free space on my hard drive. I do, however, have 6gb of ram, and I don't often use more then 2gb of it. So I wanted to use it for CD burning cache, ect.

So, does anybody know if (A) it is possible to do right, and/or (2) a better way to mount it as to not have that problem?

uname -a
> Linux theredbaron-desktop 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

---

