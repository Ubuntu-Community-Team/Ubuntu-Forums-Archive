---
title: "install package but skip questions"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by francky_51 on 2009-10-26
Hi,
I would like to know if it's possible to install a package and not being asked to configure it.
For example, I would like to install ldap-utils but not being asked to enter ldap server adress.
I am building ubuntu machines with kickstart and I would like to manage package install and configuration files with cfengine.
Thanks

---

### Post by francky_51 on 2009-10-26
I found the solution :)

DEBIAN_FRONTEND=non-interactive aptitude install ldap-utils

---

