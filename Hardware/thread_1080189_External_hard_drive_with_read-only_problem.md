---
title: "External hard drive with read-only problem"
date: 2009-02-25
forum: Hardware
---

### Post by Karadras on 2009-02-25
For some time i`ve some problem with my external drive (Western Digital 500 GB). It became read-only for Ubuntu, but I haven`t change a thing. On Windows, there is no such problem.

Isuppose the "reason" is that I tried to move on it some very large files (>3gb). In addition some new files appeared with a strange names, with some symbols, which I can`t delete in both of the OS.

---

### Post by vanadium on 2009-02-25
I am just guessing that this is a fat formatted file system that badly needs to be checked. Perform a check and repair of the file system first before attempting anything else.

---

### Post by Karadras on 2009-02-25
Where to perform the check and the repair, on Win or on Ubuntu?

---

### Post by vanadium on 2009-02-25
Wherever. Ubuntu supports vfat perfectly. The tool is "dosfsck".

---

