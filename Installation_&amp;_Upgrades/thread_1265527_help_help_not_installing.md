---
title: "help help not installing"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by jadaces on 2009-09-13
hello i am havin some problems here when i type in the terminal 


jadaces@ubuntu:~$ sudo apt-get install lynx



i get this 


E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
jadaces@ubuntu:~$   


could  someone help me correct this problem please thanks in advance

---

### Post by slakkie on 2009-09-13
what about running ... sudo dpkg --configure -a

---

### Post by zvacet on 2009-09-13
**Applications>accessories>terminal>type**

```
sudo dpkg --configure -a
```

---

