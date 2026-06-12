---
title: "How to defrag an external fuseblk storage disk"
date: 2012-11-19
forum: Hardware
---

### Post by blaineclrk on 2012-11-19
I've got a 1 TB external drive for storage with the file structure showing as fuseblk. I was wondering how to defrag the drive, or if I could format it to ext(x) and eliminate any need for defragging?

---

### Post by jerome1232 on 2012-11-19
Short version, fuseblk means it's NTFS. Honestly unless an NTFS partition get very full they don't fragment much either.

To my knowledge there is no NTFS defragger for Linux, I understand one is being ported currently and is in a testing phase.

---

