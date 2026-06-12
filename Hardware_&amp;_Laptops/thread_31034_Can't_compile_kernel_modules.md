---
title: "Can't compile kernel modules"
date: 2005-05-01
forum: Hardware &amp; Laptops
---

### Post by BeBoxer on 2005-05-01
Well, I can compile kernel modules but I can't actually use them. I'm trying to build a working version of the usb/serial/keyspan module (i.e., one which includes the firmware).

I'm currently running 2.6.10-5-686. I tried grabbing stock 2.6.10 sources, copying my config file from /boot, adding the needed options to it, and doing a 'make modules'. But what I end up with is a keyspan.ko file which spits a bunch of errors like this when I try to load it:

keyspan: disagrees about version of symbol ezusb_set_reset

So I tweaked the Makefile to set EXTRAVERSION so that it would match, but that didn't help either. Same error. I've used 'strings keyspan.ko | grep ver' to verify that the 'vermagic' of the new file is identical to the installed one. 

I tried turning off 'Source checksum for all modules' and rebuilding, but that didn't help either. I figured it would, since the source for kernel/module.c indicates it's the CRC value which triggers that particular error.

There is of course no source package for my kernel. I installed package 'linux-source-2.6.10' and untarred the resulting tarball, and am trying the build there. But to be honest I'm not optimistic because that tarball has no EXTRAVERSION set in the Makefile so it doesn't appear to be the actual source used to build the 2.6.10-5-686 kernel.

So how do I go about building a module which actually works with the 2.6.10-5-686 kernel? Or do I have to replace the entire kernel and module packages with homebuilt ones just to get one particular device? For that matter, why isn't this module in the restricted module package? The license is certainly less ornerous than the NVidia one for example.

---

### Post by BeBoxer on 2005-05-01
[QUOTE=BeBoxer]
There is of course no source package for my kernel. I installed package 'linux-source-2.6.10' and untarred the resulting tarball, and am trying the build there. But to be honest I'm not optimistic because that tarball has no EXTRAVERSION set in the Makefile so it doesn't appear to be the actual source used to build the 2.6.10-5-686 kernel.

[/QUOTE]

Now I'm really confused. That actually worked. I un-tarred the linux-source-2.6.10.tar.bz2 that resulted from installing the linux-source-2.6.10 package. Copied my /boot/config-2.6.10-5-686 to .config. Copied drivers/usb/serial/Kconfig from a kernel.org tree. A quick 'make menuconfig' to activate the firmware option and then a 'make module' resulted in a working module.

What I can't figure out is what exactly the kernel is checking when it decides on the "version" of a module? Both the vermagic and srcversion fields in the new module are different from the stock one. Anybody know? I would think that any 2.6.10 module would work with any 2.6.10 kernel, but they obviously don't. Weird.

---

### Post by az on 2005-05-01
Use the linux-headers package that is corresponding to your running kernel version instead of a source tree.

Otherwise, just install linux-tree.

---

### Post by BeBoxer on 2005-05-03
[QUOTE=azz]Use the linux-headers package that is corresponding to your running kernel version instead of a source tree.

Otherwise, just install linux-tree.[/QUOTE]


If I install linux-tree, I end up with /usr/src/linux-source-2.6.10.tar.bz2. Out of curiosity, what sub version is that? What confuses me is that there is a binary kernel 2.6.10-5 but no source package 2.6.10-5. I would think that there would be source packages for each kernel, but apparently not. What makes a particular kernel a '-5' extraversion? Is it just configuration changes? How do I tell what extraversion the linux-source-2.6.10.tar.bz2 contains?

The other thing I'm stumped about is why my modules built from kernel.org source didn't work. From what I can tell, all Debian/Ubuntu changed in the source of drivers/usb/serial is the Kconfig file so that the firmware option wouldn't show up in 'make config'. It's not as though the actual .c or .h files changed I don't think. What magic value is the kernel checking when I try to insert the module? I thought it was checking the CRC (based on the source of kernel/module.c) but the new working module has a different value than the original one. I'm totally confused about how this works.

Finally, does anyone know how to build only the modules in a certain subdirectory of the kernel? I would love to be able to just do something like 'make modules drivers/usb/serial', since a full kernel compile takes an hour or two on my laptop.

---

### Post by az on 2005-05-03
2.6.10 is the kernel version number.

-5 is the package version

-386 is the arch.

Using kernel-package, you would do something like

sudo make-kpkg --revision=5 --append-to-version=-386 modules_image

If you use the linux-headers, all this version stuff is already done for you and any module you build using the linux-headers as your source tree will have the correct information.

---

