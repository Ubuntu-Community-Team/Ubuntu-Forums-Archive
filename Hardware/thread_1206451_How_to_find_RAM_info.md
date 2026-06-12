---
title: "How to find RAM info ?"
date: 2009-07-07
forum: Hardware
---

### Post by credobyte on 2009-07-07
```
lshw
lspci
hardinfo

```

All these commands does not give me the right information - only size/free, etc. info is being displayed !
I need to know what type of RAM I'm currently using ( DDR, DDR2, etc. ).

Any suggestions ?

---

### Post by jerrrys on 2009-07-07
maybe here?

[http://www.google.com/search?q=AmD+Sempron+2600+specs&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=AmD+Sempron+2600+specs&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by damis648 on 2009-07-07
lshw (as root) can almost always tell you want you want to know about your system.

```
sudo lshw -c memory
```

---

### Post by credobyte on 2009-07-07
> **damis648 said:**
> lshw (as root) can almost always tell you want you want to know about your system.

```
sudo lshw -c memory
```
Yes, "almost" always ! lshw shows 1024MB DIMM card ( which is not correct .. I have only 512MB :D ).

---

