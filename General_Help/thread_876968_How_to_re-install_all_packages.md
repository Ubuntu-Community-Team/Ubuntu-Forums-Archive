---
title: "How to re-install all packages?"
date: 2008-08-01
forum: General Help
---

### Post by bs0d on 2008-08-01
Is it possible to reinstall all packages? 
In recovery mode with 
apt-get install ubuntu-desktop
or 
apt-get install --reinstall ubuntu-desktop

how to force apt to download and reinstall all already installed packages?

Ubuntu has no possibility to check integrity of installed files with simple command like rpm -V, so I try to recover many machines by reinstalling base system in recovery mode.

Ideas?

---

### Post by bs0d on 2008-08-01
> check integrity of installed files with simple command like rpm -V


```
debsums | grep -v "OK$"
```

---

### Post by zvacet on 2008-08-01
```
dpkg --get-selections > installed-software
```

you will find text file in your home directory.To download and reinstall 

```
dpkg --set-selections < installed-software
dselect
```

---

