---
title: "updated firefox - still same version"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by drhex on 2009-05-13
My firefox was getting old  - 3.0.8 -  so I exited it and ran (as root)

apt-get install firefox

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  firefox
1 upgraded, 0 newly installed, 0 to remove and 160 not upgraded.
Need to get 69.0kB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 http://se.archive.ubuntu.com intrepid-updates/main firefox 3.0.10+nobinonly-0ubuntu0.8.10.1 [69.0kB]
Fetched 69.0kB in 0s (198kB/s)
(Reading database ... 192822 files and directories currently installed.)
Preparing to replace firefox 3.0.8+nobinonly-0ubuntu0.8.10.2 (using .../firefox_3.0.10+nobinonly-0ubuntu0.8.10.1_all.deb) ...
Unpacking replacement firefox ...
Setting up firefox (3.0.10+nobinonly-0ubuntu0.8.10.1) ...
```

When starting up firefox after this, I expected version 3.0.10, but it is still at 3.0.8 according to the about menu. What more do I need to do?

---

### Post by zvacet on 2009-05-14
```
sudo apt-get update && sudo apt-get upgrade
```

---

