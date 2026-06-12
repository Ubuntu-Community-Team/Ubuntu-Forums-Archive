---
title: "Hash Sum Mismatch"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by derekbuc on 2009-04-23
Upgrading from Ubuntu 8.10 (Intrepid Ibex).

When I run update-manager, and click on the new distribution upgrade button, it downloads for a while, a couple of runs with differing numbers of files and then another window pops up and says,

W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/jaunty/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/jaunty/partner/binary-i386/Packages.gz)  Hash Sum mismatch
, E:Some index files failed to download, they have been ignored, or old ones used instead.

Then the update manager closes. Any idea how to fix it?

---

### Post by yeats on 2009-04-23
you could try commenting out that repository in /etc/apt/sources.list ...

---

### Post by derekbuc on 2009-04-23
I unchecked all the boxes in software sources and that seems to have worked. Thanks guys!

---

