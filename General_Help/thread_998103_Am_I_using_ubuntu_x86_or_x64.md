---
title: "Am I using ubuntu x86 or x64?"
date: 2008-11-30
forum: General Help
---

### Post by djeikyb on 2008-11-30
I forgot which one I installed. Is there a way to check?

cat /proc/cpuinfo reveals I have an x64 processor, but that doesn't help me much.

I expected either /etc/lsb-release or /etc/debian-version to say, but no..

---

### Post by taurus on 2008-11-30
```
uname -a
```
i686 = 32bit
x86_64 = 64bit

---

