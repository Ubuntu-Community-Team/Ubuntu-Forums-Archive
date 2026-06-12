---
title: "aMule (2.0.3): unmet dependencies"
date: 2005-12-22
forum: Installation &amp; Upgrades
---

### Post by Cyhatch on 2005-12-22
I'm trying to install aMule from the [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) repository and I get this:

```
The following packages have unmet dependencies:
amule: Depends: libc6 (>= 2.3.4-1) but 2.3.2.ds1-20ubuntu14 is to be installed
Depends: libcrypto++5.2c2 but it is not installable
Depends: libgcc1 (>= 1:4.0.1) but 1:4.0-0pre6ubuntu7 is to be installed
Depends: libstdc++6 (>= 4.0.1) but it is not going to be installed
Depends: libwxgtk2.6-0 (>= 2.6.1.1.1ubuntu2) but it is not installable
E: Broken packages
```

What are the repositories for these? I'm using Hoary.

---

### Post by kairu0 on 2005-12-22
That repository is only for Breezy. You cannot meet the dependencies because they are too recent for Hoary.

---

### Post by Cyhatch on 2005-12-23
Hum, oh well. :/ Thanks.

---

