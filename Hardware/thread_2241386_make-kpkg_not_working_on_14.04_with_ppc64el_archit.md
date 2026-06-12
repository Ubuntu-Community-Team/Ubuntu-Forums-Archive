---
title: "make-kpkg not working on 14.04 with ppc64el architecture"
date: 2014-08-25
forum: Hardware
---

### Post by Douglas_Lehr on 2014-08-25
Hey Everyone,
  I'm sorry for the inconvenience, but there's a problem I've been fighting with for a few days.  Essentially, I patched a kernel to work around a problem on a power8 machine.  What I'm trying to do is build .deb packages with a different name besides "generic"  The best way I've seen online is using the make-kpkg tool.  So the command I've ended up with is 

> apt-get source linux-image-3.16.0-11.16


make-kpkg --arch=ppc64el --initrd --revision=custom kernel_image

The resulting output is 

> debian/ruleset/misc/checks.mk:35: *** Error. I do not know where the kernel image goes to [kimagedest undefined] The usual case for this is that I could not determine which arch or subarch this machine belongs to. Please specify a subarch, and try again..  Stop.
make[1]: Leaving directory `/home/ubuntu/linux-3.16.0'
make: *** [debian/stamp/conf/minimal_debian] Error 2
Failed to create a ./debian directory:  at /usr/bin/make-kpkg line 984.


It doesn't appear that the new architecture is supported in make-kpkg as of yet?  Can someone confirm this?  Please let me know if you need more information on this or not.  Thanks again for everyone's time!

---

