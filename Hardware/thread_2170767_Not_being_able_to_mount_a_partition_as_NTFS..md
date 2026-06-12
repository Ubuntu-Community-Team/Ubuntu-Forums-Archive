---
title: "Not being able to mount a partition as NTFS."
date: 2013-08-27
forum: Hardware
---

### Post by axy-david on 2013-08-27
Hello,
So I mistakenly made a NTFS partition as linux-swap, I fixed that and  now the partition is fully functional in windows, but when I check with  GParted it still detects it as a linux-swap type. What can I do  to mount that partition as NTFS?
Can I force mount it or is there any other way?
I already tried to change the partition type from terminal, it said it succeeded but it still detects it as a linux-swap.

---

### Post by Bashing-om on 2013-08-27
axy-david; Hi !

I believe, if it were me, in this situation I would:
fire up ubuntu's partition editor GParted and delete that partition -> unallocated space;
fire up Windows disk utility and in Windows create the NTFS partition.

Not to say that ubuntu can not create the NTFS partition, but, native tools will assure a greater chance of success. Ubuntu can read/write NTFS however, Windows does not do the opposite thus the suggestion; Windows' tools for Windows file systems and ubuntu for ubuntu's file system.

 [INDENT]just my opinion
[/INDENT]

---

### Post by oldfred on 2013-08-27
Duplicate, closed.

Please do not create duplicate threads on the same topic. We all are volunteers and need to know what others have already suggested.

See
[http://ubuntuforums.org/showthread.php?t=2170779](http://ubuntuforums.org/showthread.php?t=2170779)

---

