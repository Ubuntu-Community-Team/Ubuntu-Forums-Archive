---
title: "[SOLVED] rsync: --compare-dest does not appear to be working"
date: 2008-09-30
forum: General Help
---

### Post by Meson on 2008-09-30
Observe the following:

```

~$ mkdir original
~$ echo "contents1" > original/file1
~$ echo "contents2" > original/file2
~$ 
~$ rsync -a --itemize-changes original/ backup1
cd+++++++++ ./
>f+++++++++ file1
>f+++++++++ file2
~$ 
~$ rsync -a --itemize-changes --compare-dest=backup1/ original/ backup2
cd+++++++++ ./
>f+++++++++ file1
>f+++++++++ file2
~$ 
~$ ll original backup1 backup2
backup1:
total 8
-rw------- 1 matt matt 10 2008-09-30 13:42 file1
-rw------- 1 matt matt 10 2008-09-30 13:43 file2

backup2:
total 8
-rw------- 1 matt matt 10 2008-09-30 13:42 file1
-rw------- 1 matt matt 10 2008-09-30 13:43 file2

original:
total 8
-rw------- 1 matt matt 10 2008-09-30 13:42 file1
-rw------- 1 matt matt 10 2008-09-30 13:43 file2

```

Shouldn't backup2/ be blank?

---

### Post by Meson on 2008-09-30
The argument for --compare-dest is relative to the backup dir.

I should have run:
```

rsync -a --itemize-changes --compare-dest=**../**backup1/ original/ backup2

```

---

