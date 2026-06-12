---
title: "Driver For My Wireless Card"
date: 2008-10-06
forum: Hardware
---

### Post by CarlosinFL on 2008-10-06
I am wondering what driver Ubuntu has loaded to utilize by Intel 4965agn internal card? Is there a way I can 'cat' the system to verify what is loaded for Ubuntu to function on my wireless card listed above?

---

### Post by nixscripter on 2008-10-07
In the terminal, type:
```
lshw -C network
```

---

