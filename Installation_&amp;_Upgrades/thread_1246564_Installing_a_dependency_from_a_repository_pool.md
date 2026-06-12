---
title: "Installing a dependency from a repository pool"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by andreasis on 2009-08-21
Hi,

I'm trying some things out on a Debian lenny install, and I hit a little roadblock:

In order to upgrade to the latest kernel, I wanted to download it from the repository at 
[http://kernel-archive.buildserver.net/debian-kernel/dists/trunk/](http://kernel-archive.buildserver.net/debian-kernel/dists/trunk/)

So I added the following line to the source list
deb [http://kernel-archive.buildserver.net/debian-kernel](http://kernel-archive.buildserver.net/debian-kernel) trunk main

and also added the corresponding key.



Now, a dependency for the 2.6.31 kernel is linux-kbuild-2.6.31 which is available at 
[http://kernel-archive.buildserver.net/debian-kernel/pool/main/l/linux-kbuild-2.6/](http://kernel-archive.buildserver.net/debian-kernel/pool/main/l/linux-kbuild-2.6/)

Is there a way to add this directory to the repositories too so that I could install it through synaptic?


thanks in advance

---

