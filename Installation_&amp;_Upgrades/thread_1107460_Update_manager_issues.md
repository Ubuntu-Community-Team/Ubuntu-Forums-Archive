---
title: "Update manager issues"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by Leviathan433 on 2009-03-26
I've followed the upgrade directions on the Ubuntu main site on but everytime I run the update manager I get the following display

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Any ideas?

I am running 8.04

---

### Post by Rohan Kapoor on 2009-03-26
Is your network connected correctly to everything first?

Also since it's early they may not have uploaded the files yet fully.

---

### Post by Leviathan433 on 2009-03-27
I am all set up on the network. I can get regular updates - it is only when I try to get a distribution upgrade that I receive this message.

---

### Post by Rohan Kapoor on 2009-03-28
> **Leviathan433 said:**
> I am all set up on the network. I can get regular updates - it is only when I try to get a distribution upgrade that I receive this message.
Ah allright, you know before you do a distribution upgrade you need to install all the normal ones, do that then do

```
sudo apt-get dist-upgrade
```

in a terminal which should guide you through your upgrade.

---

