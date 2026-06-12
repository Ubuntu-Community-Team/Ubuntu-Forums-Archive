---
title: "What will be placed in the mounted partitions?"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by dE_logics on 2009-04-10
For this kernel, the world of storage is limited to the directories in the root folder only and other partition/drives/devices will have to be accessed through these directories, or the new device will be a part of these directories.
Now can the OS automatically put files in these mounted partitions depending on what folder is it mounted in?...for example I mounted sdb2 in /usr/bin or /bin, will the OS put binary files in these mounted partitions automatically (of course if any installation is made which generates binaries, or a source code is compiled and after the step 'make install' all while the partition is mounted)?
If yes, can I specify which binaries/libraries/etc... from the installation needs to be put in which mounted partition?

---

### Post by Mark Phelps on 2009-04-10
If you're asking can you specify where to write certain kinds of files during an Ubuntu installation, the answer is -- kind of.

By that I mean, that if you partition your drive such that / (root) and /home are different partitions, then the corresponding files will be written to the different partitions during installation.

If you're asking about specifying locations for individual files during installation, I don't believe there's any way to do that.

---

### Post by dE_logics on 2009-04-11
That means nothing will go in the mounted drives even though its in a working folder.

---

### Post by dE_logics on 2009-04-11
Someone told me a different story.....](*,)

---

### Post by dE_logics on 2009-04-11
No one knows?

---

### Post by cariboo on 2009-04-12
This may help you sort things out. [Filesystem Hierarchy]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard")

Jim

---

### Post by dE_logics on 2009-04-12
Doesnt answer the question.

---

