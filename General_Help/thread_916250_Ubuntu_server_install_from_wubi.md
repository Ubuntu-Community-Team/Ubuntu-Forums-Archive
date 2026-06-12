---
title: "Ubuntu server install from wubi"
date: 2008-09-10
forum: General Help
---

### Post by Apocrathia on 2008-09-10
is this possible? I have the server iso already downloaded and sitting in the same folder as wubi.
I was just going to install the server then ```
sudo apt-get install ubuntu-desktop
```
because there doesnt seem to be an apt-get ubuntu-server package >.<
I am trying out a server setup right now and just testing everything with wubi first

---

### Post by Apocrathia on 2008-09-10
Nevermind, I just installed the desktop version and then did:
```
sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server 
```essentially the reverse of what I was trying to do but equally as effective.

---

