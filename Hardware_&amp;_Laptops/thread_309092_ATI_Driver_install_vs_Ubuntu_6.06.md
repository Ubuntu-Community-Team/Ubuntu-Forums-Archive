---
title: "ATI Driver install vs Ubuntu 6.06"
date: 2006-11-29
forum: Hardware &amp; Laptops
---

### Post by Fier on 2006-11-29
sudo nano /etc/default/linux-restricted-modules-common
DISABLED_MODULES=&#8221;fglrx&#8221;

apt-get update
apt-get install module-assistant build-essential
apt-get install fakeroot dh-make debconf libstdc++5 

apt-get install gcc-4.0-base
rm /usr/bin/gcc
ln -s /usr/bin/gcc-4.0 /usr/bin/gcc


chmod +x ati-driver-installer-8.31.5-x86.x86_64.run
./ati-driver-installer-8.31.5-x86.x86_64.run &#8211;buildpkg Ubuntu/6.06

Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.31.5...............................
................................................................................
................................................................................
................................................................................
................................................................................
................................................................................
.....................................................
==================================================
ATI Technologies Linux Driver Installer/Packager
==================================================
Generating package: Ubuntu/6.06
cp: cannot stat `/home/[MUSOR]/ati/fglrx-install/x690/*': No such file or directory
cp: cannot stat `/home/[MUSOR]/ati/fglrx-install/arch/x86/*': No such file or directory
cp: cannot stat `/home/[MUSOR]/ati/fglrx-install/common/*': No such file or directory
cp: cannot stat `/home/[MUSOR]/ati/fglrx-install/packages/Ubuntu/overlay/dapper/*': No such file or directory
/tmp/fglrx.YHnN4B /home/[MUSOR]/ati/fglrx-install
Package build failed!
...

What to do?:-k

---

### Post by pay on 2006-11-29
```
sudo apt-get update
sudo apt-get install module-assistant build-essential 
sudo apt-get install fakeroot dh-make debconf libstdc++5 linux-headers-$(uname -r)
``````
bash ati-driver-installer-8.31.5-x86.x86_64.run --buildpkg Ubuntu/dapper
``````
sudo dpkg -i xorg-driver-fglrx_8.31.5-1_i386.deb
sudo dpkg -i fglrx-kernel-source_8.31.5-1_i386.deb
sudo dpkg -i fglrx-control_88.31.5-1_i386.deb
```

---

### Post by Fier on 2006-11-29
...

---

### Post by Fier on 2006-11-29
I have:

xorg-driver-fglrx 8.25.18+2.6.15.12-1
fglrx-control 8.25.18+2.6.15.12-1
fglrx-kernel-source 8.25.18+2.6.15.12-1

Are they too old?

---

### Post by pay on 2006-11-29
You are trying to install the new driver so you need to install files. You can continue with the old driver if you wish.

---

### Post by Fier on 2006-11-30
**root@exe:/home/[MUSOR]/ati# dpkg -i xorg-driver-fglrx_8.31.5-1_i386.deb**

(Reading database ... 189294 files and directories currently installed.)
Preparing to replace xorg-driver-fglrx 8.31.5-1 (using xorg-driver-fglrx_8.31.5-1_i386.deb) ...
Stopping atieventsd: No /usr/sbin/atieventsd found running; none killed.
done.
Unpacking replacement xorg-driver-fglrx ...
Setting up xorg-driver-fglrx (8.31.5-1) ...
Starting atieventsd: done.

**root@exe:/home/[MUSOR]/ati# dpkg -i fglrx-control_8.31.5-1_i386.deb**

(Reading database ... 189294 files and directories currently installed.)
Preparing to replace fglrx-control 8.31.5-1 (using fglrx-control_8.31.5-1_i386.deb) ...
Unpacking replacement fglrx-control ...
Setting up fglrx-control (8.31.5-1) ...

[COLOR="DarkRed"]** (process:4469): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed
[/COLOR]
**root@exe:/home/[MUSOR]/ati# dpkg -i fglrx-kernel-source_8.31.5-1_i386.deb**

(Reading database ... 189294 files and directories currently installed.)
Preparing to replace fglrx-kernel-source 8.31.5-1 (using fglrx-kernel-source_8.31.5-1_i386.deb) ...
Unpacking replacement fglrx-kernel-source ...
Setting up fglrx-kernel-source (8.31.5-1) ...


[B]root@exe:/home/[MUSOR]/ati# sh ati-driver-installer-8.31.5-x86.x86_64.run --buildpkg Ubuntu/6.06
[/B]
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.31.5....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Generating package: Ubuntu/6.06
cp: cannot stat `/home/[MUSOR]/ati/fglrx-install/x690/*': No such file or directory
cp: cannot stat `/home/[MUSOR]/ati/fglrx-install/arch/x86/*': No such file or directory
cp: cannot stat `/home/[MUSOR]/ati/fglrx-install/common/*': No such file or directory
cp: cannot stat `/home/[MUSOR]/ati/fglrx-install/packages/Ubuntu/overlay/dapper/*': No such file or directory
/tmp/fglrx.nKVkTi /home/[MUSOR]/ati/fglrx-install
Package build failed!
Package build utility output:
dpkg-buildpackage: source package is fglrx-installer
dpkg-buildpackage: source version is 8.31.5-1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://www.ati.com/support/driver.html>
dpkg-buildpackage: host architecture i386
 debian/rules build
echo "Using architecture: i386"
Using architecture: i386
if [ -f /tmp/fglrx.nKVkTi/debian/control.template ]; then \
                cat /tmp/fglrx.nKVkTi/debian/control.template > /tmp/fglrx.nKVkTi/debian/control; \
        fi
for i in preinst postinst postrm atieventsd.init; do \
          if [ -f /tmp/fglrx.nKVkTi/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/dapper/" /tmp/fglrx.nKVkTi/debian/driver.$i > \
              /tmp/fglrx.nKVkTi/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx.nKVkTi/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/X11R6/lib/modules|" -e "s|#XMODDIR32#|usr/X11R6/lib32/modules|" \
            /tmp/fglrx.nKVkTi/debian/10fglrx.template > /tmp/fglrx.nKVkTi/debian/10fglrx; \
        fi
if [ -f /tmp/fglrx.nKVkTi/debian/fglrx.default ]; then \
          mv /tmp/fglrx.nKVkTi/debian/fglrx.default /tmp/fglrx.nKVkTi/debian/fglrx; \
        fi
dh_testdir
dh_testdir
# move licenses away from binary dir
if [ ! -d usr/share/doc/fglrx ]; then \
                mkdir -p usr/share/doc/fglrx; \
                mv usr/X11R6/bin/LICENSE.* usr/share/doc/fglrx; \
        fi
mv: cannot stat `usr/X11R6/bin/LICENSE.*': No such file or directory
make: *** [usr/X11R6] Error 1
/home/[MUSOR]/ati/fglrx-install
Removing temporary directory: fglrx-install

:neutral:

---

### Post by Fier on 2006-11-30
[B]sudo sh /home/\[MUSOR\]/ati/ati-driver-installer-8.31.5-x86.x86_64.run
[/B]

fglrx-install.log
> [Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
 Assuming default VMAP API
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.15-27-386/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-27-386'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:456: warning: initialisation from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2277: warning: 'deferred_flush' defined but not used
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC4.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC4
  CC      /lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-27-386'
build succeeded with return value 0
duplicating results into driver repository...
done.
==============================
- recreating module dependency list
- trying a sample load of the kernel modules
failed.
[Error] Kernel Module : Failed to install compiled kernel module - please consult readme.


do xorg.conf
> Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Driver		"fglrx"
#	Driver		"ati"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID		"PCI:1:0:0"
	
EndSection


reboot and look at xorg.log
> (II) fglrx(0): Serial No: HMCWB03857
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000008
(II) fglrx(0): POWERplay version 3.  1 power state available:
(II) fglrx(0):   1. 324/189MHz @ 50Hz [enable load balancing]

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x86) [0x80b4ab6]
1: [0xffffe420]
2: /usr/lib/xorg/modules/drivers/fglrx_drv.so [0xb72e73ed]
3: /usr/lib/xorg/modules/drivers/fglrx_drv.so(DALCWDDE+0x1a2) [0xb72e5a92]
4: /usr/lib/xorg/modules/drivers/fglrx_drv.so(swlDalHelperAddCustomizeMode+0x1a4) [0xb7281bf4]
5: /usr/lib/xorg/modules/drivers/fglrx_drv.so(atiddxPreInit+0xb21) [0xb7259d51]
6: /usr/bin/X(InitOutput+0x9b8) [0x809e3f8]
7: /usr/bin/X(main+0x292) [0x806deee]
8: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7d34ea2]
9: /usr/bin/X(FontFileCompleteXLFD+0x85) [0x806d641]

Fatal server error:
Caught signal 11.  Server aborting



---

### Post by Fier on 2006-11-30
up

---

### Post by Fier on 2006-12-02
Installed drivers in graphical mode. With success message in the end/

after rebooot

> fi@exe:~$ glxgears -printfps
658 frames in 5.0 seconds = 131.565 FPS
664 frames in 5.0 seconds = 132.792 FPS
651 frames in 5.0 seconds = 130.088 FPS

I think that it must be about 1532.792 FPS

> fi@exe:~$ modprobe fglrx
fi@exe:~$    

> fi@exe:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.6174 (8.31.5)



> fi@exe:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample,
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.6174 (8.31.5)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array,
.......
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
......


---

