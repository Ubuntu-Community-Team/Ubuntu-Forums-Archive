---
title: "Postfix install error"
date: 2009-10-14
forum: Installation &amp; Upgrades
---

### Post by theswiffervac on 2009-10-14
i am trying to install postfix, but whenever i run the command:
> sudo apt-get install postfixThis is what i get
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-numeric libsdl-mixer1.2
Use 'apt-get autoremove' to remove them.
Suggested packages:
  procmail postfix-mysql postfix-pgsql postfix-ldap postfix-pcre sasl2-bin
  resolvconf postfix-cdb
The following NEW packages will be installed:
  postfix
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
am i entering the wrong command? please help.

---

### Post by benjabean1 on 2009-10-19
This has happened to me before too. Try re-booting.

---

