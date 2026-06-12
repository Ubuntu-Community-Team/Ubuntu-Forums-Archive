---
title: "Virutalbox stole my hard disk space :("
date: 2009-07-12
forum: Installation &amp; Upgrades
---

### Post by renbla on 2009-07-12
I installed the default version of virtualbox in hardy(1.5) and had a ubuntu box in it, and later i want to build VB 3.0 so i uninstall the old VB by synaptic. The problem is: the 3gb space i used to install ubuntu wasn't released ??? :(. Even when i deleted the ubuntu.vdi in ~/.Virtualbox, it still not released. I wonder if it keep going like this, how can i gonna live w/ only a few hunred megabytes free :(:(:(

---

### Post by yeaitsdark on 2009-07-12
Unless you simply lost the disk space else where, I suggest maybe the following. 

```
sudo updatedb
locate .vdi
```

Maybe it went somewhere to hide. Could even be hiding in the trash. I think of it because sometimes I run things as root or another user and totally forget.

---

### Post by renbla on 2009-07-13
Srr but no use :(. It can't find any thing :(:(

---

