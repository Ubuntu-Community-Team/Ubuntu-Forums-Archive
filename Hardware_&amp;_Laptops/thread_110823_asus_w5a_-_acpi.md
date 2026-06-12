---
title: "asus w5a - acpi"
date: 2005-12-31
forum: Hardware &amp; Laptops
---

### Post by mdwuznik on 2005-12-31
Hi, 
I wanted to compile my own, patched version of acpi4asus module to enable blutooth on my W5A. I got a running 2.6.12-10-686 kernel , 2.6.12 kernel source installed , cpp 3.4 installed and set in the acpi4asus makefile as the compiler (I assume that breezy still compiles the kernel with gcc-3.4). The /usr/src/linux/.config is copied from /boot/config-2.6.16-10-686 , the acpi4asus 0.29 source compiles smoothly and then after copying asus_acpi.ko over the old asus_acpi.ko modprobe -v asus_acpi says "Invalid module format" for all the configurations tried ...

Anyone can help me in compiling a patched version (or including the patch in the distro itself ) ?


I assume the problem comes from kernel-compile issue, but I cannot pinpoint the actual problem, sorry....
Regards
Michal

---

### Post by Luzbel on 2005-12-31
Are you booting to the kernel you compiled yourself? It should load ok if you do. If you didn't install your own compiled kernel:

root@host:/usr/src/linux# make install (Just it case you didn't know :) )

---

### Post by mdwuznik on 2006-01-01
Thanks a lot, I'm trying to compile for a stock kernel if possible. Any chance of _not_ compiling the whole kernel ?(I'm not afraid of it, rather trying to avoid the time losses coming with each upgrade of the kernel package and the need to recompile then...).

Cheers and Happy New Year!

Michal

---

### Post by Luzbel on 2006-01-01
Well, you can package kernel and modules on .deb files once you have compiled them, but you can't (well, you can but not cleanly) compile modules against different sources from the kernel you want to use. If you wanna use Kernel A, and you need to compile a module for it, you shouldn't compile the module against B (being A!=B) sources.

If you want to avoid compiling Kernel every new version for any reason, you can have it prepackaged, but it would not be as optimized as if you compiled it yourself. Anyhow, from my personal experience I can assure you a well configured kernel on a modern processor (well, over 1.5 Ghz really) won't take that much time in compiling; and if you need to add a new module against the sources of the kernel you are using there's no need to recompile the whole thing. Be sure to have kept a former known working version to boot in case the new compiled kernel panics.

I hope my bad English let you undestand what you have in hands ;)

---

### Post by mdwuznik on 2006-01-01
You know, last time I really _needed_ to compile my own kernel to enable some features was RedHat6 on Sun Sparc Ultra 10 back in 2001(or 2002) :). 
From than on I used stock kernels on all machines around.
So for me it was really make dep && make && make modules ..... issue . 
Soem 10 minutes ago I discovered make-kpkg which seems to cover my needs well (well, I'll see after a reboot scheduled after finishing this post ). In the old times (ghr, ghr...) x.y.z tree compiling when running x.y.z-a was no problem, as far as my memory is not that fragile.... ;)

Cheers
Michal

PS:I see no reason for "bad English" excuse, I'm Polish myself :)

---

