---
title: "Error with linux headers"
date: 2009-10-03
forum: Installation &amp; Upgrades
---

### Post by giacomo.c on 2009-10-03
I should start off by saying I have a custom kernel of 2.6.29 that I compiled a few months ago to help with jack and realtime recording and whatnot.

This has never been a problem until now.  Ubuntu tried to do a "partial upgrade" and came back with a lot of errors.  Now, whenever I run synaptic it gives me this, no matter what I'm trying to install:

```

E: linux-headers-2.6.28-14: cannot remove file `/usr/src/linux-headers-2.6.28-14/arch/xtensa/platforms/iss/Makefile'
E: linux-restricted-modules-2.6.28-14-generic: failed to delete `/lib/linux-restricted-modules/2.6.28-14-generic/wl/wl.mod.o.dpkg-tmp'
E: linux-restricted-modules-2.6.28-15-generic: failed to delete `/usr/share/linux-restricted-modules/2.6.28-15-generic/modules.alias.override/ath_pci.dpkg-tmp'
```

also, it seems to have an openoffice.org-common upgrade waiting, and this will not upgrade due to these kernel-esque errors.

I'm not that linux savy, at least not enough to figure this out.  any ideas/help would be greatly appreciated.

---

### Post by giacomo.c on 2009-10-06
i tried to do an apt-get install -f sorta thing to see if it might fix it, but alas, it did not.  It did spit this out at me:

```

(Reading database ... 190144 files and directories currently installed.)
Removing linux-headers-2.6.28-14 ...
dpkg: error processing linux-headers-2.6.28-14 (--remove):
 cannot remove file `/usr/src/linux-headers-2.6.28-14/arch/xtensa/platforms/iss/Makefile': Not a directory
Removing linux-restricted-modules-2.6.28-14-generic ...
dpkg: error processing linux-restricted-modules-2.6.28-14-generic (--remove):
 failed to delete `/lib/linux-restricted-modules/2.6.28-14-generic/wl/wl.mod.o.dpkg-tmp': Stale NFS file handle
Removing linux-restricted-modules-2.6.28-15-generic ...
dpkg: error processing linux-restricted-modules-2.6.28-15-generic (--remove):
 failed to delete `/usr/share/linux-restricted-modules/2.6.28-15-generic/modules.alias.override/ath_pci.dpkg-tmp': Stale NFS file handle
Errors were encountered while processing:
 linux-headers-2.6.28-14
 linux-restricted-modules-2.6.28-14-generic
 linux-restricted-modules-2.6.28-15-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

should i just start manually deleting that crap?

---

