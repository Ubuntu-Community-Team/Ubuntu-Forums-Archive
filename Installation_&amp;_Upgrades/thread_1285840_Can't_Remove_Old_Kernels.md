---
title: "Can't Remove Old Kernels"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by giacomo.c on 2009-10-08
Ok, I've been having this issue for a while.  a couple months ago, I compiled a custom kernel with 2.6.29.4, and everything had been going fine until I decided to clear out my old kernels via ubuntu tweek.  when it tried to remove these packages:  linux-headers-2.6.28-14, linux-restricted-modules-2.6.28-14-generic, and linux-restricted-modules-2.6.28-15-generic it started giving me troubles.  now, if i try to run an apt-get install -f, it tries to remove those leftovers but gives me these errors:

```
(Reading database ... 190330 files and directories currently installed.)
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

i've been searching the forums and google, looking for a solution, but i have not been very successful.  if anyone can help, please do.  everytime i try to install something via apt-get, I have to deal with this problem and usually leave these things marked since they can't be removed.

---

