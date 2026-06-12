---
title: "Problem with proxim orinoco silver driver (WLAGS49)"
date: 2008-10-07
forum: Hardware
---

### Post by jjjacer on 2008-10-07
I have download the source code and patch for the wlags49_h1_cs driver, and im having problems compiling it. I need hermesII support for my card

Agere Systems Wireless PC Card Model 0110.

And when i add the flag -DHERMES2 \ to the Makefile it fails to compile. 

I saw there was a similar problem in a previous post [http://ubuntuforums.org/showthread.php?t=304217&page=4]("http://ubuntuforums.org/showthread.php?t=304217&page=4") and it was similar to what pptp was having problems with, he solved it but gave very vague remarks on how he did it.

This is what i get when trying to compile with Hermes2 support

```
[root@IBMLaptop wlags49-h1-cs]# make
make -C /usr/src/linux M=/root/wlags/wlags49-h1-cs modules
make[1]: Entering directory `/usr/src/linux-2.6.26-ARCH'
  CC [M]  /root/wlags/wlags49-h1-cs/wl_profile.o
  CC [M]  /root/wlags/wlags49-h1-cs/wl_sysfs.o
In file included from /root/wlags/wlags49-h1-cs/hcf.h:81,
                 from /root/wlags/wlags49-h1-cs/wl_sysfs.c:16:
/root/wlags/wlags49-h1-cs/include/hcf/hcfcfg.h:786:5: warning: "_BLDTYPE" is not defined
  CC [M]  /root/wlags/wlags49-h1-cs/wl_wext.o
In file included from /root/wlags/wlags49-h1-cs/hcf.h:81,
                 from /root/wlags/wlags49-h1-cs/wl_wext.c:88:
/root/wlags/wlags49-h1-cs/include/hcf/hcfcfg.h:786:5: warning: "_BLDTYPE" is not defined
/root/wlags/wlags49-h1-cs/wl_wext.c: In function 'wl_siwfreq':
/root/wlags/wlags49-h1-cs/wl_wext.c:231: warning: label 'out_unlock' defined but not used
/root/wlags/wlags49-h1-cs/wl_wext.c: In function 'wl_giwaplist':
/root/wlags/wlags49-h1-cs/wl_wext.c:574: error: 'wrq' undeclared (first use in this function)
/root/wlags/wlags49-h1-cs/wl_wext.c:574: error: (Each undeclared identifier is reported only once
/root/wlags/wlags49-h1-cs/wl_wext.c:574: error: for each function it appears in.)
make[2]: *** [/root/wlags/wlags49-h1-cs/wl_wext.o] Error 1
make[1]: *** [_module_/root/wlags/wlags49-h1-cs] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.26-ARCH'
make: *** [default] Error 2

```

But when i remove the flag for Hermes II support it compiles which does me no good since the card wont work without it

```
 
[root@IBMLaptop wlags49-h1-cs]# make
make -C /usr/src/linux M=/root/wlags/wlags49-h1-cs modules
make[1]: Entering directory `/usr/src/linux-2.6.26-ARCH'
  CC [M]  /root/wlags/wlags49-h1-cs/wl_profile.o
  CC [M]  /root/wlags/wlags49-h1-cs/wl_sysfs.o
  CC [M]  /root/wlags/wlags49-h1-cs/wl_wext.o
  CC [M]  /root/wlags/wlags49-h1-cs/wl_priv.o
  CC [M]  /root/wlags/wlags49-h1-cs/wl_main.o
  CC [M]  /root/wlags/wlags49-h1-cs/wl_enc.o
  CC [M]  /root/wlags/wlags49-h1-cs/wl_util.o
  CC [M]  /root/wlags/wlags49-h1-cs/wl_netdev.o
  CC [M]  /root/wlags/wlags49-h1-cs/wl_cs.o
  CC [M]  /root/wlags/wlags49-h1-cs/mmd.o
  CC [M]  /root/wlags/wlags49-h1-cs/hcfio.o
  CC [M]  /root/wlags/wlags49-h1-cs/hcf.o
  CC [M]  /root/wlags/wlags49-h1-cs/dhf.o
  CC [M]  /root/wlags/wlags49-h1-cs/sta_h1.o
  CC [M]  /root/wlags/wlags49-h1-cs/ap_h1.o
  LD [M]  /root/wlags/wlags49-h1-cs/wlags49_h1_cs.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /root/wlags/wlags49-h1-cs/wlags49_h1_cs.mod.o
  LD [M]  /root/wlags/wlags49-h1-cs/wlags49_h1_cs.ko
make[1]: Leaving directory `/usr/src/linux-2.6.26-ARCH'
[root@IBMLaptop wlags49-h1-cs]#

```

So can anyone maybe help me with this or if they know a good driver to try let me know (the card is 0x0156,0x0003 in pccardctl ident) and im using kernel 2.6.26

Proxim Orinoco Silver Model 8421-WD

---

### Post by jjjacer on 2008-10-07
sigh, anyone good at this sorta thing.

---

### Post by jjjacer on 2008-10-12
Bump for Hope?

---

### Post by glennric on 2008-10-30
Have you had any luck with this?  I managed to compile the wlags49 drivers for Intrepid Ibex with the 2.6.27-7-generic kernel.  I don't use Hermes II though.  I am still having some trouble getting it to work though.

I really don't understand why WPA support is not in the orinoco drivers yet.

---

### Post by setag on 2008-10-31
There is new code available from Andrey for both Hermes I and II cards:

[http://groups.google.com/group/linux.kernel/browse_thread/thread/a2f983686defcf97/bd4a5f9eedbde05f]("http://groups.google.com/group/linux.kernel/browse_thread/thread/a2f983686defcf97/bd4a5f9eedbde05f")

jjjacer, it looks like you are using Arch Linux. Please try the latest version of the wl_lkm Package in the AUR.

[http://aur.archlinux.org/packages.php?ID=9637]("http://aur.archlinux.org/packages.php?ID=9637")

You have to edit the PKGBUILD to build the wlags49_h2_cs module.
The Hermes I module works fine here with kernel 2.6.27.

---

### Post by glennric on 2008-11-02
I built the new code from Andrey, but the module won't load.  There is an unknown symbol or invalid parameter error.

---

### Post by glennric on 2008-11-02
I looked a little closer and it has something to do with sysfs.  After trying to load the module dmesg contains "Unknown symbol sysfs_create_group" and "Unknown symbol sysfs_remove_group".

---

### Post by setag on 2008-11-03
I forgot to mention that I wrote a [[COLOR="RoyalBlue"]_patch_[/COLOR]]("http://aur.archlinux.org/packages/wl_lkm/wl_lkm/wlags49.patch"), which simply comments out calls of the functions sysfs_create_group and sysfs_remove_group in wl_sysfs.c.

---

### Post by glennric on 2008-11-03
> **setag said:**
> I forgot to mention that I wrote a [[COLOR="RoyalBlue"]_patch_[/COLOR]]("http://aur.archlinux.org/packages/wl_lkm/wl_lkm/wlags49.patch"), which simply comments out calls of the functions sysfs_create_group and sysfs_remove_group in wl_sysfs.c.

Yeah, that works.  Comparing this code to the code that I had before (see [http://ubuntuforums.org/showthread.php?t=304217&page=10](http://ubuntuforums.org/showthread.php?t=304217&page=10)) I see that they are essentially the same.  This code has been cleaned up a little bit, and there may be some functionality that hasn't been commented out.  Hopefully this works better.  I am encouraged to see that it looks like WPA capabilities are slated to be added to the orinoco drivers in the linux kernel version 2.6.28.

---

