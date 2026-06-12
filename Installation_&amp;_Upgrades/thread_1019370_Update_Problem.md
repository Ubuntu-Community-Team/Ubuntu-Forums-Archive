---
title: "Update Problem"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by Nurhajizah on 2008-12-23
Ubuntu 8.10 newly installed, during update received error message: manually run 'dpkg --configure -a' to correct this problem. How do I do that ??

---

### Post by kostkon on 2008-12-23
> **Nurhajizah said:**
> Ubuntu 8.10 newly installed, during update received error message: manually run 'dpkg --configure -a' to correct this problem. How do I do that ??
Open a terminal (Applications &#8594; Accessories &#8594; Terminal) and give
```
sudo dpkg --configure -a
```
it will ask for a password, give yours.

Then give a
```
sudo apt-get update && sudo apt-get upgrade
```
to finish your updates.

---

