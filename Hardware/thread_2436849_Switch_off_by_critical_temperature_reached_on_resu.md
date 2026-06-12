---
title: "Switch off by critical temperature reached on resume from suspend"
date: 2020-02-14
forum: Hardware
---

### Post by yrtnsky on 2020-02-14
Xubuntu switches off Acer Aspire XC100 on resume from suspend.
In syslog I've found message:
```
thermal thermal_zone0: critical temperature reached (127 C), shutting down
```
which cannot be true, as while working CPU temperature is not higher 60 C.
Is there any way to rectify this? There is no reason to keep PC online contantly which is used only from time to time. Xubuntu is update to latest 18.04.4

---

### Post by Yellow Pasque on 2020-02-14
Maybe work around it like this:
[https://bbs.archlinux.org/viewtopic.php?pid=1538067#p1538067](https://bbs.archlinux.org/viewtopic.php?pid=1538067#p1538067)

---

### Post by yrtnsky on 2020-02-14
> **Yellow Pasque said:**
> Maybe work around it like this:
[https://bbs.archlinux.org/viewtopic.php?pid=1538067#p1538067](https://bbs.archlinux.org/viewtopic.php?pid=1538067#p1538067)

Thank you, this is working. But actually this workaround is looking like a crutch and should be re-applied after any reboot.

---

### Post by Yellow Pasque on 2020-02-14
Yeah, you can run the appropriate command automatically at boot if you are sure your system does not have real thermal issues.
I'm not sure of any way to truly fix the issue other than possibly a BIOS update. Unfortunately, Acer's BIOS changelogs aren't very good.

---

