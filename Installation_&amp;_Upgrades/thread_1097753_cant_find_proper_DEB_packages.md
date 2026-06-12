---
title: "cant find proper DEB packages"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by emilvv on 2009-03-16
Hello,
I have to install program on UBUNTU server, but i cant find proper DEB files to finish instalation. Here is the screenshot of error messages. Please help me to find missing packages ( DEBs ) or please provide me with a direct link .. 

THANKS

Emil

---

### Post by taurus on 2009-03-16
You need to install all those dependencies first before you can install monitor.

Search for those packages with apt-cache.

```
apt-cache search libsocket*
```

---

