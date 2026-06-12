---
title: "Logitech MX5000: mxtools problem"
date: 2007-03-09
forum: Hardware &amp; Laptops
---

### Post by Timtro on 2007-03-09
Well, what a ride this is turning out to be.

Dear reader, thank you for your consideration.

I'm trying to get mxtools for my new MX5000 keyboard to compile. Thus far, I've had to visit:
[http://linuxsoft.cern.ch/cern/slc4X/i386/yum/os/repodata/repoview/netpbm-devel-0-10.25-2.EL4.3.html](http://linuxsoft.cern.ch/cern/slc4X/i386/yum/os/repodata/repoview/netpbm-devel-0-10.25-2.EL4.3.html)
to get the rpm for the development version of the netpbm library, convert it to deb with alien, and now I'm having a problem I can't resolve.

During ./configure, I get the following error:
```

checking pbm.h usability... yes
checking pbm.h presence... yes
checking for pbm.h... yes
checking for pbm_readpbm in -lnetpbm... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
checking for MX5000D... configure: error: Package requirements (glib-2.0 >= 2.8.0 ) were not met:

No package 'glib-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables MX5000D_CFLAGS
and MX5000D_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


```

As far as I can tell, I should have glib! Isn't it part of GTK/Gnome??

Anyhow, any advice would be greatly appreciated.

Thank you all.

---

### Post by teaker1s on 2007-03-10
try searching and installing with synaptic
```
gksudo synaptic
```

think it may be refered in synaptic as "libglib2.0-0"

also make sure "build-essential" is installed if not already

---

### Post by Timtro on 2007-03-13
Thanks, that helped.

---

