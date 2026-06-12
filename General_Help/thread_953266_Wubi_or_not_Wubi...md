---
title: "Wubi or not Wubi.."
date: 2008-10-20
forum: General Help
---

### Post by Zenmij on 2008-10-20
[FONT="System"]ok, so I installed Wubi, everythings fine and I like it. SOooo what now? Progress to partitioning and install ubuntu instead?

Why not just keep Wubi? whats teh disadvantage?[/FONT]:)

---

### Post by ago on 2008-10-20
Disadvanatages of wubi installation:

1) No hibernation
2) Disk I/O slightly slower
3) File-system not as robust as in an installation to a dedicated partition (in particular power failures might create problems).

---

### Post by Kamex on 2008-10-20
In addition to the above, what compelled me to use full Linux was the fact that WUBI limits you to 30GB of space, which may be plenty for traditional Linux applications, but when you start installing games on Wine or storing movies, that space fills up pretty fast.

---

### Post by ago on 2008-10-21
Well the limit is intentional, since if you need more than 30GB you should really consider a full installation. That said you can save files directly in the ntfs partition (under /host)...

---

