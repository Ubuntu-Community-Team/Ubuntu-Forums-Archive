---
title: "Problems with old Nvidia card installation on Ubuntu FF 7.04"
date: 2007-06-07
forum: Hardware &amp; Laptops
---

### Post by Cashmir on 2007-06-07
Hi, 

I was trying to install my Nvidia Riva TNT 2 64 pro on Ubuntu 7.04 however I've stucked somewhere...

Here is short description what I've done... :
1) I came out of graphic suite x
2) I've checked if I have latest gcc
3) I've installed package - build-essential linux-headers-'uname -r'
4) I've launched installation of Nvidia driver from official page (suitable for my card) and during it I've received information that there is problem with my kernel... Installer was trying to download some updates from Nvidia site but it hadn't succeeded...

5) below you will find log from my installer:

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Jun 6 22:01:34 2007

option status:
license pre-accepted : false
update : false
force update : false
expert : false
uninstall : false
driver info : false
precompiled interfaces : true
no ncurses color : false
query latest version : false
OpenGL header files : true
no questions : false
silent : false
no recursion : false
no backup : false
kernel module only : false
sanity : false
add this kernel : false
no runlevel check : false
no network : false
no ABI note : false
no RPMs : false
no kernel module : false
force SELinux : default
no X server check : false
force tls : (not specified)
X install prefix : (not specified)
X library install path : (not specified)
X module install path : (not specified)
OpenGL install prefix : (not specified)
OpenGL install libdir : (not specified)
utility install prefix : (not specified)
utility install libdir : (not specified)
doc install prefix : (not specified)
kernel name : (not specified)
kernel include path : (not specified)
kernel source path : (not specified)
kernel output path : (not specified)
kernel install path : (not specified)
proc mount point : /proc
ui : (not specified)
tmpdir : /tmp
ftp mirror : [ftp://download.nvidia.com](ftp://download.nvidia.com)
RPM file list : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
ke the installer to attempt to download a kernel interface for your kernel f
rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
this means that the installer will need to compile a kernel interface for
your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.20-16-generic/build'
-> Kernel output path: '/lib/modules/2.6.20-16-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Cleaning kernel module build directory.
executing: 'cd ./usr/src/nv; make clean'...
rm -f -f nv.o nv-vm.o os-agp.o os-interface.o os-registry.o nv.o nv-vm.o os-
agp.o os-interface.o os-registry.o nvidia.mod.o
rm -f -f build-in.o nv-linux.o *.d .*.{cmd,flags}
rm -f -f nvidia.{o,ko,mod.{o,c}} nv_compiler.h *~
rm -f -rf .tmp_versions
-> Building kernel module:
executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.20-16-gener
ic/build SYSOUT=/lib/modules/2.6.20-16-generic/build'...

NVIDIA: calling KBUILD...
make CC=cc KBUILD_VERBOSE=1 -C /lib/modules/2.6.20-16-generic/build SUBDIRS
=/tmp/selfgz23272/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv modules
test -e include/linux/autoconf.h -a -e include/config/auto.conf || ( \
echo; \
echo " ERROR: Kernel configuration is invalid."; \
echo " include/linux/autoconf.h or include/config/auto.conf are mis
sing."; \
echo " Run 'make oldconfig && make prepare' on kernel src to fix it
."; \
echo; \
/bin/false)
mkdir -p /tmp/selfgz23272/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/.tmp_ver
sions
rm -f /tmp/selfgz23272/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/.tmp_versio
ns/*
make -f scripts/Makefile.build obj=/tmp/selfgz23272/NVIDIA-Linux-x86-1.0-718
4-pkg1/usr/src/nv
echo \#define NV_COMPILER \"`cc -v 2>&1 | tail -n 1`\" > /tmp/selfgz23272/NV
IDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/nv_compiler.h
cc -Wp,-MD,/tmp/selfgz23272/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/.nv.
o.d -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERNEL
__ -Iinclude -include include/linux/autoconf.h -Iubuntu/include -Wall -Wun
def -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2
-pipe -msoft-float -mregparm=3 -mpreferred-stack-boundary=2 -march=i586 -mt
une=generic -ffreestanding -maccumulate-outgoing-args -Iinclude/asm-i386/m
ach-default -fomit-frame-pointer -g -fno-stack-protector -Wdeclaration-afte
r-statement -Wno-pointer-sign -I/tmp/selfgz23272/NVIDIA-Linux-x86-1.0-7184-p
kg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subsc
ripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -O -fno-common
-MD -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KER
NEL__ -DMODULE -DNTRM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMO
DULE -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=7184 -DNV_U
NIX -DNV_LINUX -DNV_INT64_OK -DNVCPU_X86 -UDEBUG -U_DEBUG -DNDEBU
G -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_PCI_GET_
CLASS_PRES
ENT -DNV_PM_MESSAGE_T_PRESENT -DNV_PCI_CHOOSE_STATE_PRESENT -DNV_VM_INSERT_P
AGE_PRESENT -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_
VMAP_4_PRESENT -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(
nv)" -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz23272/NVIDIA-Li
nux-x86-1.0-7184-pkg1/usr/src/nv/.tmp_nv.o /tmp/selfgz23272/NVIDIA-Linux-x86
-1.0-7184-pkg1/usr/src/nv/nv.c
In file included from /tmp/selfgz23272/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
c/nv/nv.c:14:
/tmp/selfgz23272/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/nv-linux.h:17:26:
error: linux/config.h: No such file or directory
In file included from include/linux/list.h:8,
from include/linux/wait.h:22,
from include/asm/semaphore.h:41,
from include/linux/sched.h:59,
from include/linux/utsname.h:35,
from /tmp/selfgz23272/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
c/nv/nv-linux.h:19,
from /tmp/selfgz23272/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
c/nv/nv.c:14:
include/linux/prefetch.h: In function ‘prefetch_range’:
include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
rithmetic
/tmp/selfgz23272/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/nv.c: At top leve
l:
/tmp/selfgz23272/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/nv.c:93: warning:
‘kmem_cache_t’ is deprecated
/tmp/selfgz23272/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/nv.c: In function
‘nv_kern_open’:
/tmp/selfgz23272/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/nv.c:1764: warnin
g: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[3]: *** [/tmp/selfgz23272/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/nv.
o] B&#322;&#261;d 1
make[2]: *** [_module_/tmp/selfgz23272/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/sr
c/nv] B&#322;&#261;d 2
NVIDIA: left KBUILD.
nvidia.ko failed to build!
make[1]: *** [module] B&#322;&#261;d 1
make: *** [module] B&#322;&#261;d 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed. Please see the file
'/var/log/nvidia-installer.log' for details. You may find suggestions
on fixing installation problems in the README available on the Linux
driver download page at [www.nvidia.com](www.nvidia.com).

Can somebody help me out ? :) Now it is above my short skills...

---

### Post by netexpert on 2007-06-07
I meet a problem like you.

I have a Nvidia Quardro 2 Pro AGP video card. but i can not close xserver to run thr nvidia installer pack:-)

Thx!

---

### Post by Cashmir on 2007-06-07
[QUOTE=netexpert;2797621]I meet a problem like you.

I have a Nvidia Quardro 2 Pro AGP video card. but i can not close xserver to run thr nvidia installer pack:-)

you are closing the xserver by typing into console:
sudo /etc/init.d/gdm stop (or instead of gdm you can try kdm, xdm etc.)

good luck :)

---

### Post by netexpert on 2007-06-11
> **Cashmir said:**
> [QUOTE=netexpert;2797621]I meet a problem like you.

I have a Nvidia Quardro 2 Pro AGP video card. but i can not close xserver to run thr nvidia installer pack:-)

you are closing the xserver by typing into console:
sudo /etc/init.d/gdm stop (or instead of gdm you can try kdm, xdm etc.)

good luck :)

Thank you for your help. I found maybe my nvidia driver is not match, i will download a new driver.

---

