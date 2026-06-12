---
title: "Using ext2/ext3 on Windows"
date: 2008-09-26
forum: General Help
---

### Post by MakLeod on 2008-09-26
Hey all,

I just had a quick question.  I've been using ext2fs (driver allowing windows to access ext2/ext3 partitions).  I use my /home as my storage and backup partition while also using it for my windows games.  Maybe I am paranoid, but I've been noticing some load/lag issues with certain games.  Could this be at all from Windows accessing an ext2 partition through the ext2fs driver?  Will I get better gaming performance out of using a native NTFS partition or does it not matter if I use an ext2/ext3 drive?  Sorry if this doesn't make sense...thanks!

---

### Post by Pro-reason on 2008-09-26
I have not heard of this specific problem before, but it would not be at all surprising if third-party file-system drivers performed more slowly than drivers built into the Windows kernel.  The same certainly happens with Linux.

---

