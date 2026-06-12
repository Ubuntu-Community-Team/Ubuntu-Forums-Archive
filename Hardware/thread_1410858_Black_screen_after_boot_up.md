---
title: "Black screen after boot up"
date: 2010-02-19
forum: Hardware
---

### Post by quanganht on 2010-02-19
I removed my ATI graphics card, and removed the appropriate driver, like this:
```
cd /usr/share/ati
sudo sh ./fglrx-uninstall
```
After that, I can not boot Ubuntu anymore. It just goes blank after the Ubuntu icon disappear.

---

### Post by buzzmandt on 2010-02-19
check xorg (/etc/X11/xorg.conf) it might still be trying to use the ati driver no longer installed.

---

### Post by quanganht on 2010-02-19
The file xorg.conf is just empty

---

