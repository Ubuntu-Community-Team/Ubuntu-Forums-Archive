---
title: "Problem with suspend in gutsy (ntos_wq/0)"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by varunbhalerao on 2007-10-24
Hi all !
I updated my dell inspiron e1505 updated to gutsy, and the suspend feature which wasnt working for me in feisty is now working. But, when the system resumes after suspend, a process called "ntos_wq/0" takes up most of the cpu - and cant even be killed by root.

from top:
```
 
PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3148 root      10  -5     0    0    0 S 45.3  0.0   6:33.84 ntos_wq/0    

```

kill -9 3148 makes no difference to this process... :confused:

Any tips ?

On another note, i have a swap of 512 MB but 1gb ram - anyway i can enable hibernation ?

-- Varun

---

### Post by lavinog on 2007-12-06
are you still having this problem?
what kind of wireless card do you have?
have you tried disabling your wireless and seeing if the problem persists?

---

