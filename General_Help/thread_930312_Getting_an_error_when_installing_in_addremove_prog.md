---
title: "Getting an error when installing in add/remove programs."
date: 2008-09-25
forum: General Help
---

### Post by gnarkilljboy on 2008-09-25
When I go to add or remove a program in Ubuntu, I get this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


What is wrong and how do I fix it?

---

### Post by iaculallad on 2008-09-25
> **gnarkilljboy said:**
> When I go to add or remove a program in Ubuntu, I get this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


What is wrong and how do I fix it?

To fix this, open your terminal (Applications->Accessories->Terminal) and input the command below:

```
sudo dpkg --configure -a
```

---

### Post by gnarkilljboy on 2008-09-25
Thanks!!

---

