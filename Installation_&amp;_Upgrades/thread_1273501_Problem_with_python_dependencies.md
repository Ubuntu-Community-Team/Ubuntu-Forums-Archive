---
title: "Problem with python dependencies"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by jawad.ssuet on 2009-09-23
Hi,


I am trying to setup one opensource OpenXCAP server but encountered with following problems. What I think there is some problem with python-support as I was facing this problem on Ubuntu 8.04/7.10/9.04/9.10. Can someone help.


The following packages have unmet dependencies:
  openxcap: Depends: python-support (>= 0.90.0) but 0.6.4ubuntu1 is to be installed
            Depends: python-lxml (>= 2.0.7-1) but 1.3.3-1 is to be installed
            Depends: python-twisted-core (>= 8.1.0) but it is not going to be installed
            Depends: python-twisted-web (>= 8.1.0) but it is not going to be installed
            Depends: python-twisted-web2 (>= 8.1.0) but it is not going to be installed
            Depends: python-application (>= 1.1.5) but it is not going to be installed
            Depends: python-gnutls (>= 1.1.8) but it is not going to be installed
            Depends: python-sqlobject but it is not going to be installed

---

### Post by Partyboi2 on 2009-09-24
Hi, can you open a terminal (Applications>Accessories>Terminal) and post your sources.lit please
```
cat /etc/apt/sources.list
```

---

