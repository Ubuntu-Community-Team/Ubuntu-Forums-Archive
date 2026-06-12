---
title: "stddef.h not present in /usr/include"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by f00k3r on 2009-08-03
Hi,

   I recently installed Ubuntu Gutsy (need the older version) from a CD and after the installation, I did :
```
sudo apt-get install build-essential
```
I even tried 
```
sudo apt-get install libc6-dev
```

but /usr/include doesn't contain the file: stddef.h 
What should I do?

Regards,
Bharat.

---

### Post by puttux on 2009-09-03
This baffled me for sometime... I finally found it :)

/usr/lib/gcc/i486-linux-gnu/4.2/include

Vaivaswatha,

---

