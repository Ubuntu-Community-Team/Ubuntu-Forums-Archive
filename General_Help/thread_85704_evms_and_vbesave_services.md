---
title: "evms and vbesave services?"
date: 2005-11-03
forum: General Help
---

### Post by twelvegates on 2005-11-03
In Ubuntu it's similar like in Windows.
There are several services and one seldom knows whether they are really required.

What is *evms*?
What is *vbesave*?

---

### Post by Alexander Kirillov on 2005-11-03
[QUOTE=twelvegates]In Ubuntu it's similar like in Windows.
There are several services and one seldom knows whether they are really required.

What is *evms*?
What is *vbesave*?[/QUOTE]
EVMS: Enterprise Volume Management System
vbesave: saves VESA (video) state - mostly useful for suspend/hibernate 

You can look at the scripts at /etc/init.d/ - if you know shell scripts, you can see what exaclty each of them does.

---

