---
title: "Problems with .tar.bz2"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by Maurits01 on 2009-05-18
Hi, 

I recently installed the latest version of Ubuntu and am very inexperienced. 

I am tying to install a program called[ graphgene-0.4]("http://sourceforge.net/projects/graphgene") which is a .tar.bz2 I got from sourceforge.net

When I type ./configure I get this: 

```
Package requirements (  gtk+-2.0 >= 2.4   libglade-2.0 >= 2.4   libgnomeui-2.0) were not met:

No package 'gtk+-2.0' found
No package 'libglade-2.0' found
No package 'libgnomeui-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GENE_CFLAGS
and GENE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

No idea what to do. I tried the ease compiler guide at [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) and have been searching at many other places but I cannot solve it. Also the readme file doesn't offer any relief.

Any suggestions? Thanks!

---

### Post by Mark Phelps on 2009-05-18
Trying to install from source is probably the most difficult thing for a new Linux person to do.  You need LOTS of libraries to satisfy dependencies and the correct library to install is not readily apparent.

The messages mean you need to open Synaptic and install (at least) the missing packages.

You would do better searching Synaptic to see if it has the graphing package you want.  It's able to identify the dependencies and attempt to resolve them for you.

---

