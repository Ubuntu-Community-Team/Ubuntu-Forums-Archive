---
title: "Error updating heimdal libraries"
date: 2006-02-14
forum: Installation &amp; Upgrades
---

### Post by dakebusi on 2006-02-14
I've tried to update my Ubuntu 5.10, to get the new heimdal libraries (libasn1-6-heimdal and libkrb5-17-heimdal), but I get the following error when executing 'apt-get update':

```

Err http://security.ubuntu.com breezy-security/main libasn1-6-heimdal 0.6.3-11ubuntu1.1
  404 Not Found
Err http://security.ubuntu.com breezy-security/main libkrb5-17-heimdal 0.6.3-11ubuntu1.1
  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/h/heimdal/libasn1-6-heimdal_0.6.3-11ubuntu1.1_i386.deb  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/h/heimdal/libkrb5-17-heimdal_0.6.3-11ubuntu1.1_i386.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

It's been giving this error in the last couple of days. Is there anything wrong with these updates?

Thanks!

---

### Post by dakebusi on 2006-02-16
Am I the only one having this problem??????

---

### Post by dakebusi on 2006-02-17
Ok, finally, today (Feb 17) the packages were available and I've been able to install them.

---

