---
title: "Compiling kernel and inode.o"
date: 2005-12-05
forum: General Help
---

### Post by cougem on 2005-12-05
Hi I followed the tips in this topic on trying to get the kernel compiled on an Acer 8104 laptop.
[http://www.ubuntuforums.org/showthread.php?t=46536](http://www.ubuntuforums.org/showthread.php?t=46536)

I used his config to compile my kernel, but I'm getting:

CC fs/inode.o
fs/inode.c:1093: error: static declaration of ‘generic_drop_inode’ follows non-static declaration
include/linux/fs.h:1418: error: previous declaration of ‘generic_drop_inode’ was here
make[2]: *** [fs/inode.o] Error 1
make[1]: *** [fs] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.12'
make: *** [stamp-build] Error 2


Do you know what could be causing this? What's inode.o? Nobody else in that topic got problems, though maybe they were using hoary?

Many thanks,

cougem

---

