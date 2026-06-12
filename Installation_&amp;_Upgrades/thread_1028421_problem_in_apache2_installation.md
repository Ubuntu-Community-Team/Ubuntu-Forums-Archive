---
title: "problem in apache2 installation"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by ravinderreddy37 on 2009-01-02
hi 
i have unistalled apache ,php and mysql 
after that i tried for [http://localhost/](http://localhost/) also it displayed some error message.

but when try to install apache it is displaying the following error 

Package apache2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package apache2 has no installation candidate


i gave sudo apt-get install apache2 

what should i do i m new to ubuntu plez help me

thnks for all.

---

### Post by Partyboi2 on 2009-01-02
Hi,
Open a terminal (Applications>Accessories>Terminal) and try updating first,
```
sudo apt-get update
sudo apt-get install apache2
```
If that does not work can post  your sources list 
```
cat /etc/apt/sources.list
```

---

