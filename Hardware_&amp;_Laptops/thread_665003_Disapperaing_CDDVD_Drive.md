---
title: "Disapperaing CD/DVD Drive"
date: 2008-01-11
forum: Hardware &amp; Laptops
---

### Post by kmac on 2008-01-11
Any idea how to hunt down a DVD/CD drive that used to work just fine but is no longer recognized in either Windows or Ubuntu? It still boots live CD, so it is making communication to the notebook, however I can't find any trace of it in my OS.

Any help would be grand

--Kyle

---

### Post by Yellow Pasque on 2008-01-11
Does lshw pick it up?
```
sudo lshw -class disk
```

---

### Post by kmac on 2008-01-13
No 

--Kyle

---

