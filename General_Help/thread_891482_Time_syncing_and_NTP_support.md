---
title: "Time syncing and NTP support"
date: 2008-08-16
forum: General Help
---

### Post by /////// on 2008-08-16
Whenever I try to get Ubuntu to 'keep synchronized with Internet servers' it always asks me to install NTP support even though i've already installed NTP support. If I try to install NTP again, nothing happens and the next time I try to sync with an Internet server, it asks me to install NTP support again.

---

### Post by /////// on 2008-08-16
Bump

---

### Post by fsmithred on 2008-08-17
If you want to set it up to synchronize at regular intervals, some setup is needed. If you just want to synchronize it now, you don't need to install anything extra, just go to a terminal and run:
```
sudo ntpdate ntp.ubuntu.com
```

This might help:
[https://help.ubuntu.com/7.10/server/C/NTP.html](https://help.ubuntu.com/7.10/server/C/NTP.html)

---

