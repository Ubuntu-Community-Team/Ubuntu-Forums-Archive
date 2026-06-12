---
title: "synce-trayicon won't work"
date: 2007-02-03
forum: Hardware &amp; Laptops
---

### Post by cyber_bushi on 2007-02-03
Hi folks,

I'm using my o2 xda mini with ubuntu edgy and most things work out fine with synce, just when i try to start my synce-trayicon i get the following:

```
synce-trayicon: error while loading shared libraries: libgtop-2.0.so.2: cannot open shared object file: No such file or directory
```

libgtop is installed in version 2.7

any clues?

regards,

cb

---

### Post by cyber_bushi on 2007-04-25
sudo ln -s /usr/lib/libgtop-2.0.so.7 /usr/lib/libgtop-2.0.so.2

---

