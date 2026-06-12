---
title: "Kernel error on configure"
date: 2014-01-11
forum: Hardware
---

### Post by linuxcompulsive on 2014-01-11
Hi all,

I got a brand new wacom intuos cth480. I's new so, I have to get the drivers input-wacom-0.20 and compile it over my ubuntu 13.10.
After ./config command i get this message:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/fer/Baixades/input-wacom-0.20.0/missing: Unknown '--is-lightweight' option
Try '/home/fer/Baixades/input-wacom-0.20.0/missing --help' for more information
configure: WARNING: 'missing' script is too old or missing
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc understands -c and -o together... yes
checking for style of include used by make... GNU
checking dependency style of gcc... none
checking for kernel type... Linux
checking for linux-based kernel... yes
checking for kernel source/headers... not found
***
*** WARNING:
*** Unable to guess kernel source directory
***   Looked at /lib/modules/3.8.0-34-generic/source, /lib/modules/3.8.0-34-generic/build,
***     /usr/src/linux, /usr/src/linux-3.8.0-34-generic, and
***     /usr/src/linux-2.6
*** Kernel modules will not be built
***

checking that generated files are newer than configure... done
configure: creating ./config.status
config.status: creating Makefile
config.status: creating 2.6.30/Makefile
config.status: creating 2.6.36/Makefile
config.status: creating 2.6.38/Makefile
config.status: creating 3.7/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
make  all-recursive
make[1]: Entering directory `/home/fer/Baixades/input-wacom-0.20.0'
make[2]: Entering directory `/home/fer/Baixades/input-wacom-0.20.0'
make[2]: Leaving directory `/home/fer/Baixades/input-wacom-0.20.0'
make[1]: Leaving directory `/home/fer/Baixades/input-wacom-0.20.0'

----------------------------------------
  BUILD ENVIRONMENT:
       linux kernel - yes 
      kernel source - no 

We could not find the kernel development environment to build the driver.
Please install the kernel source or the kernel development package and try again.

My distro is Ubuntu 13.10
My Kernel is: uname -r: 3.8.0-34-generic and the system is updated.
I have the kernel and the kernel dev installed... (linux-image-3.8.0-34-generic and linux-image-extra-3.8.0-34-generic)

Could anybody help me? 
Thanks in Advance

Xavi

---

### Post by tomearp on 2014-01-11
To install the kernel headers and kernel source open a terminal:
```
sudo apt-get install linux-headers-$(uname -r) linux-source-3.8.0
```

---

### Post by linuxcompulsive on 2014-01-11
Hi Tomearp,

Thanks for your fast reply.
When I do it, a message error tell me that:
The  «linux-headers-3.8.0-34-generic» and «linux-source-3.8.0» package haven't not installation candidate. 
Looking in synaptic, the only version are 3.11.*
Could you tell me what I am doing wrong?
Thanks again

Linuxcompulsive

---

### Post by howefield on 2014-01-11
> **linuxcompulsive said:**
> Could you tell me what I am doing wrong?

You are using the "wrong" kernel, 13.10 uses the 3.11 series, is this an upgrade from a raring (13.04) installation ?

---

### Post by linuxcompulsive on 2014-01-11
Thanks to both, Howefield's and Tomearp.
I checked the pre-released updates of the Software & Updates. After updated, the kernel has ben changed to 3.11.
The compilation of the new drivers of the wacom run correctly, so now I can use the Wacom tablet.

The whole solution was:
Download the input-wacom-0.20.0 drivers
Unrar and cd to the folder
./autogen.sh --prefix=/usr
sudo cp ./3.7/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
(And finaly rebuild the dependencies)
sudo depmod -a


Linuxcompulsive.

---

