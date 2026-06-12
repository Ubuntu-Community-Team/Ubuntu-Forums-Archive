---
title: "ERROR  during down loads please help"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by Wrightda on 2009-01-12
Im new to linux so far so good (just glad im no longer lining the pockets of Mr. Gates) any way i got this error message that told me to run (dpkg --configure -a) went to terminal ran this and recieved (requested operation requires superuser privilage ) anyone know how to fix this??

---

### Post by hangfire on 2009-01-12
> **Wrightda said:**
> Im new to linux so far so good (just glad im no longer lining the pockets of Mr. Gates) any way i got this error message that told me to run (dpkg --configure -a) went to terminal ran this and recieved (requested operation requires superuser privilage ) anyone know how to fix this??

Put sudo in front, to give the command super-user privileges.

```
sudo dpkg --configure -a
```

It will ask for your password (yours, not root's) before continuing.

-HF

---

### Post by Wrightda on 2009-01-12
Awesome thanks hangfire!

---

