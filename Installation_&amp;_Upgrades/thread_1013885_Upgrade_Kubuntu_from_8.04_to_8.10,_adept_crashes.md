---
title: "Upgrade Kubuntu from 8.04 to 8.10, adept crashes"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by plut0 on 2008-12-17
I'm attempting to upgrade Kubuntu from 8.04 to 8.10 using the following command:

> kdesudo "adept_manager --dist-upgrade-devel"

Adept loads, I click Version Upgrade, a new distribution is found, I click next and Adept crashes.  How do I fix this?  Is there another way of upgrading?

---

### Post by plut0 on 2008-12-18
I was able to upgrade using the Alternate CD.

---

### Post by gjoellee on 2008-12-18
what you could have done is this:
```
sudo apt-get install update-manager
```
when that is installed use this command:
```
update-manager -d
```

---

