---
title: "[SOLVED] Explain &amp;quot;useradd -r&amp;quot;"
date: 2008-08-05
forum: General Help
---

### Post by devman on 2008-08-05
Could someone please explain to me the difference between a user account created with "-r" and one that is not. The man page was really unhelpful as it didn't even list "-r" as an option! Also I know it creates a "system account" but that doesn't mean anything to me, what makes a system account different from a regular account?

---

### Post by Helios1276 on 2008-08-05
Deleted

---

### Post by koenn on 2008-08-05
> -r
This flag is used to create a system account. That is, a user with a UID lower than the value of UID_MIN defined in /etc/login.defs and whose password does not expire. Note that useradd will not create a home directory for such an user, regardless of the default setting in /etc/login.defs. You have to specify -m option if you want a home directory for a system account to be created. This is an option added by Red Hat 

[http://linux.die.net/man/8/useradd](http://linux.die.net/man/8/useradd)

---

### Post by devman on 2008-08-05
Thanks koenn, I was searching google for an answer on this and was not coming up with much. So thanks for an answer and a new resource for finding them!

---

### Post by koenn on 2008-08-06
> **devman said:**
> Thanks koenn, 
you're welcome

---

