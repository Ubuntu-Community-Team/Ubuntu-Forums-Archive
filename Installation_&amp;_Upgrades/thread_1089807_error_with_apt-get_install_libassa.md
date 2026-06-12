---
title: "error with apt-get install libassa"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by jom2000 on 2009-03-07
When I try to install the libassa package, it fails as follows:

```
sudo apt-get install libassa
Package libassa is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libassa has no installation candidate
```

There are other libassa related packages:
```
libassa           libassa0-dev      libassa3.5-5      libassa3.5-5-dev
libassa0          libassa3.4-0-dev  libassa3.5-5-dbg
``` 

I successfully installed libassa3.5-5. When I install the latest version of Granule, it works, however it leaves an error in the package manager:
```

sudo apt-get check 
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
  granule: Depends: libassa but it is not installable
E: Unmet dependencies. Try using -f.
```

I hope someone can help me with my two questions:
1. How do I install libassa?
2. If I dont install libassa, how do I make the package manager ignore the error when I install the latest version of Granule?

---

### Post by taurus on 2009-03-07
```
sudo apt-get -f install
sudo apt-get update
```

---

### Post by jom2000 on 2009-03-08
> **taurus said:**
> ```
sudo apt-get -f install
sudo apt-get update
```

This does not work because it uninstalls Granule.

---

