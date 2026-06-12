---
title: "/etc/adjtime"
date: 2008-09-02
forum: General Help
---

### Post by sulekha on 2008-09-02
Hi,

 can anyone explain what exactly is the purpose of /etc/adjtime file ?

---

### Post by sameerds on 2008-09-02
It's used by the hwclock utility, provided by the util-linux package.

---

### Post by ibuclaw on 2008-09-02
It stores data that allows your hardware clock to keep in sync with the real time.

At least, it may appear so after having a browse through the hwclock manual...

Regards
Iain

---

