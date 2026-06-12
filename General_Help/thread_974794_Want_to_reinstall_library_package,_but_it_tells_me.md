---
title: "Want to reinstall library package, but it tells me its going to install other stuff"
date: 2008-11-07
forum: General Help
---

### Post by jasper.davidson on 2008-11-07
I think I accidentally messed up one of my installed libraries, so I would like to purge it and then reinstall it. Problem is, when I do:
```
sudo apt-get purge libatk1.0-0
```
Then it tells me that as part of purging that package, it is going to install some other packages, including kde-icons-oxygen; I don't want KDE4 though, so I don't want that kde-icons-oxygen package or any other packages installed. I simply want to purge the libatk1.0-0 library and reinstall it with a freshly downloaded version. Is this possible? Thanks for any help.

---

### Post by cariboo on 2008-11-07
Usually when you purge a package it also wants to remove all it's dependencies. If you are running any KDE apps like K3B or Amarok you still need the icon package.

Jim

---

