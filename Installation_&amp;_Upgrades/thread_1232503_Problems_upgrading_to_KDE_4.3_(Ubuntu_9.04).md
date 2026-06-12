---
title: "Problems upgrading to KDE 4.3 (Ubuntu 9.04)"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by Varox1337 on 2009-08-05
Hi all!

I just tried updating my standard KDE version of Ubuntu 9.04 to KDE 4.3 by using the package of Kubuntu Backports PPA

( [http://www.kubuntu.org/news/kde-4.3](http://www.kubuntu.org/news/kde-4.3)  )

The console output of synaptic showed these lines:

```
Setting up kscreensaver (4:4.3.0-0ubuntu1~jaunty1~ppa1) ...
Setting up kdeartwork (4:4.3.0-0ubuntu1~jaunty1~ppa1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Errors were encountered while processing:
 kstars
 kdeedu
```before I got this error message:

```
E: /var/cache/apt/archives/libindi0_0.6-0ubuntu1_i386.deb: trying to overwrite `/usr/bin/indiserver', which is also in package indi
```

If I try to fix the broken package, I get the following message:

```
(Reading database ... 289296 files and directories currently installed.)
Unpacking libindi0 (from .../libindi0_0.6-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libindi0_0.6-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/bin/indiserver', which is also in package indi
Errors were encountered while processing:
 /var/cache/apt/archives/libindi0_0.6-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of kstars:
 kstars depends on libindi0 (>= 0.6); however:
  Package libindi0 is not installed.
dpkg: error processing kstars (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdeedu:
 kdeedu depends on kstars (>= 4:4.3.0-0ubuntu1~jaunty1~ppa2); however:
  Package kstars is not configured yet.
dpkg: error processing kdeedu (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kstars
 kdeedu
```



Did anyone get the same error and knows how to fix it?

Thanks for your help!
 Varox

---

### Post by hggdh on 2009-08-05
The package 'libindi0' has a conflict with 'indi' -- which caused 'libindi0' not to be installed.

'kstars' depends on having 'libindi0' installed; since 'libindi0' failed to install, 'kstars' also failed to upgrade.

'kdeedu' depends on 'kstars'; since 'kstars' failed to install, kdeedu also failed to upgrade.

So. The two last errors are a consequence of the first. The package maintainer will have to change 'libindi0' (or 'indi') packaging to remove the conflict, and rebuild the package(s). After the new versions hit the PPA/-backports, you will be able to fully upgrade.

You should consider opening a bug for the error (if this is from a -backports repository, or talking in #kubuntu-devel (if this is from a PPA).

---

### Post by sachin7 on 2009-08-06
> **hggdh said:**
> The package 'libindi0' has a conflict with 'indi' -- which caused 'libindi0' not to be installed.

'kstars' depends on having 'libindi0' installed; since 'libindi0' failed to install, 'kstars' also failed to upgrade.

'kdeedu' depends on 'kstars'; since 'kstars' failed to install, kdeedu also failed to upgrade.

So. The two last errors are a consequence of the first. The package maintainer will have to change 'libindi0' (or 'indi') packaging to remove the conflict, and rebuild the package(s). After the new versions hit the PPA/-backports, you will be able to fully upgrade.

You should consider opening a bug for the error (if this is from a -backports repository, or talking in #kubuntu-devel (if this is from a PPA).

i also faced this problem

dont know how to solve this

---

### Post by Varox1337 on 2009-08-06
I just reported the bug. You will find more information at the Bug tracking system of Ubuntu:

[https://bugs.launchpad.net/ubuntu/+source/meta-kde/+bug/409814](https://bugs.launchpad.net/ubuntu/+source/meta-kde/+bug/409814)

Varox

---

