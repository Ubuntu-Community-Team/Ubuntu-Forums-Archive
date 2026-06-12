---
title: "security.ubuntu.pool ...brokken link"
date: 2009-09-16
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2009-09-16
I need to use 
[http://security.ubuntu.pool/main/n/nss/libnss3-dev_3.12.3.10Ubuntu0.8.04.1_i386.deb](http://security.ubuntu.pool/main/n/nss/libnss3-dev_3.12.3.10Ubuntu0.8.04.1_i386.deb)
but it is brokken, can some body help me to point to a working server ?

---

### Post by Partyboi2 on 2009-09-17
Looking at the link, it is showing
```
http://security.ubuntu.pool/main/n/nss/
```
where as it should be 
```
http://security.ubuntu.com/ubuntu/pool/main/n/nss/
```
Can you open a terminal and post your sources.list
```
cat /etc/apt/sources.list
```

---

