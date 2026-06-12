---
title: "libtiff4 error"
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by inhifistereo on 2009-07-19
I am trying to retrieve an update via the Update Manager:  libtiff4.  When I click "Install Update" I receive the following error:


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/tiff/libtiff4_3.8.2-11ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tiff/libtiff4_3.8.2-11ubuntu0.9.04.1_i386.deb)
  404 Not Found




Any thoughts?

---

### Post by Partyboi2 on 2009-07-19
Hi, try reloading the package list first. Open a terminal (Applications>Accessories>Terminal) and
```
sudo apt-get update
sudo apt-get upgrade
```

---

