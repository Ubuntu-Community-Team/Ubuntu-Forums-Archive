---
title: "Clean install of Ubuntu"
date: 2008-11-07
forum: General Help
---

### Post by Chapeen on 2008-11-07
Hi,
I did certain manipulations to ubuntu which in consequence I cannot
get in to ubuntu anymore (I only get a black screen with bunch of letters which means nothing to me).How can I reinstall Ubuntu on that same partition? I have Vista as a second OS.I do not want to damage my Vista partition.

---

### Post by ibuclaw on 2008-11-07
When the installation asks you for how you want to partition the hard drive, select **manual** and be weary not to confuse the two. Windows uses **NTFS** and Linux uses **ext3**.

Click the Linux partition and set it to use as **ext3**, mount point **/** and format **yes**.

Double check that it is the right partition you have selected. Then proceed with the installation as normal.

Regards
Iain

---

