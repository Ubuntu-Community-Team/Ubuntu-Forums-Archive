---
title: "Not able to partition external USB hard drive with LiveCD"
date: 2008-10-31
forum: General Help
---

### Post by codeking on 2008-10-31
I'm trying to partition an external USB hard drive on a computer running Ubuntu LiveCD.  Whenever I try to resize the current partition it gives me the following error:

> ntfsresize v2.0.0 (libntfs 10:0:0)
ERROR(95): Opening '/dev/sdf1' as NTFS failed: Operation not supported
The NTFS journal file is unclean. Please shutdown Windows properly before
using this software! Note, if you have run chkdsk previously then boot
Windows again which will automatically initialize the journal correctly.

I don't know why it says its unclean, it works fine on windows.

Also I am unable to mount any of my partitions (both on internal and external hard drive) to view the files.

So how can I get this hard drive partitioned?

---

### Post by sacauntos on 2010-01-15
Hello,
I'm having a similar issue. I have a single 160Gb HD and I am dual booting windows xp and ubuntu 9.04. Windows partition is NTFS formatted and is way bigger than my ubuntu partition. I wanted to free some more space from the NTFS partition and gain it for linux, but without having to re-install windows (there are some things I'm afraid I won't be able to replace so easily).

I used gparted after installing ntfsprogs and I get the same error as codeking above, but unlike him, I can mount the ntfs partition and see its files.

Does anyone know how to overcome this issue?

Thanks a lot.

---

