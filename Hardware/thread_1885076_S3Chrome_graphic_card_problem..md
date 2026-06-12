---
title: "S3Chrome graphic card problem."
date: 2011-11-22
forum: Hardware
---

### Post by jonatutu on 2011-11-22
Hi I am new to ubuntu. Please help
Yesterday I install ubuntu 11.10 via wubi. When I boot up everything works fine but soon I 
realize the mouse is flickering.

I went to check the system setting.
[System Info] -Graphics
Driver VESA:
experience standard.

I then tried to install the linux driver for s3chrome.
I followed the steps here. 
[http://drivers.s3graphics.com/en/download/drivers/chrome4x-Linux/Readme.txt](http://drivers.s3graphics.com/en/download/drivers/chrome4x-Linux/Readme.txt)


And this is all I got.

Package vdpau was not found in the pkg-config search path.
Perhaps you should add the directory containing `vdpau.pc'
to the PKG_CONFIG_PATH environment variable
No package 'vdpau' found
Installing/Uninstalling S3G Linux driver built on Xorg 7.3 
Cannot find pre-build S3G kernel driver for kernel 3.0.0-12-generic
Found 01:00.0 VGA compatible controller: S3 Inc. Device 9045 (rev 01) on your system.
Backup /usr/lib/xorg/modules/extensions/libglx.so sucessfully.
cp: cannot stat `/etc/X11/xorg.conf': No such file or directory
Backup /etc/X11/xorg.conf sucessfully.
Install s3g_drv.so sucessfully.
Install libglx.so sucessfully.
Install libGL.so.1.2 sucessfully.
Install s3g_dri.so sucessfully.
Install libva.so.0.28.0 sucessfully
Install s3g_drv_video.so sucessfully.
Error Install libvdpau_s3g.so.1!!! Required Package libvdpau.
Install S3DApp.cfg sucessfully.
mv: cannot stat `/etc/X11/xorg.conf': No such file or directory
ln: accessing `/usr/lib32/libGL.so.1': Not a directory
ln: accessing `/usr/lib32/libGL.so': Not a directory
Install 32bit compatible libGL.so.1.2 sucessfully.
Install 32bit compatible s3g_dri.so sucessfully.
[I]Begin building kernel modules
*.o
*.ko
.depend
.*.flags
.*.d
.*.cmd
*.mod.c
linux
.tmp_versions
*~
Module.*
rm -f linux
ln -s . linux
make -C /lib/modules/3.0.0-12-generic/build  SUBDIRS=`pwd` S3GSRCDIR=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
/home/waikit/Downloads/S3G-InstallPkg-x86_64/s3gdrm/s3g/Makefile:220: *** Only 2.4.x and later kernels are supported (3.0.4).  Stop.
make[1]: *** [_module_/home/waikit/Downloads/S3G-InstallPkg-x86_64/s3gdrm/s3g] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make: *** [modules] Error 2
[I]End building kernel modules
Install s3g.ko failed.

-----------------------------------------------------
Ok I after googling for quite some time I still cant find a solution.
After reading the installation guide again and again I think
this could be the problem why s3g.ko failed.
Anyone can help me understand what it means what is it that i have to do.

------------------------- 1.2 PREPARING YOUR SYSTEM ------------------------- 
S3G Linux driver includes a kernel driver module "s3g.ko"; therefore, you need  to make sure your Linux kernel is set up to support module loading firstly.  The S3 Graphics kernel module has a kernel interface layer that must be  compiled specifically for each kernel. S3 Graphics Linux driver package includes   the source code for this kernel interface layer, as well as precompiled kernel modules for some of the popular Linux distributions.  If the pre-compiled kernel module for your system is not included in the install  package then you need the kernel header files and the necessary kernel source  code installed for the compilation to work. On most Linux distributions, this means that you will need to locate and install the kernel development package.  To show which kernel is currently running on your Linux, run      $uname -r

---

