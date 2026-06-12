---
title: "Generating a configuration file for preseed"
date: 2009-09-25
forum: Installation &amp; Upgrades
---

### Post by louigi600 on 2009-09-25
This is what I get if I do the first part of the documented configuration  file for preseed installation:

```
root@eng-prova:~# debconf-get-selections --installer > preseed.conf
debconf: DbDriver "di_questions": could not open /var/log/installer/cdebconf/questions.dat
root@eng-prova:~# cat preseed.conf 
root@eng-prova:~# ls -l preseed.conf 
-rw-r--r-- 1 root root 0 2009-09-25 13:58 preseed.conf
root@eng-prova:~# ls -l var/log/installer/cdebconf/questions.dat
ls: cannot access var/log/installer/cdebconf/questions.dat: No such file or directory
root@eng-prova:~#
```I've not done anything special to my system other then installing some extra stuff and keeping it up-to-date.
What's going wrong (apart from the file obviously missing) ?

PS: I'm running on a x86_64 ubuntu 9.04 desktop

---

### Post by kadok0520 on 2010-01-06
ubuntu 8.04.3LTS also happened it !

---

### Post by guvnr on 2010-05-05
try:-

debconf-get-selections > debconf
nano debconf

---

