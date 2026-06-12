---
title: "how to install lamp in Ubuntu"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by earth_tech on 2009-09-03
hello,
TO install lamp in Ubuntu use following commands:
earth@earth $sudo apt-get install lamp-server

the out put is 
Reading package list............Done
Building Dependency tree
Reading state information .........Done
E: couldn't find lamp server

Again use sudo tasksel
This command run successfully and shows enter password.After enter password it open a box and there has two options. Select desktop edition and press enter.After that enter the following command 
sudo apt-get install libapache2-mod-auth-mysql phpmyadmin and out put is

Reading package list............Done
Building Dependency tree
Reading state information .........Done
E: couldn't find package libapache2 -mod- auth-mysql

Tell me in which way i can solve this problem.

---

### Post by wojox on 2009-09-03
It should be:

```
sudo tasksel install lamp-server
```

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

