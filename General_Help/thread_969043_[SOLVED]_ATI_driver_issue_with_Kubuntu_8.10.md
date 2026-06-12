---
title: "[SOLVED] ATI driver issue with Kubuntu 8.10"
date: 2008-11-03
forum: General Help
---

### Post by AlainJLEB on 2008-11-03
Hi there,

After the Kubuntu 8.10 upgrade, I've seen a drop in X performance ... indeed, Xorg has been updated and thus I need a new build/version of ATI's proprietary driver.

After downloading them, I run the installer and it gives an error right after the uncompress, telling the version is not supported ... strange error, but after a search on google this seems normal: there is an issue with ATI's driver linked to the new version of Ubuntu/Xorg

I decide to check the wiki mentioned on the ATI's driver download page ([http://wiki.cchtml.com/](http://wiki.cchtml.com/)), where there is an howto for installing the latest driver depending on which distribution you're using ... Yes, Ubuntu 8.10 is there: [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

Going for "Installing the restricted drivers manually", I have no issue at installing the required packages. Running the ATI installer in buildpkg mode works also with no issue reported. The following steps about checking the modules and blacklisted is also OK.

BUT, when performing the dpkg -i fglrx-kernel-source_8.542-0ubuntu1_i386.deb, I have an issue during the build. The following error is reported in the dkms directory:
```
ATI module generator V 2.0
==========================
initializing...
build_date =Sat Nov 1 23:18:42 CET 2008
uname -a =Linux imac 2.6.27-7-generic #1 SMP Thu Oct 30 04:18:38 UTC 2008 i686 GNU/Linux
uname -s =Linux
uname -m =i686
uname -r =2.6.27-7-generic
uname -v =#1 SMP Thu Oct 30 04:18:38 UTC 2008
uid=0(root) gid=0(root) groups=0(root)
.
drwxr-xr-x 94 root root 24576 2008-10-31 00:57 /usr/include
.
total 610844
drwxr-sr-x  2 root src       4096 2008-09-20 11:27 ati
drwxr-sr-x  3 root src       4096 2008-09-20 11:28 fglrx-8.532
drwxr-xr-x  2 root root      4096 2008-11-01 23:17 fglrx-8.542
lrwxrwxrwx  1 root src         19 2008-11-01 23:14 linux -> linux-source-2.6.27
drwxr-xr-x 20 root root      4096 2008-04-24 20:38 linux-headers-2.6.24-16
drwxr-xr-x  6 root root      4096 2008-04-24 20:38 linux-headers-2.6.24-16-generic
drwxr-xr-x 20 root root      4096 2008-05-03 18:19 linux-headers-2.6.24-17
drwxr-xr-x  6 root root      4096 2008-05-03 18:19 linux-headers-2.6.24-17-generic
drwxr-xr-x 20 root root      4096 2008-06-04 20:26 linux-headers-2.6.24-18
drwxr-xr-x  6 root root      4096 2008-06-04 20:26 linux-headers-2.6.24-18-generic
drwxr-xr-x 20 root root      4096 2008-08-26 08:03 linux-headers-2.6.24-19
drwxr-xr-x  6 root root      4096 2008-08-26 08:03 linux-headers-2.6.24-19-generic
drwxr-xr-x 20 root root      4096 2008-07-29 10:10 linux-headers-2.6.24-20
drwxr-xr-x  6 root root      4096 2008-07-29 10:10 linux-headers-2.6.24-20-generic
drwxr-xr-x 20 root root      4096 2008-10-28 09:07 linux-headers-2.6.24-21
drwxr-xr-x  6 root root      4096 2008-10-28 09:07 linux-headers-2.6.24-21-generic
drwxr-xr-x 22 root root      4096 2008-10-31 00:50 linux-headers-2.6.27-7
drwxr-xr-x  7 root root      4096 2008-10-31 00:50 linux-headers-2.6.27-7-generic
drwxr-xr-x 23 root root      4096 2008-05-01 19:44 linux-source-2.6.24
-rw-r--r--  1 root root 273940480 2008-05-01 19:45 linux-source-2.6.24.tar
-rw-r--r--  1 root root  46896073 2008-10-22 04:58 linux-source-2.6.24.tar.bz2
drwxr-xr-x 25 root root      4096 2008-10-30 06:44 linux-source-2.6.27
-rw-r--r--  1 root root 303953920 2008-10-30 06:45 linux-source-2.6.27.tar
.
file /lib/modules/2.6.27-7-generic/build/include/linux/agp_backend.h says: AGP=1
OsVersion says: SMP=1
file /proc/kallsyms says: SMP=1
file /lib/modules/2.6.27-7-generic/build/include/linux/autoconf.h says: SMP=1
file /lib/modules/2.6.27-7-generic/build/include/linux/autoconf.h says: MODVERSIONS=1
.
CC=gcc
cc_version=
found major but not minor version match for gcc and the ip-library
ls -l ./libfglrx_ip.a
lrwxrwxrwx 1 root root 18 2008-11-01 23:18 ./libfglrx_ip.a -> libfglrx_ip.a.GCC4
.
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
def_vma_api_version=-DFGL_LINUX253P1_VMA_API
 Assuming default VMAP API
 Assuming default munmap API
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/var/lib/dkms/fglrx/8.542/build modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /var/lib/dkms/fglrx/8.542/build/firegl_public.o
/var/lib/dkms/fglrx/8.542/build/firegl_public.c: In function ‘__ke_printk’:
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:1915: warning: format not a string literal and no format arguments
/var/lib/dkms/fglrx/8.542/build/firegl_public.c: In function ‘__ke_flush_cache’:
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:2791: error: too many arguments to function ‘smp_call_function’
/var/lib/dkms/fglrx/8.542/build/firegl_public.c: In function ‘__ke_vm_phys_addr_str’:
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:3522: warning: return makes pointer from integer without a cast
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:3523: warning: return makes pointer from integer without a cast
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:3524: warning: return makes pointer from integer without a cast
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:3526: warning: return makes pointer from integer without a cast
/var/lib/dkms/fglrx/8.542/build/firegl_public.c: In function ‘KCL_enable_pat’:
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:4063: error: too many arguments to function ‘smp_call_function’
/var/lib/dkms/fglrx/8.542/build/firegl_public.c: In function ‘KCL_disable_pat’:
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:4082: error: too many arguments to function ‘smp_call_function’
/var/lib/dkms/fglrx/8.542/build/firegl_public.c: At top level:
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:5774: warning: initialization from incompatible pointer type
/var/lib/dkms/fglrx/8.542/build/firegl_public.c:5800: warning: initialization from incompatible pointer type
make[2]: *** [/var/lib/dkms/fglrx/8.542/build/firegl_public.o] Error 1
make[1]: *** [_module_/var/lib/dkms/fglrx/8.542/build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [kmod_build] Error 2
build failed with return value 2
```

Any idea how ot solve this? Should I wait for a new version of the driver?

---

### Post by AlainJLEB on 2008-11-03
Hi there

I have tried to do the Ubuntu way, and now I'm back with X running, but still not with fglrx :(

When running fglrxinfo or glxinfo, the result is always:
```
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  159 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

```

Any idea on how to have accelerated X ?

---

### Post by AlainJLEB on 2008-11-04
A reboot solved the problem 
```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 2600 XT
OpenGL version string: 2.1.8087 Release

```

... and with full acceleration!

```
fgl_glxgears
Using GLX_SGIX_pbuffer
4439 frames in 5.0 seconds = 887.800 FPS
4503 frames in 5.0 seconds = 900.600 FPS
4867 frames in 5.0 seconds = 973.400 FPS

```

---

### Post by patryk77 on 2008-11-04
I have the same problem.

Could you post the contents of /etc/X11/xorg.conf ?

Maybe it would help me out.

Thanks.


Edit: Oh, I finally fixed it too.

I had commented out the 2.6.27-7 kernel in GRUB because it gave me a black screen. It seems that was caused by the graphics drivers, not the kernel. Oops!

But rebooting with the new kernel finally works :D

---

