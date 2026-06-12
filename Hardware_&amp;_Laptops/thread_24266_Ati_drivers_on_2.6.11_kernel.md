---
title: "Ati drivers on 2.6.11 kernel"
date: 2005-04-06
forum: Hardware &amp; Laptops
---

### Post by songochain on 2005-04-06
Hi all! somebody has installed ati drivers using 2.6.11 kernel?? i've read that there is a patch to can use it on a 2.6.11 kernel
Thanks

---

### Post by mirtux on 2005-04-06
Hi,
   you must download the new drivers. Try here [http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html](http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html)
with the package **8.10.19-2 **there is a patch against the kernel 2.6.11

Regards,
MC

---

### Post by Dracontopes on 2005-04-15
I am trying to install the ATi **8.12.10** on the **2.6.11-1-k7** kernel.

I really don;t know what patch I should use to make it work. I got some patches from the rage3d board but they give me errors like this:

```

chris@chris:/lib/modules/fglrx/build_mod $ sudo sh make.sh
gcc: couldn't run 'i486-linux-gcc-3.3.5': Onbekend bestand of map
make.sh: line 60: [: !=: unary operator expected
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.11-1-k7/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.11-1-k7'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.o
/lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.c:57: error: static declaration of '__fgl_agp_try_unsupported' follows non-static declaration
/lib/modules/fglrx/build_mod/2.6.x/agp_backend.h:92: error: previous declaration of '__fgl_agp_try_unsupported' was here
make[2]: *** [/lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.o] Fout 1
make[1]: *** [_module_/lib/modules/fglrx/build_mod/2.6.x] Fout 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.11-1-k7'
make: *** [kmod_build] Fout 2
build failed with return value 2
chris@chris:/lib/modules/fglrx/build_mod $

```

I have the new Breezy updates installed (I know it's risky) and with them came gcc4.0 I think, maybe that is the problem?

**Update:** I uninstalled gcc-4.0 and created a symlink to gcc-3.3. Now, everything works fine again and after two patches the module compiled OKAY and I'm now enjoying a direct renderded workstation :)

---

