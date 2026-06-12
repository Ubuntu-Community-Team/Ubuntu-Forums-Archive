---
title: "error when update linux-image-2.6.27-7-generic"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by demonhva on 2009-01-01
hi everyone! i have problem when apdate pkg linux-image-2.6.27-7-generic, message output:[http://dooquang.t35.com/Screenshot.png](http://dooquang.t35.com/Screenshot.png) please help me.
thank you!:(

---

### Post by IQRules on 2009-01-02
could be /boot FS full?

Try to check with df on all FS.

---

### Post by demonhva on 2009-01-02
thank you, please explain more detail!:(

---

### Post by IQRules on 2009-01-05
:~/Ubuntu$ df -k /boot
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             35578568  22561744  11209516  67% /

If 100% Use, it is full.

---

