---
title: "Graphic Card issue"
date: 2010-02-10
forum: Hardware
---

### Post by frs89 on 2010-02-10
Hello all:

I'm installing ubuntu 9.10 on my notebook. How do I discover my graphic card? I don't know what it is, The resolution is very bad and in System/Administration/Hardware Drivers there are no proprietary drivers. Please help.

Regards

---

### Post by IcarusR on 2010-02-10
Typing this in a terminal will tell you what graphics card you have 

```
lspci | grep Display
```

---

