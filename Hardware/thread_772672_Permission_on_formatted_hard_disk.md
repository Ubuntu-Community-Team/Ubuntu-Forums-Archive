---
title: "Permission on formatted hard disk"
date: 2008-04-28
forum: Hardware
---

### Post by Roman10 on 2008-04-28
I have formatted a secondary hard disk for the first time.

Now, when i try to write something on the disk, appears that I don't have the permission.

Why?

---

### Post by kidders on 2008-04-29
Hi there,

That's standard practice. *You* have to decide who gets to do what on the new filesystem, and until then, root typically gets write access (and it's probably world-readable).

If you're the only user of your computer, **sudo chown roman10: /path/to/mount/point** might be appropriate. You may wish to remove world readability (eg **sudo chmod o-r /path/to/mount/point**). What to do is entirely up to you. That's all assuming you're using a proper (ie non-Microsoft) filesystem (eg Ext3, JFS, and so on). Microsoft filesystems don't support octal permissions, so access control has to be handled differently in those cases.

---

