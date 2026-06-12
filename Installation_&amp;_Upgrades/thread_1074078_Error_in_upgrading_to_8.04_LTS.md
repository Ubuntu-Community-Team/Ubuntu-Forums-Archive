---
title: "Error in upgrading to 8.04 LTS"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by TideMan on 2009-02-18
When I try to upgrade from 7.10 to 8.04 LTS, the upgrade manager stalls in:
"Setting new software channels"
with these messages:
> Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2](http://nz.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2) Hash Sum mismatch
Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.bz2](http://nz.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.bz2) Hash Sum mismatch


It tells me there is probably a network problem and to try again.
I've tried several times and it always stops at this point.

Where do I go from here?

---

### Post by taurus on 2009-02-18
One option is to try another server.

---

### Post by TideMan on 2009-02-18
> One option is to try another server.

Where in the Update Manager do I do that?

---

### Post by taurus on 2009-02-18
You can change to another server in System -> Administration -> Synaptic Package Manager -> Settings -> Repositories.  Make sure you shut down update manager first before you open synaptic.

---

### Post by TideMan on 2009-02-18
Thanks Taurus.
It's hateful for a Kiwi to admit it, but it looks like an Aussie mirror works better.

---

### Post by taurus on 2009-02-18
> **TideMan said:**
> 
It's hateful for a Kiwi to admit it, but it looks like an Aussie mirror works better.

](*,)

---

