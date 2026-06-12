---
title: "How to remove an unpacked but unconfigured package"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by shredder12 on 2009-09-03
I tried to install some library using apt but jst before installation when it asked me to configure some of the options concerning the library I aborted the installation..
so every time i try to install anything.. the installation takes place nicely .. but the package manager also tries installing that library..
I don't want that to happen.. how do i get rid of it??

---

### Post by slakkie on 2009-09-03
Removing a package can be done by:

aptitude purge <packagename>

---

### Post by stlsaint on 2009-09-03
try 
sudo apt-get remove (package)

---

### Post by mrgnash on 2009-09-03
```
sudo dpkg --configure -a
```

Then just:

```
sudo apt-get remove --purge *name_of_library* && sudo apt-get clean
```

-- to remove it.

---

