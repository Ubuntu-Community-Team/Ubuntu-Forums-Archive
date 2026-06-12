---
title: "[SOLVED] List fuse-mounted filesystems?"
date: 2008-09-02
forum: General Help
---

### Post by mopi on 2008-09-02
Is there a way to list the filesystems mounted by fuse?
I want to make a backup script that should run only if an encfs filesystem has been mounted. 

There must be a way but I can't find it. 

Thanks in advance.

---

### Post by Vivaldi Gloria on 2008-09-02
I think

```
mount
``` 

shows all mounted systems including the fuse ones. Try

```
mount | grep encfs
```

---

### Post by mopi on 2008-09-02
You're right. Thank you.

---

### Post by Vivaldi Gloria on 2008-09-02
> **mopi said:**
> You're right. Thank you.

You're welcome. Have fun.

---

