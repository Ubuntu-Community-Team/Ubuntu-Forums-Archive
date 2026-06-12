---
title: "Installing linux-image-2.6.30-020630-generic: linux-generic metapackage ?"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by arielCo on 2009-06-14
I downloaded linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30/") so I can finally run swapon on my Windows swapfile. The description reads:
> You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed. Still, I cannot find the metapackage anywhere, but I understand it's just a list of dependencies. Supposing it hasn't been built, what would those dependencies be? My previous attempt was with dpkg -i for 2.6.29, and then the b44 module did not autoload anymore; maybe this is why.

Thanks and regards,
ariel

---

### Post by jimv on 2009-06-14
If you don't mind running an alpha version, Karmic Koala comes with 2.6.30.

---

