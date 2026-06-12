---
title: "Hi what is dpkg ?"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by daie3 on 2009-04-28
hi am new in ubuntu 8.10 i was updating from update manager when it come to the end of install the system crach and now i cant install any thing i get this message 
[COLOR=Red]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/COLOR]
any help ?

---

### Post by Sef on 2009-04-28
Applications > Accessories > Terminal

Copy and paste (or type) this code:

```
sudo dpkg --configure -a
```Enter > type in password > enter

That should fix your problem.

dpkg = debian package.

---

### Post by daie3 on 2009-04-28
Thanks you saved me :)

---

