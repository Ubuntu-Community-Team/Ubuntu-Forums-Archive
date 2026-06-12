---
title: "What does this mean?"
date: 2008-09-13
forum: General Help
---

### Post by douggiephresh on 2008-09-13
What does this mean? I get this error message sometimes when I check for updates.


GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/hardy/avant-window-navigator/binary-amd64/Packages.gz](http://download.tuxfamily.org/syzygy42/dists/hardy/avant-window-navigator/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/hardy/avant-window-navigator/source/Sources.gz](http://download.tuxfamily.org/syzygy42/dists/hardy/avant-window-navigator/source/Sources.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by y-lee on 2008-09-13
Try
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

to fix it.

I think it means you are missing the latest GPG public key that Apt uses for signature checking for whatever reason.

---

### Post by douggiephresh on 2008-09-13
didnt help

---

### Post by ikt on 2008-09-13
> **douggiephresh said:**
> What does this mean? I get this error message sometimes when I check for updates.


GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/hardy/avant-window-navigator/binary-amd64/Packages.gz](http://download.tuxfamily.org/syzygy42/dists/hardy/avant-window-navigator/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/hardy/avant-window-navigator/source/Sources.gz](http://download.tuxfamily.org/syzygy42/dists/hardy/avant-window-navigator/source/Sources.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

I think Avant Window Navigator moved to Launchpad,

If you know how to edit your sources.list, I would replace the old awn entry with this:

deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main

..

update: I was close.

:

[http://download.tuxfamily.org/syzygy42/index.html](http://download.tuxfamily.org/syzygy42/index.html)

The syzygy42 ubuntu repository has been removed, as I was no longer actively updating anything in the repository. If you are looking for Exaile packages, see the exaile downloads page.([http://www.exaile.org/downloads](http://www.exaile.org/downloads)) If you are looking for my Avant Window Navigator packages, they are now available from my launchpad PPA.([https://launchpad.net/~reacocard-awn/+archive](https://launchpad.net/~reacocard-awn/+archive)) All other packages are, so far as I am aware, not available elsewhere. If you have any questions, please feel free to contact me, Aren Olson, by email as reacocard at gmail dot com, or via IRC as reacocard on freenode. 

Many thanks to the people of Tuxfamily.org, for kindly provding my hosting for nearly two years. This repository would never have happened without them.

---

### Post by douggiephresh on 2008-09-15
so .... what do i have to do?

---

### Post by ikt on 2008-09-16
> **douggiephresh said:**
> so .... what do i have to do?

it depends, are you using Exaile or Avant Window Navigator?

---

