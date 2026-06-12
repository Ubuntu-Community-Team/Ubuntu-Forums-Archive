---
title: "Installing nvidia 180.60 drivers"
date: 2009-11-13
forum: Hardware
---

### Post by darkwrat on 2009-11-13
Hello,

I have a little problem with installing the mentioned nvidia driver on 9.10...
the problem i have is that kernel module won't compile even though I have all dependencies (linux-headers, build-essential...) installed. I did check the installation log and it says that autoconf.h could be missing, but that header file is where it should be.

The reason why I wan't to install version 180.60 is because 185.xx nor 190.xx works with my GPU (gf 9650m gt) and so far ubuntu is only distro i can't install driver on

Is there any other solution?

Cheers.

---

### Post by tribaal on 2009-11-13
I'm having the same issue. Cannot compile the nvidia driver module on Ubuntu 9.10.

Anybody have a workaround?

- Trib'

---

### Post by aldeby on 2009-11-14
I have the same problem trying to use the 180.60 nvidia driver version.

I need to use this specific version because later ones silently override user PowerMizer settings in xorg.conf!

---

