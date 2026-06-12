---
title: "Philips Freevents h12y - mmc0 error kills install"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by hawkz on 2009-03-31
Hi all,

I've recently been given a Philips Freevents (Think its twinhead) h12y to play with.

I get

```
[ 121.981706] mmc0: Unknown controller version (16). You may experience problems.
```

And I do experience the problem of the install stopping there. It's the first intel netbook with an SD card reader that's died on ubuntu install.

Any ideas?

---

### Post by hawkz on 2009-04-01
Sorted it,

You need to install from the alternative install disk.

Then you can add in support for mmc and sdhci after.

Yay!

---

### Post by hawkz on 2009-05-23
The explicit way of getting round this, is to boot via a live CD.

Then add:

```
blacklist sdhci-pci
blacklist sdhci
blacklist mmc_core
```

to /etc/modprobe.d/blacklist.conf

---

