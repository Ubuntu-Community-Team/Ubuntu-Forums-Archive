---
title: "older kernel version"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by miazma on 2009-02-18
Hello,

I've installed Ubuntu 8.10, but I need an older kernel (2.6.24-22-generic), but `apt` doesn't find anything :(

greetings,
Johannes

---

### Post by Martje_001 on 2009-02-18
This is because it is removed from the repository's. Try compiling your own kernel.

---

### Post by miazma on 2009-02-18
Hm, yes that's what I thought, but are no sources available anymore? Furthermore I can't find a 2.6.24-22 kernel at kernel.org

greetings,
Johannes

---

### Post by Martje_001 on 2009-02-18
That's because everything behind the '**-**' are modifications made by the Ubuntu kernel team. Sorry ;)

---

### Post by miazma on 2009-02-18
Isn't it possible to get exactly this kernel from any repository?

---

### Post by miazma on 2009-02-19
Hm, ok maybe I should try a 2.6.24 kernel from kernel.org.

---

### Post by Martje_001 on 2009-02-19
> **miazma said:**
> Isn't it possible to get exactly this kernel from any repository?
It should be possible since the patches are stored... try:
```
apt-get source <package>
```

---

### Post by miazma on 2009-02-19
E: Unable to find a source package for 2.6.24-22*

---

### Post by linux_tech on 2009-02-19
[https://launchpad.net/ubuntu/+source/linux/2.6.24-22.44](https://launchpad.net/ubuntu/+source/linux/2.6.24-22.44)
[https://launchpad.net/ubuntu/+source/linux-backports-modules-2.6.24/2.6.24-22.29](https://launchpad.net/ubuntu/+source/linux-backports-modules-2.6.24/2.6.24-22.29)

---

