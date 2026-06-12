---
title: "[SOLVED] Weird error when I try to run updates."
date: 2008-08-25
forum: General Help
---

### Post by morbid_bean on 2008-08-25
Im not sure what I did to mess this up, I think it has to do with when I decided to install a ps1 emulator.....anytime I try to run updates I will get

```
Failed to fetch http://packages.dfreer.org/dists/feisty/main/binary-i386/Packages.gz  302 Found
Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by qstraza on 2008-08-25
well you have a wrong repository mirror added in /etc/apt/sources.list
remove dfreer from it and run apt-get update, i think this should solve it

---

### Post by morbid_bean on 2008-08-25
Sweet! acutually figured it out on my own....just removed that link thing from my software sources and its fixed.:lolflag:

---

### Post by qstraza on 2008-08-25
well thats what i said;)
take a look in /etc/apt/sources.list ;)

gg

---

