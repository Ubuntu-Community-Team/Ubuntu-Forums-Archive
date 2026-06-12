---
title: "Package glib-2.0 was not found in the pkg-config search path. Perhaps you should add"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by amarshukla123 on 2009-08-20
Now I am trying to install mono2.4 from its source so I have downloaded the source and while I tried to install it I got the error as below . Please help me hwo to install it as already I had failed to install it from my repo the mono2.0 version .Error I got is as following -

**[B]**[/B]
checking for pkg-config... /usr/bin/pkg-config
Package glib-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glib-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glib-2.0' found
Package gthread-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gthread-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gthread-2.0' found
Package glib-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glib-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glib-2.0' found
Package gthread-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gthread-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gthread-2.0' found
checking pkg-config is at least version 0.9.0... yes
checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 1.3.11) were not met:

No package 'glib-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.

---

### Post by Partyboi2 on 2009-08-20
Hi, you need to install the libglib2.0-dev package
```
sudo apt-get install libglib2.0-dev
```

[B]
[/B]

---

