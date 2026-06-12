---
title: "403 forbidden on repository updates"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by TheParadox2 on 2009-07-15
im new to ubuntu, and i get an error when performing an update:

```
Err http://mn.archive.ubuntu.com jaunty/main Packages
  403 Forbidden
Err http://mn.archive.ubuntu.com jaunty/restricted Packages
  403 Forbidden
Err http://mn.archive.ubuntu.com jaunty/main Sources
  403 Forbidden
Err http://mn.archive.ubuntu.com jaunty/restricted Sources
  403 Forbidden
Err http://mn.archive.ubuntu.com jaunty/universe Packages
  403 Forbidden
Err http://mn.archive.ubuntu.com jaunty/universe Sources
  403 Forbidden
Err http://mn.archive.ubuntu.com jaunty/multiverse Packages
  403 Forbidden
Err http://mn.archive.ubuntu.com jaunty/multiverse Sources
  403 Forbidden
Err http://mn.archive.ubuntu.com jaunty-updates/main Packages
  403 Forbidden
Err http://mn.archive.ubuntu.com jaunty-updates/restricted Packages
  403 Forbidden
Err http://mn.archive.ubuntu.com jaunty-updates/main Sources
  403 Forbidden
Err http://mn.archive.ubuntu.com jaunty-updates/restricted Sources
  403 Forbidden
Err http://mn.archive.ubuntu.com jaunty-updates/universe Packages
  403 Forbidden
Err http://mn.archive.ubuntu.com jaunty-updates/universe Sources
  403 Forbidden
Err http://mn.archive.ubuntu.com jaunty-updates/multiverse Packages
  403 Forbidden
Err http://mn.archive.ubuntu.com jaunty-updates/multiverse Sources
  403 Forbidden
Err http://mn.archive.ubuntu.com jaunty-backports/main Packages
  403 Forbidden
Err http://mn.archive.ubuntu.com jaunty-backports/restricted Packages
  403 Forbidden
Err http://mn.archive.ubuntu.com jaunty-backports/universe Packages
  403 Forbidden
Err http://mn.archive.ubuntu.com jaunty-backports/multiverse Packages
  403 Forbidden
Err http://mn.archive.ubuntu.com jaunty-backports/main Sources
  403 Forbidden
Err http://mn.archive.ubuntu.com jaunty-backports/restricted Sources
  403 Forbidden
Err http://mn.archive.ubuntu.com jaunty-backports/universe Sources
  403 Forbidden
Err http://mn.archive.ubuntu.com jaunty-backports/multiverse Sources
  403 Forbidden
W: Failed to fetch http://mn.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages  403 Forbidden

W: Failed to fetch http://mn.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages  403 Forbidden

W: Failed to fetch http://mn.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources  403 Forbidden

W: Failed to fetch http://mn.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources  403 Forbidden

W: Failed to fetch http://mn.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages  403 Forbidden

W: Failed to fetch http://mn.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources  403 Forbidden

W: Failed to fetch http://mn.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages  403 Forbidden

W: Failed to fetch http://mn.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources  403 Forbidden

W: Failed to fetch http://mn.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages  403 Forbidden

W: Failed to fetch http://mn.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages  403 Forbidden

W: Failed to fetch http://mn.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources  403 Forbidden

W: Failed to fetch http://mn.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources  403 Forbidden

W: Failed to fetch http://mn.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages  403 Forbidden

W: Failed to fetch http://mn.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources  403 Forbidden

W: Failed to fetch http://mn.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages  403 Forbidden

W: Failed to fetch http://mn.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources  403 Forbidden

W: Failed to fetch http://mn.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-i386/Packages  403 Forbidden

W: Failed to fetch http://mn.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-i386/Packages  403 Forbidden

W: Failed to fetch http://mn.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages  403 Forbidden

W: Failed to fetch http://mn.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages  403 Forbidden

W: Failed to fetch http://mn.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/source/Sources  403 Forbidden

W: Failed to fetch http://mn.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/source/Sources  403 Forbidden

W: Failed to fetch http://mn.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/source/Sources  403 Forbidden

W: Failed to fetch http://mn.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/source/Sources  403 Forbidden

E: Some index files failed to download, they have been ignored, or old ones used instead.

```browsing to the address gives the same error... why don't i have access?? no firewall/proxy setup either.

---

### Post by raymondh on 2009-07-15
mirrors could be overloaded. try again later.

Here's an old [link ]("http://ubuntuforums.org/showthread.php?t=186455")from the forums.  Note the various fixes...

1.  Using ftp instead of http
2.  proxy off and editing the .conf file to delete HTTP

etc.

Good luck.

---

