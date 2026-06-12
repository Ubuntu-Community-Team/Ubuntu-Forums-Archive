---
title: "Acer 8104 / 8100 - Compiling kernel issues"
date: 2005-12-05
forum: Hardware &amp; Laptops
---

### Post by cougem on 2005-12-05
Hi I followed the tips in this topic:
[http://www.ubuntuforums.org/showthread.php?t=46536](http://www.ubuntuforums.org/showthread.php?t=46536)

I used this config to compile my kernel, but I'm getting:

CC fs/inode.o
fs/inode.c:1093: error: static declaration of ‘generic_drop_inode’ follows non-static declaration
include/linux/fs.h:1418: error: previous declaration of ‘generic_drop_inode’ was here
make[2]: *** [fs/inode.o] Error 1
make[1]: *** [fs] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.12'
make: *** [stamp-build] Error 2


Do you know what could be causing this?
Many thanks,

cougem

---

