---
title: "Unable to Update?"
date: 2008-08-20
forum: General Help
---

### Post by TreadLight on 2008-08-20
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I got this message when trying to update my Ubuntu. What do I do?

---

### Post by pparks1 on 2008-08-20
I'd do the following

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

---

### Post by cdtech on 2008-08-20
Try typing this in a terminal:
"sudo dpkg --configure -a && sudo apt-get -f install"

---

### Post by spiderbatdad on 2008-08-20
I would do post #3 then post #2 :)

---

### Post by Gondee on 2008-08-20
Try this, and tell us what you get

```
df -H
```

---

