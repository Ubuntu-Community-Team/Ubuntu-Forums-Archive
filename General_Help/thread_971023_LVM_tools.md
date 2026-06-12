---
title: "LVM tools"
date: 2008-11-04
forum: General Help
---

### Post by rnelson0 on 2008-11-04
Hi all! I've been using LVM with my hard drives for a while now and however much I like the idea, the recent crash of a hard drive convinced me that it is not as great as it seem.

I have a question regarding LVM. Say I have an LVM volume made up to two drives, is there any way for me to see how much of the data on the logical volume is actually stored on the second drive?

Thanks in advance.

---

### Post by Cruz on 2008-11-04
Yes. Try vgscan and vgdisplay. One of them shows you how the PEs are distributed over the physical volumes and how much is free on which.

---

### Post by rnelson0 on 2008-11-04
Damn... is that all? I guess I don't know how to read what vgscan and vgdisplay are telling me. Time for me to read the man pages, eh?

---

