---
title: "problem installing nfs"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by ub007 on 2008-12-07
I'm trying to set up NFS.

Did
#apt-get update
#apt-get install nfs
Couldn't find package nfs

What am i missing here?

---

### Post by williammanda on 2008-12-07
> **ub007 said:**
> I'm trying to set up NFS.

Did
#apt-get update
#apt-get install nfs
Couldn't find package nfs

What am i missing here?

Use synaptic to install NFS and all the files will be installed.
Thanks

---

### Post by __Ryan__ on 2008-12-07
you just need the correct package.

```
sudo apt-get install nfs-common
```

---

