---
title: "chroot: permission denied"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by dE_logics on 2009-09-09
I'm trying to chroot into gentoo stage3 tarballs...I mount proc and dev but I get an issue when chrooting - 

```
chroot: cannot run command `/bin/bash': Permission denied
```

I can execute other file in the partition where Gentoo is...so there's no exec permission problem.

Also to ensure this I did - 

```
mount -o exec /dev/sdb1
```

With no go.

---

### Post by dE_logics on 2009-09-09
I successfully changed that error to - 

```
chroot: cannot run command `/bin/bash': Input/output error
```

---

