---
title: "Is this a good practice?"
date: 2008-08-13
forum: General Help
---

### Post by Fixman on 2008-08-13
Is a good practice setting on /etc/fstab, to mount my pen drive with the **sync** option? Has anybody tried it?

---

### Post by dexter.deepak on 2008-08-13
i personally prefer using the sync option for pen drives.
sync means that the data is written to the device as you go on writing...it is not postponed to later times like async (default)
so , with async , if you forget to unmount properly (like typical windows users), then you may lose your data.

---

### Post by Fixman on 2008-08-13
> **dexter.deepak said:**
> i personally prefer using the sync option for pen drives.
sync means that the data is written to the device as you go on writing...it is not postponed to later times like async (default)
so , with async , if you forget to unmount properly (like typical windows users), then you may lose your data.

I knew that, I just wanted to know if there could be any problem with it.

---

