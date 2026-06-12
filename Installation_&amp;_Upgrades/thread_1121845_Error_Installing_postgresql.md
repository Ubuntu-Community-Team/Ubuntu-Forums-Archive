---
title: "Error Installing postgresql"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by sqadeer on 2009-04-10
While trying to install postgresql, required for LXR, I got the following errors:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/postgresql-8.3/libpq5_8.3.6-0ubuntu8.04_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/postgresql-8.3/libpq5_8.3.6-0ubuntu8.04_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/postgresql-8.3/postgresql-client-8.3_8.3.6-0ubuntu8.04_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/postgresql-8.3/postgresql-client-8.3_8.3.6-0ubuntu8.04_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/postgresql-8.3/postgresql-8.3_8.3.6-0ubuntu8.04_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/postgresql-8.3/postgresql-8.3_8.3.6-0ubuntu8.04_i386.deb)
  404 Not Found [IP: 91.189.88.40 80]

Seems the postgresql packages are not available.

Please help.

Thanks.

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/postgresql-8.3/postgresql_8.3.6-0ubuntu8.04_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/postgresql-8.3/postgresql_8.3.6-0ubuntu8.04_all.deb)
  404 Not Found [IP: 91.189.88.40 80]

---

### Post by Partyboi2 on 2009-04-10
Try updating the package list first from a terminal 
```
sudo apt-get update
```Or hit the reload button in synaptic package manager, then try installing postgresql.  If that does not work then try changing your download server in Software Sources under the first tab.

---

### Post by sqadeer on 2009-04-12
> **Partyboi2 said:**
> Try updating the package list first from a terminal 
```
sudo apt-get update
```Or hit the reload button in synaptic package manager, then try installing postgresql.  If that does not work then try changing your download server in Software Sources under the first tab.

Thanks partyboy2. Updating solved the problem

---

### Post by danielrosenstark on 2009-06-01
Still the right response, even years later... Thanks!

---

### Post by lake54 on 2009-06-01
?

---

