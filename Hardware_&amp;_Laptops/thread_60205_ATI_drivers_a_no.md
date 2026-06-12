---
title: "ATI drivers a no"
date: 2005-08-26
forum: Hardware &amp; Laptops
---

### Post by Chuki on 2005-08-26
I'm pretty much a linux newb. I've been tinkering with Ubuntu for a couple months, but just now starting to really getting into it and go through all the hoops and loops so I'm not dependant on windows anymore. Right now I'm trying to get 3d gaming going on my Radeon 9700 pro.

I've followed everysingle little how to I can, and cannot get it install correctly for the life of me.

When I install this is the log file in fglrx-install.log

```
[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agp3.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agpgart_be.o
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:6070: warning: `ati_gart_base' defined but not used
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/i7505-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_stub_putminor':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:498: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:582)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:500: warning: `inter_module_unregister' is deprecated (declared at include/linux/module.h:578)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_stub_register':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:520: warning: `inter_module_register' is deprecated (declared at include/linux/module.h:577)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:551: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:582)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_agp_uninit':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3428: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:582)
include/linux/module.h: At top level:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1921: warning: `deferred_flush' defined but not used
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC3.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC3
  CC      /lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
build succeeded with return value 0
duplicating results into driver repository...
done.
==============================
- creating symlink
- recreating module dependency list
- trying a sample load of the kernel module
done.[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agp3.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agpgart_be.o
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:6070: warning: `ati_gart_base' defined but not used
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/i7505-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_stub_putminor':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:498: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:582)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:500: warning: `inter_module_unregister' is deprecated (declared at include/linux/module.h:578)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_stub_register':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:520: warning: `inter_module_register' is deprecated (declared at include/linux/module.h:577)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:551: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:582)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_agp_uninit':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3428: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:582)
include/linux/module.h: At top level:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1921: warning: `deferred_flush' defined but not used
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC3.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC3
  CC      /lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
build succeeded with return value 0
duplicating results into driver repository...
done.
==============================
- creating symlink
- recreating module dependency list
- trying a sample load of the kernel module
done.
``` 


After this I still just come up with the Mesa drivers. I want my 3d accel :(

---

### Post by s_p_a_r_k_y on 2005-08-26
your trying to build your drivers from the  ati website? Being a newbie (even I do this) I just used synaptic to install them.

Look for fglrx in synaptic. You'll want the kernel one and the xorg package as well. Then you will want to edit the xorg file located in /etc/X11/xorg.conf but you can run the config tool they provide from the console 

fglrxconfig

Run it as root. It creates the file /etc/X11/XFree86-4
but we want /etc/X11/xorg.conf so copy the first file over the 2nd. YOu will probably want to make a backup of your current xorg.conf file before you overwrite it : )

---

### Post by Chuki on 2005-08-26
[QUOTE=s_p_a_r_k_y]your trying to build your drivers from the  ati website? Being a newbie (even I do this) I just used synaptic to install them.

Look for fglrx in synaptic. You'll want the kernel one and the xorg package as well. Then you will want to edit the xorg file located in /etc/X11/xorg.conf but you can run the config tool they provide from the console 

fglrxconfig

Run it as root. It creates the file /etc/X11/XFree86-4
but we want /etc/X11/xorg.conf so copy the first file over the 2nd. YOu will probably want to make a backup of your current xorg.conf file before you overwrite it : )[/QUOTE]
 I just fixed... the fglrx.ko wasn't being replaced by the ati generated one when I ran the installer. A simple copy and now I have working 3d!

---

### Post by s_p_a_r_k_y on 2005-08-26
grreat. Also make sure that you mention fglrx in /etc/modules so it gets loaded upon boot.

---

### Post by Chuki on 2005-08-26
[QUOTE=s_p_a_r_k_y]grreat. Also make sure that you mention fglrx in /etc/modules so it gets loaded upon boot.[/QUOTE]
 is that what they're talking about when creating a symbolic link?

I just upgraded my image to from 386 to k7, and had to reinstall the ati drivers. I just ran the installer then copied over the fglrx.ko file. Like I did before and I got it working again.

---

### Post by s_p_a_r_k_y on 2005-08-26
no, /etc/modules contains modules to be loaded on bootup. SO stick anything in there that should go there...including fglrx if its not there

---

### Post by Septor on 2005-08-29
The fglrx kernel module is automatically loaded by X when it is launched, you do not need it in your /etc/modules files or in any boot-time module load file.

---

