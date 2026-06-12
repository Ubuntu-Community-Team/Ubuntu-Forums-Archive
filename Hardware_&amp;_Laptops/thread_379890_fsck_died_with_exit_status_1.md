---
title: "fsck died with exit status 1"
date: 2007-03-09
forum: Hardware &amp; Laptops
---

### Post by jfenwick on 2007-03-09
I have two SATA hard drives in my computer, one has the root partition and one has the home partition. I just tried to boot up a few minutes and I got this error during fsck:

```

Log of fsck -C -R -A -a
Thu Mar  8 23:57:38 2007

fsck 1.39 (29-May-2006)
/dev/sda1: clean, 36/20080 files, 20327/40131 blocks
/dev/sdb1 has been mounted 30 times without being checked, check forced.
/dev/sdb1: 12383/13680640 files (7.0% non-contiguous), 11641196/27350654 blocks
fsck died with exit status 1

Thu Mar  8 23:59:43 2007
----------------

```

I looked up exit code 1 in the man page and found this:

> 1    - File system errors corrected

If that's the case, then why did it "die" with exit status 1? Did it fail or did it just correct errors? How do I found out what these errors are?

---

### Post by DagMan on 2007-03-11
It's just refering to the program terminating.  It means that fsck terminated with an exit status of 1, or that fsck finished and returned the information that corrections were made.
I wouldn't be concerned about an exit status 1 by the way.

---

