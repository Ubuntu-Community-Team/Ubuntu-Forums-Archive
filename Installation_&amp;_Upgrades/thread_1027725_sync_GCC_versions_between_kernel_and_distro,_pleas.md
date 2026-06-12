---
title: "sync GCC versions between kernel and distro, please"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by derekshaw on 2009-01-01
I've run into a situation with no apparent workaround.

First let me say that I have *a lot* of machines to support, so standardization is paramount.  Custom tweaks are a last-gasp option.

Installing VMWare Server 2 reveals that the kernel was compiled with a different GCC than is provided in the updates to the distribution (hardy 8.04 LTS).

To wit.
the kernel:
Linux version 2.6.24-22-generic (buildd@crested) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Nov 24 19:35:06 UTC 2008

the distribution (after updates):
Package: gcc-4.2 (4.2.4-1ubuntu3)
[http://packages.ubuntu.com/en/hardy-updates/gcc-4.2](http://packages.ubuntu.com/en/hardy-updates/gcc-4.2)

This poses a problem, since I need vmware server for a production machine, and VMWare definitely advises against compiling the vmware modules with a different compiler than the one used for the kernel.

There seems to be no simple way to revert to the original hardy version of GCC.  I suppose a bare-metal re-install and carefully locking the gcc version before applying updates would be feasible.  But the phrases "bush league" and "storing up trouble for the future" come to mind when thinking about such a situation.

Compiling my own kernel strikes me as the ultimate in non-standard solutions. 

Anybody got any more elegant solutions?

And finally, when might the people compiling the kernel start using the same compiler being pushed out with the distro (updates)?

---

