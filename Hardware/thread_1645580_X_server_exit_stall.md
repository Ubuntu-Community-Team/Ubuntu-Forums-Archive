---
title: "X server exit stall"
date: 2010-12-14
forum: Hardware
---

### Post by N3TS3cure on 2010-12-14
Hello,

Recently installed Ubuntu 10.10 as a learning project for myself. 
Everything has gone smoothly and I've been able to install programs I needed and everything else.

Except for drivers.

Specifically, the nVIDIA driver for the GT 240.
Whenever I exit out of X server, the computer stalls at "Checking Battery State", which is strange considering I'm on a desktop.

Here is the code I was told stops X server (and thus the last code I use before it stalls)

```
sudo /etc/init.d/gdm stop
```

Any ideas?
Thanks


-EDIT-

Nevermind, I'm an idiot.
They're included in the repositories.

---

