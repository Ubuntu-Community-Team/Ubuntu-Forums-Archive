---
title: "remove file and all hardlinks ie: COMPLETE remove"
date: 2008-09-30
forum: General Help
---

### Post by Meson on 2008-09-30
How can I completely remove a file?  If for example there are 10 hardlinks throughout the same system, how can I remove them all at once?

---

### Post by dcstar on 2008-09-30
> **Meson said:**
> How can I completely remove a file?  If for example there are 10 hardlinks throughout the same system, how can I remove them all at once?

**ls -i** will show you the inode of the file, and there may be a way to find all the other entries that also have that inode (but I can't think of it at the moment).

---

