---
title: "Ubuntu Kernel"
date: 2005-11-11
forum: General Help
---

### Post by guardianangelz on 2005-11-11
Hi, I'm a semi-veteran Ubuntu user and a newbie to this forum.  I'm trying to compile a new kernel for a server I'm trying to run at my school, but for one reason or another it's not been booting.  We alighted on the awesome idea of stealing a .config file from a Ubuntu kernel source, but I can't find one anywhere on my machine or on the Internet.  If anybody (Ubuntu developers, other users on this forum) have the Ubuntu Linux kernel as an uncompiled source code (or, alternatively, a .config file from such a source code) could they PLEASE send it to me?

Thanks,
Terry

---

### Post by Azrael on 2005-11-11
Um.. have you looked at your /boot/config-2.6.*yourversion*?

---

### Post by az on 2005-11-11
and you need an initrd.

If you are using kernel-package, do

sudo make-kpkg --revision=1 --append-to-version=whatever --initrd kernel_image kernel_headers

You can also use the --stem=linux flag if you want the packages to be named linux-image-xxx instead of kernel-image-xxx.  That should not matter since you will not be getting kernel updates from the repositories.

If you are not using kernel-package, use kernel-package.  It is the easiest and the safest way to muck around with custom kernels.

You can also use fakeroot instead of sudo.

---

### Post by guardianangelz on 2005-11-11
Yeah... all this for trying to get the IPVS utility to work on the server.  It's supposed to be included in the kernel version behind Ubuntu 5.1, but guess what? It's (I think) not included in the Ubuntu compilation.

I was under the impression the initrd was only for SCSI ("You don't have skuzzie installed, do you?" "*blank stare*") so it's not a necessity.  Tell me if I'm wrong.  And you can't manipulate files that came out the back side of a "make" command, can you?  Like the config-xxx files?

---

