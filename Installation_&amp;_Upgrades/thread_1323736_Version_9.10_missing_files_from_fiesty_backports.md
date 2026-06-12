---
title: "Version 9.10 missing files from fiesty backports"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by jimgeiser on 2009-11-12
I have an error indicator in the panel that when I ask it to get updates I get error messages that I am missing some files:
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.31 80]
Why would I need these old files? and why do they not get added to the update list?

---

### Post by utnubuuser on 2009-11-12
remove the url listings from your /etc/apt/sources.list

---

