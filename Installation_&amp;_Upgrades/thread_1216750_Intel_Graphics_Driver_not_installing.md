---
title: "Intel Graphics Driver not installing"
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by Declanthedork on 2009-07-18
I'm running 9.04. I've heard about the "serious problems with Intel Graphics in 9.04." 

What my problem is, is that I can't use Compiz or get a higher res than 800x600. 

I found the driver for my card and started the installer. Everything went swimmingly until the actual installation. It couldn't install. Here's the log file:
```
make -C /lib/modules/2.6.28-13-generic/build SUBDIRS=/home/declan/Documents/code/dripkg/agpgart-2.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
  CC [M]  /home/declan/Documents/code/dripkg/agpgart-2.0/backend.o
/home/declan/Documents/code/dripkg/agpgart-2.0/backend.c:68: error: conflicting types for ‘agp_backend_acquire’
include/linux/agp_backend.h:105: error: previous declaration of ‘agp_backend_acquire’ was here
/home/declan/Documents/code/dripkg/agpgart-2.0/backend.c:77: error: conflicting types for ‘agp_backend_acquire’
include/linux/agp_backend.h:105: error: previous declaration of ‘agp_backend_acquire’ was here
/home/declan/Documents/code/dripkg/agpgart-2.0/backend.c:88: error: conflicting types for ‘agp_backend_release’
include/linux/agp_backend.h:106: error: previous declaration of ‘agp_backend_release’ was here
/home/declan/Documents/code/dripkg/agpgart-2.0/backend.c:93: error: conflicting types for ‘agp_backend_release’
include/linux/agp_backend.h:106: error: previous declaration of ‘agp_backend_release’ was here
/home/declan/Documents/code/dripkg/agpgart-2.0/backend.c:220: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘drm_agp’
/home/declan/Documents/code/dripkg/agpgart-2.0/backend.c: In function ‘agp_add_bridge’:
/home/declan/Documents/code/dripkg/agpgart-2.0/backend.c:281: error: implicit declaration of function ‘inter_module_register’
/home/declan/Documents/code/dripkg/agpgart-2.0/backend.c:281: error: ‘drm_agp’ undeclared (first use in this function)
/home/declan/Documents/code/dripkg/agpgart-2.0/backend.c:281: error: (Each undeclared identifier is reported only once
/home/declan/Documents/code/dripkg/agpgart-2.0/backend.c:281: error: for each function it appears in.)
/home/declan/Documents/code/dripkg/agpgart-2.0/backend.c: In function ‘agp_remove_bridge’:
/home/declan/Documents/code/dripkg/agpgart-2.0/backend.c:301: error: implicit declaration of function ‘inter_module_unregister’
make[2]: *** [/home/declan/Documents/code/dripkg/agpgart-2.0/backend.o] Error 1
make[1]: *** [_module_/home/declan/Documents/code/dripkg/agpgart-2.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
make: *** [default] Error 2
make -f Makefile.linux DRM_MODULES=gdg.ko modules
make[1]: Entering directory `/home/declan/Documents/code/dripkg/drm'
make -C /lib/modules/2.6.28-13-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
rm: cannot remove `/home/declan/Documents/code/dripkg/drm/.tmp_versions/CVS': Is a directory
make[2]: *** [crmodverdir] Error 1
make[2]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/declan/Documents/code/dripkg/drm'
make: *** [gdg.ko] Error 2
```

Thank you so much for your help!

-Declan :popcorn:

---

### Post by coffeecat on 2009-07-18
I can't help you with your compiling problems, but I can point you to a page that might solve your issue and which doesn't involve any compiling at all. You just add a repository and download and install the Intrepid Intel driver.

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

That page also gives a link to this useful page:

[https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance](https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance)

---

