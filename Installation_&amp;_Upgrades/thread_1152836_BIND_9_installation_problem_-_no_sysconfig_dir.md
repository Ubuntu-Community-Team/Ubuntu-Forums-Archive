---
title: "BIND 9 installation problem - no sysconfig dir"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by TDK800 on 2009-05-08
On Redhat Linux there was the file: /etc/sysconfig/named

For BIND Named process options, where You could set e.g.:
ROOTDIR=/var/named/chroot
ENABLE_ZONE_WRITE=yes


There is not /etc/sysconfig dir on ubuntu. So in what file could I enable zone writes?

Thanks

---

### Post by godjil on 2010-05-06
> **TDK800 said:**
> On Redhat Linux there was the file: /etc/sysconfig/named

For BIND Named process options, where You could set e.g.:
ROOTDIR=/var/named/chroot
ENABLE_ZONE_WRITE=yes


There is not /etc/sysconfig dir on ubuntu. So in what file could I enable zone writes?

Thanks

edit the /etc/apparmor.d/usr.sbin.named
find 
  /etc/bind/** r,

replace
  /etc/bind/** rw,

then restart apparmor

---

