---
title: "Breezy autodected graphic chip and Hoary doesn't"
date: 2005-09-22
forum: Hardware &amp; Laptops
---

### Post by simple on 2005-09-22
well the other day i installed the Breezy preview and it auto-detected and used my computers intel 915gv chipset graphics, i was wondering how, what can i do to get it running with Hoary, use the xorg.conf? or is there more to it.. noticably with Hoary some of the 3D screensavers.. "antispect" in particular ran laggy and slow, at 4fps, with Breezy since it detected and using the chipset, it runs smooth and perfect at 32fps at the same settings.. thanks in advanced for the responses

---

### Post by mlomker on 2005-09-22
Breezy probably includes the driver from [here.](http://dri.freedesktop.org/wiki/Intel)

---

### Post by simple on 2005-09-22
maybe, that wiki is confusing to me, not sure what to get/do..

---

### Post by mlomker on 2005-09-22
lol.  I hear you.  It didn't look like an easy install, but this is the [driver.](http://dri.freedesktop.org/snapshots/i915-20050718-linux.i386.tar.bz2).  It looks like it would have to be compiled and then installed.  It's not as simple as download something in Synaptic.

You can always wait another month.  Breezy will be out and relatively stable soon enough.

---

### Post by simple on 2005-09-26
well, Breezy after updating seems to be completely stable, updating the new kernel and all, but it gets rid of the graphics driver, and doesn't load it as am odule so i try to run that script and get the error 
<quote>make DRM_MODULES=i915.o modules
make[1]: Entering directory `/home/simple/dripkg/drm/linux-core'
make -C /lib/modules/2.6.12-9-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
/home/simple/dripkg/drm/linux-core/Makefile:279: *** CONFIG_X86_CMPXCHG needs to be enabled in the kernel.  Stop.
make[2]: *** [_module_/home/simple/dripkg/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/simple/dripkg/drm/linux-core'
make: *** [i915.o] Error 2
</quote>
will this be able to be fixed, maybe if it's updated in the repositories to enable that, or do i have to compile the kernel myself and enable it?

---

### Post by mlomker on 2005-09-26
> CONFIG_X86_CMPXCHG

Yeah, it sounds like you'd have to compile your own kernel to use that particular driver.

Have you tried **sudo dpkg-reconfigure xserver-xorg**?  Make sure Breezy is using the right driver.

---

### Post by simple on 2005-09-26
actually i just updated to the 686 kernel vs the 386, worked on boot :D thanks a lot for your help man, i thought i'd never get an answer on a driver, and i used that script 4 times now thanks a lot

---

### Post by mlomker on 2005-09-26
So much for you thinking Breezy is stable, eh?  I'm sure it'll turn out great but I'm not going to run it for a while.

---

### Post by simple on 2005-09-26
well before when updating Breezy, it would break xorg. today i did a complete update from a fresh install and i updated the kernel. the original kernel 2.6.12-8-386 was stable with the graphics.. i guess somewhere along the line from 2.6.12-9-386 that option wasn't enabled in the kernel's config when being compiled, but was enabled in 2.6.12-9-686. so yeah i think it's stable, not one problem since the 300+ updated files today which a few days ago completely broke the system

---

