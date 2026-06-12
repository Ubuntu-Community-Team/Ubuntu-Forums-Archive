---
title: "HP h8-1131sc = impossible to startup"
date: 2012-02-10
forum: Hardware
---

### Post by uhappo on 2012-02-10
HI,

I've managed to install ubuntu via alternate cd, so it's "in".

But there's no way to start ubuntu, everything boots to black screen. Here are some photos I've taken, it's from Ubuntun Finland forum:

[http://forum.ubuntu-fi.org/index.php?topic=41704.0]("http://forum.ubuntu-fi.org/index.php?topic=41704.0")

Any ideas how to fix this problem?

---

### Post by uhappo on 2012-03-05
It was all about inserting
```
nomodeset
```
to boot parameters, installing nvidia-drivers from terminal and then reboot

---

