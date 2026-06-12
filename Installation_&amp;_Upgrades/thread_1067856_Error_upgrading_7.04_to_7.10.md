---
title: "Error upgrading 7.04 to 7.10"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by Threnners on 2009-02-12
I'm trying to upgrade 7.04 to 7.10 so I can get back to 8.04 (and not have to deal with video driver drama) and get the following error when trying to upgrade the package:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 8

Do I need to add additional links in sources.list?   I already added the old- entries.

---

### Post by kostkon on 2009-02-12
You could follow this guide [here]("https://help.ubuntu.com/community/GutsyUpgrades").

---

### Post by Threnners on 2009-02-12
I followed those instructions the first time.   I've added the additional lines to sources.list.   This is the error I'm getting while the install for the package is running.

---

### Post by kostkon on 2009-02-12
> **Threnners said:**
> I followed those instructions the first time.   I've added the additional lines to sources.list.   This is the error I'm getting while the install for the package is running.
No, you need to *replace* your current lines in your *sources.list* file with the ones that are given in this guide...

---

### Post by Threnners on 2009-02-12
That didn't work either.   I get the same fail to fetch errors.

I went back, removed all the other links, and replaced everything else with [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com)..... 

Never mind... I think I know what's going on here.

---

### Post by Threnners on 2009-02-12
Never did get it to work.  I got "could not find repository" even when I changed all links to reflect the old-release location.  It might be a good idea to update the instructions though.

I wiped it, found a 7.10 release, and am updating it to 8.04 now.

---

