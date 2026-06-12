---
title: "ATI + custom kernel 2.6.22, Ubuntu 6.06"
date: 2007-08-11
forum: Hardware &amp; Laptops
---

### Post by phax on 2007-08-11
Hello!

I have my own compiled kernel 2.6.22 -- compiled in debian/ubuntu way with:

```
make-kpkg --revision=custom.0.1 kernel_image --initrd
```

I use it without problems, but I want to compile ATI drivers. I downloaded the latest installer from their site

```
ati-driver-installer-8.39.4-x86.x86_64.run
```

installation process terminates with this error:

```

# cat fglrx-install.log 
[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
ATI module generator V 2.0
==========================
initializing...
Error:
kernel includes at /lib/modules/2.6.22custom1/build/include do not match current kernel.
they are versioned as ""
instead of "2.6.22custom1".
you might need to adjust your symlinks:
- /usr/include
- /usr/src/linux
[Error] Kernel Module : Failed to compile kernel module - please consult readme.

```

And I don't know why:( 

In the /usr/src I have symlink linux -> linux-2.6.22

and

```

in /lib/modules/2.6.22custom1:
source -> /usr/src/linux-2.6.22
build -> /usr/src/linux-2.6.22
include -> /usr/src/linux/include/

```
Maybe there is problem in the "custom1"? I don't know.

Thanks for any help...

---

