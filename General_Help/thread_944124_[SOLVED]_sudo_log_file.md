---
title: "[SOLVED] sudo log file"
date: 2008-10-11
forum: General Help
---

### Post by sulekha on 2008-10-11
Hi all, 
 
  i have read in a book that the sudo utility logs all commands it  executes. this log can be useful for retracing your steps if you make a mistake  and for system auditing- what is the name of this log file and where it is located ?

NB:- i use ubuntu 8.04

---

### Post by jerome1232 on 2008-10-11
/var/log/auth.log

and the older copies will be

/var/log/auth.log.0

/var/log/auth.log.1.gz
/var/log/auth.log.2.gz 

etc...

---

### Post by sulekha on 2008-10-11
> **jerome1232 said:**
> /var/log/auth.log

and the older copies will be

/var/log/auth.log.0

/var/log/auth.log.1.gz
/var/log/auth.log.2.gz 

etc...

thanx now i am able to find my sudo log files

---

