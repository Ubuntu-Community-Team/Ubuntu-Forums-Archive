---
title: "Updating problem"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by matthewlowery on 2009-04-03
jeez another error!
It says 210 updates available ( just installed) so I click and then click Install Updates. It then says:
```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct
 the problem. 
E: _cache->open() failed, please report.

```
and when I run it it says:

```
matthew@ubuntu:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
matthew@ubuntu:~$ 

```
I'm the *only user on the computer!*

---

### Post by boof1988 on 2009-04-03
> **matthewlowery said:**
> jeez another error!
It says 210 updates available ( just installed) so I click and then click Install Updates. It then says:
```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct
 the problem. 
E: _cache->open() failed, please report.

```
and when I run it it says:

```
matthew@ubuntu:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
matthew@ubuntu:~$ 

```
I'm the *only user on the computer!*

I believe you have to run the command with *sudo* (which gives you superuser privileges)...
```
sudo dpkg --configure -a
```

---

### Post by matthewlowery on 2009-04-03
thanks for that, works now.

---

