---
title: "System setup"
date: 2008-10-21
forum: General Help
---

### Post by arijitm on 2008-10-21
Heii, guyz..
i need to setup a system with two apache web servers one linked with PHP4 another linked with PHP5 and one mysql server.
.
how can i do that??

---

### Post by shawnrgr on 2008-10-22
```
sudo apt-get install apache2 php4 php5
sudo /etc/init.d/apache2 restart
```

i don't know if you can have 2 apache services running on the same box

---

