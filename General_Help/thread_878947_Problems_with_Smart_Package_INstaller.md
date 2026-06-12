---
title: "Problems with Smart Package INstaller"
date: 2008-08-03
forum: General Help
---

### Post by colobix on 2008-08-03
I tried to install a package file the other day (li)me wire for ubuntu btw).

And now when i try to install something, all i get is this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I don't really know what to do. I tried to open the smart package installer to fix the roblem but it said that configuration is in readonly mode,
So I don't know what to do.
Are any of you folks familiar withthis problem, please help.

Many thanks.

---

### Post by CatKiller on 2008-08-03
Well, doing what the error message suggests is selcting Applications -> Accessories -> Terminal and typing ```
sudo dpkg --configure -a
```

---

