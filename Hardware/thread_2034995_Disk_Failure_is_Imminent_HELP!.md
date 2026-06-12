---
title: "Disk Failure is Imminent? HELP!"
date: 2012-07-29
forum: Hardware
---

### Post by joelstitch on 2012-07-29
I am getting this message about my laptops hard drive. Is there any way to fix it? The computer is not that old.

---

### Post by mikewhatever on 2012-07-29
No, no way to fix it. You'll have to replace the hdd.

---

### Post by joelstitch on 2012-07-29
> **mikewhatever said:**
> No, no way to fix it. You'll have to replace the hdd.

Thats what I though. Thanks.

---

### Post by ahallubuntu on 2012-07-29
Look at the actual S.M.A.R.T. attributes that are failing.  If there are a lot of failed sectors or other nasty errors, then yes, you must replace the drive.  But if you have just a few pending sectors, sometimes you can clear them by writing zeros to the whole drive (which will erase everything) and checking S.M.A.R.T. again.  If any pending  sectors are still there, then you must replace the drive for sure.  Other S.M.A.R.T. errors will not go away by writing zeros.

---

