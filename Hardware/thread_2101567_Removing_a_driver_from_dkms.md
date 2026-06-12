---
title: "Removing a driver from dkms"
date: 2013-01-05
forum: Hardware
---

### Post by rezaf on 2013-01-05
Hi, I'm trying to remove the dahdi driver module from dkms, but even after doing "dkms remove" or "dkms uninstall" (even with both commands) can't remove it and when I do "dkms status" the terminal give "dahdi, 2.5.0.1+dfsg-1ubuntu2: added" response. how can I remove the driver from dkms completely ??

```
root@r-VirtualBox:/home/r# sudo dkms remove -m dahdi -v 2.5.0.1+dfsg-1ubuntu2 --all
root@r-VirtualBox:/home/r# dkms status
dahdi, 2.5.0.1+dfsg-1ubuntu2: added
```

Thanks.

---

### Post by rezaf on 2013-01-05
any suggestion ?

---

