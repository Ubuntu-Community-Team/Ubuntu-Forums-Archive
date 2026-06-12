---
title: "[SOLVED] Prob with Update Manager"
date: 2008-12-10
forum: Installation &amp; Upgrades
---

### Post by williebfree on 2008-12-10
Hello Everyone!

I am having trouble loading updates. It has worked in the past, but now I get an error message as follows:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I attempted to run 'dpkg --configure -a' in Terminal and got "need to be superuser" error message. 

This is where I am stuck.  Any suggestions?

Your assistance is greatly appreciated!

---

### Post by Partyboi2 on 2008-12-10
Put sudo in front of dpkg --configure -a to give you admin rights.
```
sudo dpkg --configure -a
```

---

### Post by williebfree on 2008-12-24
It worked! Thanks!

---

### Post by Mario5000 on 2009-01-01
> **Partyboi2 said:**
> Put sudo in front of dpkg --configure -a to give you admin rights.
```
sudo dpkg --configure -a
```


I have the exact same problem, but this didn't help me.  After writing

  sodu dpkg --configure -a

I got

  bash: sodu: command not found

ANY HELP ?

---

### Post by Partyboi2 on 2009-01-01
> **Mario5000 said:**
> I have the exact same problem, but this didn't help me.  After writing

  sodu dpkg --configure -a

I got

  bash: sodu: command not found

ANY HELP ?
Looks like you have typo it is meant to be sudo not sodu
```
sudo dpkg --configure -a
```

---

