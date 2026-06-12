---
title: "Segmentation fault (core dumped)"
date: 2008-09-10
forum: General Help
---

### Post by milezteg on 2008-09-10
I am running Ubuntu 2.6.20-17.39-386

Today apt-get install stopped working.  Whenever I install anything I get this:

```
# apt-get install nano
Reading package lists... Done
Segmentation fault (core dumped)
```

Aside from reinstalling can anyone suggest how I might troubleshoot this?

---

### Post by milezteg on 2008-09-10
umm anyone?

---

### Post by russlar on 2008-09-10
The only other time I've seen this was when I ran

$ man woman


seriously though, just refresh your package listings

apt-get clean; apt-get update

---

