---
title: "Using aufs in fstab"
date: 2008-11-15
forum: General Help
---

### Post by noerbo on 2008-11-15
Hello

  What would the following mount command look like in fstab?

mount -t aufs -o br:/mnt/foo1:/mnt/foo2:/mnt/foo3 none /foo

---

### Post by JLarky on 2008-12-12
> **noerbo said:**
> Hello

  What would the following mount command look like in fstab?

mount -t aufs -o br:/mnt/foo1:/mnt/foo2:/mnt/foo3 none /foo


none  /foo  aufs  br:/mnt/foo1:/mnt/foo2:/mnt/foo3 0 0

works fine in my Debian Lenny system

---

