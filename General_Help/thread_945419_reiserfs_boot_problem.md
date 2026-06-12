---
title: "reiserfs boot problem"
date: 2008-10-12
forum: General Help
---

### Post by Linneo on 2008-10-12
Hello.
I'm having a strange problem.
Searching the forum and google I've found this problem but still no solution.
It started yesterday. I've even deleted the root partition and restored it from a partimage backup imge, but still the same message at boot:

fsck 1.40.8 (13-Mar-2008)
Filesystem seems mounted read-only. Skipping journal replay.
Checking internal tree..finished
Reiserfs super block in block 16 on 0x806 of format 3.6 with standard journal
Blocks (total/free): 12207376/11408674 by 4096 bytes
Filesystem is clean
Reiserfs super block in block 16 on 0x806 of format 3.6 with standard journal
Blocks (total/free): 12207376/11408674 by 4096 bytes
Filesystem is clean

Any ideas?
Thanks

---

### Post by spiderbatdad on 2008-10-12
so what is the problem? That looks normal. Is it that it keeps checking during boot?
Reiserfs is not ideal for all file systems...it is particularly suited to /var if you wanted a separate partition for logs, otherwise ext2 or ext3 would be preferred for your linux file system.

---

### Post by sokopok on 2008-10-12
It's the filesystem check that happens at every boot. It's telling you "Filesystem is clean". So there is no problem.

You can try this to make sure the splash screen doesnt disappear so you don't see these messages: [http://ubuntuforums.org/showthread.php?t=863454&highlight=checkfs.sh](http://ubuntuforums.org/showthread.php?t=863454&highlight=checkfs.sh)

---

