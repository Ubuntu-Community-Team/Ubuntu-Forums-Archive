---
title: "Cache and socket errors"
date: 2008-10-15
forum: General Help
---

### Post by hg21 on 2008-10-15
Hi,

When I want to edit a root owned file with kate using sudo I always get the following errors:

Error: "/var/tmp/kdecache-me" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-me" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-me" is owned by uid 1000 instead of uid 0

It doesn't prevent me doing it but I'd like to know how to correct it.

Thanks

---

### Post by hg21 on 2008-10-19
These errors do not occur if I use kdesudo. 

Not quite sure why, man kdesudo merely says it's a frontend for sudo.

---

### Post by Krydahl on 2008-10-19
Looks very similar to this bug:

[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/53845](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/53845)

---

### Post by hg21 on 2008-10-28
Thanks for reply Krydahl (are you who I think you are?). Yes it does look similar I'll use kdesu in future.

---

### Post by Krydahl on 2008-10-28
Could be. :)

---

