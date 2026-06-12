---
title: "Error message in Synaptic"
date: 2005-11-12
forum: General Help
---

### Post by GabrielWolff on 2005-11-12
Hey.

I try to update all kinds of stuff and always get:

E: /var/cache/apt/archives/libmpcdec3_1.2-1_i386.deb: trying to overwrite `/usr/lib/libmpcdec.so.3.0.0', which is also in package libmpcdec

I can't give the manager any OK or so. If he's so keen to overwrite something - why not?

Waddoeyedo?

I'm trying to remov the package, but without much success. Even while trying to remove it, I get the same message...

---

### Post by Xian on 2005-11-12
What is the output of this command:

```
$ sudo apt-get remove libmpcdec
```

---

