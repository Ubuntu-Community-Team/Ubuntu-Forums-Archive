---
title: "[SOLVED] Ubuntu install problem.."
date: 2008-10-03
forum: General Help
---

### Post by Axerthon on 2008-10-03
Well, I try to reinstall Ubuntu 8.04.1 from scratch, and when I arrive at the screen where it is copying files,after a while it says something about my hard disk being read only... :confused:

The CD is okay, I tested it's md5sum and I also checked it with the built-in CD integraity checker. No warnings or errors.

Any help? Very very weird problem :|

---

### Post by Zill on 2008-10-03
More detail of what you actually require and what you have done so far will help.  eg.

1)  When you say reinstall, does this mean the PC has already had 8.04 installed before and, if so, was the installation successful?

2)  Do you want a totally clean install removing all previous programs and data, or do you want to retain part of your old installation such as your /home directory and/or <shudder> MS Windows?

---

### Post by Axerthon on 2008-10-04
1. 8.04.1 was installed, I tried to upgrade the OS and on the middle of the update it crashed...I restarted and all was destroyed.
2. Yes yes, I want a 100% clean computer.

---

### Post by /////// on 2008-10-04
Load Ubuntu from the install disk, go to System>Administration>Partition Editor. In GParted, delete all the previous partition on the disk. Then re-create a new ext3 partition. When installing Ubuntu from the disk, choose the manual disk scheme thing (where it asks you about the partitions) and select the partition you created as the / (root) folder.

---

### Post by Axerthon on 2008-10-04
Thanks a lot. Can be closed.

---

### Post by Zill on 2008-10-04
> **Axerthon said:**
> Thanks a lot. Can be closed.
Glad you got things working :-)

Would you now please go to the Thread Tools menu at the top of the page and "Mark this thread as solved".

Only the originator can do this and it will help others searching for solutions.  Thank you.

---

