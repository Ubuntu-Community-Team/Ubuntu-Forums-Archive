---
title: "I cannot add a programm"
date: 2008-09-25
forum: General Help
---

### Post by fantasmas on 2008-09-25
Hello everyone, i m new user in ubuntu and i have a problem.I m trying to add a programm and the system giving me an error like :

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Can i have some help please?

---

### Post by WWSmith36 on 2008-09-25
Open a terminal from Applications-> Accessories-> Terminal and type this code

```
sudo dpkg --configure -a
```

You will be prompted for your password, you will see nothing when you type it.  Hit enter.

Hope that helps

---

