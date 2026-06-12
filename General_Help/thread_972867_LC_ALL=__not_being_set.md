---
title: "LC_ALL=  not being set"
date: 2008-11-06
forum: General Help
---

### Post by jrz on 2008-11-06
On a fresh install of Ubuntu 8.10 we were experiencing errors stating that LANGUAGE and LC_ALL were unset and could not default to 'C'.
We changed the default language on the login screen to en_GB and now show LANGUAGE=en_GB, but LC_ALL= is still showing nothing when we run the command locales.

What is LC_ALL and from where does it get it's value set?

---

### Post by Francewhoa on 2009-06-12
An easy way to fix this is installing the following package. It will automatically set the LC_ALL:
```
apt-get install language-pack-en
```

---

