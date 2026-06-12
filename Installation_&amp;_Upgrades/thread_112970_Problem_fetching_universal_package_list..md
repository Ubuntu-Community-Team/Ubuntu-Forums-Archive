---
title: "Problem fetching universal package list."
date: 2006-01-05
forum: Installation &amp; Upgrades
---

### Post by bananana on 2006-01-05
I get this error when running apt-get update:

Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages [3028kB]
99% [5 Packages gzip 0]
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
  Sub-process gzip returned an error code (1)
Fetched 19.8kB in 14s (1377B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)

I can workaround by:
$ wget [http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)
$ gunzip Packages.gz
$ cp Packages /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages

Anyone else seeing this?

---

### Post by Koobi on 2006-01-05
i had this same error a few days ago. didn't really have enough time to look into it but it eventually sorted itself out and i don't see this error anymore.

---

