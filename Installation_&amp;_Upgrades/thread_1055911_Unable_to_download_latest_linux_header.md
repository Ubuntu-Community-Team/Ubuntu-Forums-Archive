---
title: "Unable to download latest linux header"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by ravi.rg.gupta on 2009-01-31
Hi,
I am trying to update to linux-headers-2.6.27-11 but the update manager is failing to contact the server. I am getting following error:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.27-11-server_2.6.27-11.26_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.27-11-server_2.6.27-11.26_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.27-11_2.6.27-11.26_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.27-11_2.6.27-11.26_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.27-11-generic_2.6.27-11.26_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.27-11-generic_2.6.27-11.26_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.27-11.26_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.27-11.26_i386.deb)
  404 Not Found


Am I trying to update too early..?


Ravi Gupta

---

### Post by Partyboi2 on 2009-01-31
Try changing your download server in Software Sources (System>Admin>Software Sources) under the first tab.

---

### Post by x33a on 2009-01-31
yesterday i too was facing the same problem. i changed the servers and still got the problem. then in the evening i again ran apt-get update with the main server and it worked!!!

---

### Post by ravi.rg.gupta on 2009-01-31
Seems like the problem was the server itslef. Just updated successfully now. :p

---

