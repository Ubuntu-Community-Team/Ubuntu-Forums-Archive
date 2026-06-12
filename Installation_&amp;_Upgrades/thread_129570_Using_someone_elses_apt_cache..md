---
title: "Using someone elses apt cache."
date: 2006-02-14
forum: Installation &amp; Upgrades
---

### Post by Isfria on 2006-02-14
I have a hard drive from an installation of Ubuntu that recently migrated from hoary to breezy. It has about 800 mb of packages in "/var/cache/apt/archives". Is it ok to use this as a repository when upgrading my hoary to breezy?

If so, is this the correct APT line to add to synaptic?

"deb /mnt/nlin/var/cache/apt/archives breezy main restricted breezy-security universe multiverse"

Thanks
Simon

---

### Post by anirban.sam on 2006-02-14
or you can simply copy all the debs to yr ..apt/archive folder

---

### Post by Isfria on 2006-02-14
OIC.

Thankyou.

---

