---
title: "Cannot find package"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by Digital Ninja on 2009-09-28
While installing flash player through GDebi installer, an error occured saying not all required files could be downloaded. Missing file is:
[http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-dev_3.12.3.1-0ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-dev_3.12.3.1-0ubuntu0.9.04.1_i386.deb)

After browsing the /nss folder, I found a file called libnss3-dev_3.12.3.1-0ubuntu0.9.04.**[COLOR="Red"]2[/COLOR]**_i386.deb

How can I tell Ubuntu to include that file insted, because it's obviously (a new version of) the same file.

---

### Post by Partyboi2 on 2009-09-28
Hi, make sure you update the package list first
```
sudo apt-get update
```
If that does not work try changing your download server under Software Sources (System>Admin>Software Sources)

---

