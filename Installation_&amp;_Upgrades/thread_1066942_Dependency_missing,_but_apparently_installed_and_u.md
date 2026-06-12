---
title: "Dependency missing, but apparently installed and up to date..."
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by cparks0225 on 2009-02-11
I'm getting confusing and seemingly conflicting messages when attempting to compile some third party software, wondering if anybody has seen this before.

Running ./configure gives me the following:

[INDENT]checking for LIBXML2... configure: error: Package requirements (libxml-2.0 >= 2.6.0) were not met:

No package 'libxml-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBXML2_CFLAGS
and LIBXML2_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.[/INDENT]

However, attempting to run "apt-get install libxml2", I get this:

[INDENT]Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxml2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/INDENT]

Any help is greatly appreciated.
Thank you,
~CParks

---

### Post by Partyboi2 on 2009-02-11
When compiling generally you need to install the development packages of the packages that it complains about that are missing so install libxml2-dev
```
sudo apt-get install libxml2-dev
```
[B]
[/B]

---

### Post by cparks0225 on 2009-02-12
That did the trick, thanks :)

---

