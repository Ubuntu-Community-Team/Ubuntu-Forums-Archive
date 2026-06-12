---
title: "Separate partition for /var, Debootstrap warning"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by webdevguy on 2008-12-29
Is it possible to install Ubuntu Server 8.04 with /var on a separate partition? When I try I get a red screen:

Debootstrap warning
Warning: Failure trying to run: chroot /target dpkg --force-depends --install var/cache/apt/archives/..etc..

Is the problem a lack of a forward slash in front of "var" in the paths listed in the dpkg options?

---

