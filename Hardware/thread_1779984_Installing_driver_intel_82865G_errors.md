---
title: "Installing driver intel 82865G errors"
date: 2011-06-11
forum: Hardware
---

### Post by pawan98 on 2011-06-11
Hi i have ubuntu 11.04 and i was trying to install the drivers for my intel 82865G but it didn't work... 

pawan@pawan:~/dripkg$ sudo ./install.sh


DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.sourceforge.net](http://dri.sourceforge.net) ]

==========================================================================

Welcome to the DRI Driver Installation Script

The package you downloaded is for the following driver: 

Driver Name    : gdg
Description    : Intel 830M/845G/852GM/855GM/865G/915G Driver
Architecture   : I386
Build Date     : 20040604
Kernel Module  : gdg

Optional Information

Driver Version      :  
Special Description :  

Press ENTER to continue or CTRL-C to exit.



DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.sourceforge.net](http://dri.sourceforge.net) ]

==========================================================================

Select from the following options:

  1. Install driver (default)
  2. Uninstall driver

Enter reponse [1-2], or CTRL-C to exit
1
get_osname()










DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.sourceforge.net](http://dri.sourceforge.net) ]

==========================================================================

The script will now compile the agpgart module and DRM kernel modules
for your machine.

Press ENTER to continue or CTRL-C to exit.


Compiling new agpgart module...

ERROR: AGPGART module did not compile

Compiling DRM module...

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

pawan@pawan:~/dripkg$ 

Here is the dri.log file.

make -C /lib/modules/2.6.38-8-generic/build SUBDIRS=/home/pawan/dripkg/agpgart-2.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/pawan/dripkg/agpgart-2.0/ali-agp.o
/home/pawan/dripkg/agpgart-2.0/ali-agp.c: In function ‘agp_ali_init’:
/home/pawan/dripkg/agpgart-2.0/ali-agp.c:390:2: error: implicit declaration of function ‘pci_module_init’
make[2]: *** [/home/pawan/dripkg/agpgart-2.0/ali-agp.o] Error 1
make[1]: *** [_module_/home/pawan/dripkg/agpgart-2.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [default] Error 2
make -f Makefile.linux DRM_MODULES=gdg.ko modules
make[1]: Entering directory `/home/pawan/dripkg/drm'
make -C /lib/modules/2.6.38-8-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
rm: cannot remove `/home/pawan/dripkg/drm/.tmp_versions/CVS': Is a directory
make[2]: *** [crmodverdir] Error 1
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/pawan/dripkg/drm'
make: *** [gdg.ko] Error 2

---

### Post by MatesCZ on 2011-08-23
I have exactly the same problem :-( Somewhere I've seen that recompiling kernel with some specific options could help, but I don't really want to do such a complicated thing...

---

