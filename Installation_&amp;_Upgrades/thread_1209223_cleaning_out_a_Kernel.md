---
title: "cleaning out a Kernel"
date: 2009-07-10
forum: Installation &amp; Upgrades
---

### Post by bgbnbigben on 2009-07-10
Hey all,

So, after deciding i needed a few speed boosts and could do with culling a bit of unnecessary **** inside the kernel, i headed on over to kernel.org and got the latest kernel. After a bit of tweaking and ****, i got to the point where i went --append-to-version=Benstweak
That was a big mistake.
Now make-kpkg is stuck; i cant make-kpkg clean, i cant build versions with non-capitalised names, etc. etc.
I manually rm -rf'd the directory i had unzipped and tweaked from (which had been moved to /usr/src) and deleted the link, however make-kpkg still compains like an absolute prick whenever i try to do anything
Does anyone have any advice on how i can clean out this failed build?

Just as a reference, the exact error message is as shown (i re-made a kernel with a few different tweaks in it, but it's still complaining about the old version):
```
root@Ben-Ubuntu:/usr/src/linux-2.6.30.1.1337# make-kpkg clean
exec make -f /usr/share/kernel-package/ruleset/minimal.mk clean 
/usr/share/kernel-package/ruleset/misc/version_vars.mk:159: *** Error. 
The Kernel Release version 2.6.30.1BensTweak VERSION=[2], PATCHLEVEL=[6], SUBLEVEL=[30], EXTRAVERSION=[.1], iatv=[], LOCALVERSION=[BensTweak], UTS_RELEASE_VERSION=[], KERNELRELEASE=[]. is not all lowercase.
Since the version ends up in the package name of the kernel image package, this is a Debian policy violation, and the packaging system shall refuse to package the image. .  
Stop.
```Thanks for the help

---

### Post by bgbnbigben on 2009-07-11
Shameless self bump.

Any ideas?

---

### Post by bgbnbigben on 2009-07-11
and another bump....

---

### Post by bgbnbigben on 2009-07-12
c'mon, there's gotta be someone out there who knows what to do! "googling it" has failed me and im desperately trying to compile this new kernel!

---

### Post by bgbnbigben on 2009-07-14
Bump.
Bump.
Bump.

---

### Post by bgbnbigben on 2009-07-15
am i flogging a dead horse here or what.....

---

### Post by bgbnbigben on 2009-07-16
hmm, okay, i think im just going to reformat the partition.
Wasnt what i wanted, but im stuck and im not gonna keep bumping a dead thread.
thanks to those that gave up their time thinking.

---

