---
title: "completely new to install drivers in Linux, please help"
date: 2008-12-26
forum: Hardware
---

### Post by mslaney on 2008-12-26
I actually work on computers for a living, but I'm completely new to Linux, so please assume I know nothing but will learn quick. I'm trying to install a video driver, specifically Intel 82865G, but I keep getting an error from the install script stating that it can't compile agpgart or the kernel. After reading multiple posts from others, I learned what I think are at least two of the possible causes:

1. I need to have the kernel source package installed.
2. I need to get out of X before running the script.

I think I was able to accomplish the former. I used the package manager to download the source package. (It even said something to the effect of, "this is used for other packages to be able to compile custom flavors.") I also tried a couple variations of closing X (ctrl-alt-bckspc, ctrl-alt-F1 then sudo init 3) However, I'm not convinced either of the methods of exiting X worked, especially since when I type "startx" it gives me an error the server is running, and I the error is still complaining about compiling, not about X.

Please let me know if you have any ideas, suggestions, or best of all solutions on how to fix this.

Thanks,

Matthew



The error is:

Compiling new agpgart module...

ERROR: AGPGART module did not compile

Compiling DRM module...

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.


The referenced log file is:

make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/home/matthew/Desktop/dripkg/agpgart-2.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/matthew/Desktop/dripkg/agpgart-2.0/backend.o
/home/matthew/Desktop/dripkg/agpgart-2.0/backend.c:68: error: conflicting types for ‘agp_backend_acquire’
include/linux/agp_backend.h:105: error: previous declaration of ‘agp_backend_acquire’ was here
/home/matthew/Desktop/dripkg/agpgart-2.0/backend.c:77: error: conflicting types for ‘agp_backend_acquire’
include/linux/agp_backend.h:105: error: previous declaration of ‘agp_backend_acquire’ was here
/home/matthew/Desktop/dripkg/agpgart-2.0/backend.c:88: error: conflicting types for ‘agp_backend_release’
include/linux/agp_backend.h:106: error: previous declaration of ‘agp_backend_release’ was here
/home/matthew/Desktop/dripkg/agpgart-2.0/backend.c:93: error: conflicting types for ‘agp_backend_release’
include/linux/agp_backend.h:106: error: previous declaration of ‘agp_backend_release’ was here
/home/matthew/Desktop/dripkg/agpgart-2.0/backend.c:220: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘drm_agp’
/home/matthew/Desktop/dripkg/agpgart-2.0/backend.c: In function ‘agp_add_bridge’:
/home/matthew/Desktop/dripkg/agpgart-2.0/backend.c:281: error: implicit declaration of function ‘inter_module_register’
/home/matthew/Desktop/dripkg/agpgart-2.0/backend.c:281: error: ‘drm_agp’ undeclared (first use in this function)
/home/matthew/Desktop/dripkg/agpgart-2.0/backend.c:281: error: (Each undeclared identifier is reported only once
/home/matthew/Desktop/dripkg/agpgart-2.0/backend.c:281: error: for each function it appears in.)
/home/matthew/Desktop/dripkg/agpgart-2.0/backend.c: In function ‘agp_remove_bridge’:
/home/matthew/Desktop/dripkg/agpgart-2.0/backend.c:301: error: implicit declaration of function ‘inter_module_unregister’
make[2]: *** [/home/matthew/Desktop/dripkg/agpgart-2.0/backend.o] Error 1
make[1]: *** [_module_/home/matthew/Desktop/dripkg/agpgart-2.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [default] Error 2
make -f Makefile.linux DRM_MODULES=gdg.ko modules
make[1]: Entering directory `/home/matthew/Desktop/dripkg/drm'
make -C /lib/modules/2.6.27-9-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
rm: cannot remove `/home/matthew/Desktop/dripkg/drm/.tmp_versions/CVS': Is a directory
make[2]: *** [crmodverdir] Error 1
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/matthew/Desktop/dripkg/drm'
make: *** [gdg.ko] Error 2

---

### Post by cariboo on 2008-12-26
You may be approaching your problem the wrong way. Most drivers are include with the kernel. If you can boot  to the desktop, but have the wrong resolution. Go to System-->Administration-->Hardware drivers, and see if there is a driver listed for your graphics adapter.

If you can't boot to a desktop, boot in recovery mode and chose xfix at the menu, once xfix has finished,  choose resume to boot to the desktop, then check hardware drivers.

I'm not sure what it akes to get Intel drivers to work in Ubuntu, as my laptop has an ATI video adpater and my desktop has an Nvidia graphics adapter and both just work. I'm waiting on an Intel based motherboard, but it won't be here until after new years, so I'll have to wait a while to join in the fun. :)

Jim

---

### Post by Sef on 2008-12-26
What is your video card?

---

### Post by mslaney on 2008-12-26
I don't think I'm going about it wrong, and it seems as though it shouldn't take that much to make it work. Intel offers the Linux driver on their website and there is an installer script. It appears to try to do what I want it to do when I run the installer.

Nothing is shown in the Sys-Admin-Hardware Drivers dialog.

It's a 82865G chipset which is onboard on an old Compaq d530 I bought on eBay. According to the Intel site, it uses the driver set "i915". See: [http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=1044&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=1044&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go)!

I just noticed also that on that link it says that it includes DRM and agpgart modules. Could it be that it can't find those somehow when it tries to install itself?

Thanks,

Matthew

---

### Post by mslaney on 2009-01-12
So I've downloaded every conceivable package that may be missing to compile the DRM and AGPART, but nothing seems to work. Also, I tried everything I could find on how to get out of X, but it still always gives me an error that X is still running if I try to restart it, so I think this may be a problem also. Any thoughts?

---

### Post by ugm6hr on 2009-01-12
Not wanting to go over previous material, but I'm pretty sure the Intel 82865G driver is open-source, and is included as default.  It is labeled as i915 (I think).

You can install it with:
```
sudo apt-get install xserver-xorg-video-intel
```

I'm pretty certain there is no need to compile it from source.

---

