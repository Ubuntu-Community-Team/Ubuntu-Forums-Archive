---
title: "Can I loose data while the disk partition is unmounted?"
date: 2011-01-31
forum: Hardware
---

### Post by S.A.A on 2011-01-31
Due to some regular craches (I'm working on it), I've encountered some very annoying data loss on the active partition (ext4 file system) and obviously it's because "Delayed allocation". 

My workaround is to move my files (these are only documents) to another partiton (ext4 too), and when I know the crash is coming (It's hardaware related issue), I do "umount".

So my simple question is: can I loose my documents from the unmounted partition?

---

### Post by vanadium on 2011-01-31
You won't lose data from a disk that is not in use, whether it is mounted or not. The data loss occurs when you are actively writing to a disk while the crash occurs.

With a journaled file system, the risk of severe data loss should be low compared to using a non journaled file system. It is probably existing nevertheless.

Unstead of unmounting the disk, you could also flush the cache right after a copy operation: I believe this is done by the "sync" command.

---

### Post by S.A.A on 2011-01-31
Thanks for the quick reply and for the infos.

---

