---
title: "Cannot open synaptic package manager"
date: 2008-08-02
forum: General Help
---

### Post by xie on 2008-08-02
I get this whenever I try to install anything from the repos  : 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by sayakb on 2008-08-02
Open a terminal (Applications->Accessories->Terminal)
And type in:
```
sudo dpkg --configure -a
```
After the command finishes up, try opening synaptic again.

---

### Post by xie on 2008-08-02
Thank you. I fixed the problem. Synaptic Package Manager works now.

---

