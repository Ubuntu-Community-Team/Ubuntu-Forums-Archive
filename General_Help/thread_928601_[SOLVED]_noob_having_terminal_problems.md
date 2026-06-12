---
title: "[SOLVED] noob having terminal problems"
date: 2008-09-24
forum: General Help
---

### Post by evergreen_p on 2008-09-24
hi guys, i have had linux installed for around a week with no real problems. but i just tried this code in terminal:

sudo apt-get autoclean

and got this error

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


 the same error has come up a few times now from different code

---

### Post by lswest on 2008-09-24
If you read the error messages, they often offer solutions to the problem.  In this case, running dpkg --configure -a as a super user (since you ran the prior commands as such, as it's a system-wide program).  Therefore  ```
sudo dpkg --configure -a
``` will fix your problem.

---

### Post by Dan_Dranath999 on 2008-09-24
type in terminal that code:

```
dpkg --configure -a
```

---

### Post by evergreen_p on 2008-09-24
thanks heaps guys!

---

