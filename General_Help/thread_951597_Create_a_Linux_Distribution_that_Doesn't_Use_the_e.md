---
title: "Create a Linux Distribution that Doesn't Use the ext3 filesystem"
date: 2008-10-18
forum: General Help
---

### Post by flouran on 2008-10-18
Hey guys,
I was wondering if it was at all possible to create a customized Ubuntu LiveCD that does not use the ext3 filesystem, but another filesystem (for instance, JFS)? I know that it is possible to do this because Linux is a "UNIX-like" OS which does not use the original UNIX filesystem, UFS, but uses ext3. Moreover, Macintosh OS X uses the Hfsplus filesystem, although it is based off of BSD which uses UFS as well. Lastly, HP UX is UNIX-based but uses the VxFS filesystem instead of UFS.

Also, if I changed the filesystem of Ubuntu, would that mean I would have to reprogram the Linux kernel's monolithic structure (although there is a kernel module for support with JFS)?


Any help is greatly appreciated,
Flouran

---

### Post by damis648 on 2008-10-18
When you install it, just select to format the / partition (or /home or whatever) as JFS or UFS or what you need and then select the mount point.

---

### Post by flouran on 2008-10-18
But, how would I customize the LiveCD so that by default it formats a partition as JFS?

---

