---
title: "[SOLVED] Accessing root.disk from windows"
date: 2008-09-02
forum: General Help
---

### Post by dodle on 2008-09-02
Is there a way, or a tool that allows you to access the filesystem stored in root.disk from Windows?  I've heard that Wubi can be run as a virtual machine, but don't know if it's true.  I'm not all that familiar with virtualization, but it sounds as though transferring files from your local machine to your virtual machine isn't possible, or is it?

---

### Post by dodle on 2008-09-02
Sorry for creating a thread with such a simple solution.  I found an answer here [http://uranus.it.swin.edu.au/~jn/linux/explore2fs-old.htm#Download]("http://uranus.it.swin.edu.au/~jn/linux/explore2fs-old.htm#Download")

I have Ext2fsd installed, but that only works to mount physical partitions.  Which I like because it allows you to browse through your Linux partition with Explorer just like it's a regular Windows partition.

---

