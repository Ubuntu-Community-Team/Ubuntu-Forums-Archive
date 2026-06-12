---
title: "Intel Mobile 915GM video"
date: 2007-02-05
forum: Hardware &amp; Laptops
---

### Post by starling on 2007-02-05
Just installed Ubuntu 6.10 on my laptop (Benq Joybook S53) And I can't get the resolution to change to widescreen (1280x768). I assume this is because video drivers are not installed. It has an intel Mobile 915GM/GMS/910GML Express. I downloaded drivers from intel website but they won't install. I get the following message:

```
Compiling new agpgart module...

ERROR: AGPGART module did not compile

Compiling DRM module...

ERROR: Kernel modules did not compile
```

this is the log file:

```
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/mark/downloads/dripkg/agpgart-2.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/mark/downloads/dripkg/agpgart-2.0/backend.o
/home/mark/downloads/dripkg/agpgart-2.0/backend.c:69: error: conflicting types for ‘agp_backend_acquire’
include/linux/agp_backend.h:105: error: previous declaration of ‘agp_backend_acquire’ was here
/home/mark/downloads/dripkg/agpgart-2.0/backend.c:77: error: conflicting types for ‘agp_backend_acquire’
include/linux/agp_backend.h:105: error: previous declaration of ‘agp_backend_acquire’ was here
/home/mark/downloads/dripkg/agpgart-2.0/backend.c:89: error: conflicting types for ‘agp_backend_release’
include/linux/agp_backend.h:106: error: previous declaration of ‘agp_backend_release’ was here
/home/mark/downloads/dripkg/agpgart-2.0/backend.c:93: error: conflicting types for ‘agp_backend_release’
include/linux/agp_backend.h:106: error: previous declaration of ‘agp_backend_release’ was here
/home/mark/downloads/dripkg/agpgart-2.0/backend.c:220: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘drm_agp’
/home/mark/downloads/dripkg/agpgart-2.0/backend.c: In function ‘agp_add_bridge’:
/home/mark/downloads/dripkg/agpgart-2.0/backend.c:281: warning: ‘inter_module_register’ is deprecated (declared at include/linux/module.h:562)
/home/mark/downloads/dripkg/agpgart-2.0/backend.c:281: error: ‘drm_agp’ undeclared (first use in this function)
/home/mark/downloads/dripkg/agpgart-2.0/backend.c:281: error: (Each undeclared identifier is reported only once
/home/mark/downloads/dripkg/agpgart-2.0/backend.c:281: error: for each function it appears in.)
/home/mark/downloads/dripkg/agpgart-2.0/backend.c: In function ‘agp_remove_bridge’:
/home/mark/downloads/dripkg/agpgart-2.0/backend.c:301: warning: ‘inter_module_unregister’ is deprecated (declared at include/linux/module.h:563)
make[2]: *** [/home/mark/downloads/dripkg/agpgart-2.0/backend.o] Error 1
make[1]: *** [_module_/home/mark/downloads/dripkg/agpgart-2.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [default] Error 2
make -f Makefile.linux DRM_MODULES=gdg.ko modules
make[1]: Entering directory `/home/mark/downloads/dripkg/drm'
make -C /lib/modules/2.6.17-10-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
rm: cannot remove `/home/mark/downloads/dripkg/drm/.tmp_versions/CVS': Is a directory
make[2]: *** [crmodverdir] Error 1
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/mark/downloads/dripkg/drm'
make: *** [gdg.ko] Error 2
```

I have seen this a few other places, something to do with the compiler?
Someone please tell me how to fix it, i really don't care about 3D support, i just want all the pixels i'm entitled to.
It's not just a case of changing xorg.conf, I tried that.

---

### Post by cosborn72 on 2007-02-05
There is a package in Synaptic called 915resolution.  Have you tried installing it?  It magically fixed all my resolution problems on an HP with a intel 945 chip.  I believe it is in one of the standard repositories.

---

### Post by starling on 2007-02-06
I did come across that but did not try it. The problem is not that the drivers don't support the resolution, more that the drivers are not installed and therefore resolution cannot be changed.

I didn't mention this but the in the screen resolution options I can only have 1024x768, regardless of what xorg.conf says.

I will try 915resolution, see if i can break the computer again. Will get back to u.

---

### Post by starling on 2007-02-06
Bloody hell, that worked! do u know how long i spent trying to fix this?! and u just waltz in and put your finger right on it.

Thanks :D

---

