---
title: "Need help"
date: 2008-11-11
forum: General Help
---

### Post by yigster on 2008-11-11
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

what is this? I get this error every time I want to open the synaptic package manager..and yes I am new if it is going to solve the problem how do I run it manually??

---

### Post by Patrick793 on 2008-11-11
To fix it, go to Applications > Accessories > Terminal.

Enter this:
```
sudo dpkg --configure -a
```

You should now be able to use Synaptic like normal.

---

### Post by yigster on 2008-11-11
thanks a lot =)

---

