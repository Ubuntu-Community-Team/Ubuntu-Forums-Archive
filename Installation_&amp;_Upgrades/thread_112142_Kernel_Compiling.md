---
title: "Kernel Compiling"
date: 2006-01-03
forum: Installation &amp; Upgrades
---

### Post by TecnoVM64 on 2006-01-03
Hello people, I've been trying to compile the recent linux kernel 2.6.15 but i have the following problem:

root@h4x:/usr/src/linux# make xconfig
  HOSTCC  scripts/basic/fixdep
In file included from /usr/include/sys/socket.h:35,
                 from /usr/include/netinet/in.h:24,
                 from /usr/include/arpa/inet.h:23,
                 from scripts/basic/fixdep.c:115:
/usr/include/bits/socket.h:304:24: error: asm/socket.h: No such file or directory
make[1]: *** [scripts/basic/fixdep] Error 1
make: *** [scripts_basic] Error 2

Any ideas?

---

