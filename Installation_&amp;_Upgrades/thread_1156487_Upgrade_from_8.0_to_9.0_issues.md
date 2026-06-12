---
title: "Upgrade from 8.0 to 9.0 issues"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by kmatousek on 2009-05-11
Anybody know what to do here?  I don't use Ubuntu that much and am sure someone has a simple fix for this.

Thanks,


Issue:


After trying to run Update Manager in v. 8.0 in attempt to upgrade to 9.0

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5

System tries to download 52 files and fails, returning the above message.

Update manager then shows system is up-to-date.

---

### Post by zvacet on 2009-05-11
First,you can not skip versions.If you want to upgrade to Jaunty it will look like Hardy>Intrepid>Jaunty.Maybe it is easier to make separate home (if you don´t have one) and do fresh install.For separate home read [this.]("http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html")
If you want to upgrade then in **system>admin>software sources** uncheck all third party repos like that one  witch gives you trouble.

---

