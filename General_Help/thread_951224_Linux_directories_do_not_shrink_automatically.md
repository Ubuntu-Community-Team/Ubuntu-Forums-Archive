---
title: "Linux directories do not shrink automatically"
date: 2008-10-17
forum: General Help
---

### Post by sulekha on 2008-10-17
Hi all,

this is what i have read in a book

Because Linux directories do not shrink automatically, removing a file
from a directory does not shrink the directory, even though it frees
up space on the disk.remove unused space and make a directory smaller,
you must copy or move all the files to a new directory and remove the
original directory.

how valid is this claim ?

---

### Post by MaxIBoy on 2008-10-17
Sounds like a load of carp to me. Perhaps this was a restriction of the Minix filesystem at some point, but something that archaic would not exist in ext2, ext3, or ext4.

---

### Post by bigbear2350 on 2008-10-20
Its True

[http://sourceforge.net/mailarchive/forum.php?thread_name=alpine.DEB.1.10.0803291346060.21122%40sheep.housecafe.de&forum_name=jfs-discussion](http://sourceforge.net/mailarchive/forum.php?thread_name=alpine.DEB.1.10.0803291346060.21122%40sheep.housecafe.de&forum_name=jfs-discussion)

[http://osdir.com/ml/file-systems.ext3.user/2006-08/msg00005.html](http://osdir.com/ml/file-systems.ext3.user/2006-08/msg00005.html)

> The fact that ext3 doesn't shrink directories is a long-standing Uniximplementation restriction. It's not impossible for us to add supportfor truncating directories as files get deleted, but it's just neverbubbled up to the top of the todo list; in practice, workloads thatcreate gigantic directories that then shrink down to nothing arerelatively rare.

---

### Post by vanadium on 2008-10-20
It is indeed true. You can see it for yourself:

```

mkdir test
ls -lad test
echo "this is a file" | tee test/file{1..1000}
ls -lad test
rm -f test/*
ls -lad test

```

I knew this is the case with fat and fat32, but I never imagined ext3 would suffer the same issue.

---

