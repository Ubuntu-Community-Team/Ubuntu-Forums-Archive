---
title: "tsemgr - compile help"
date: 2008-10-12
forum: General Help
---

### Post by SSamiK on 2008-10-12
I'm trying to compile tsemgr, but have run into a problem... 

I'm getting this far:
```
tsemgr-0.08$ ./configure 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking for gtk-config... yes
checking for openobex-config... no
checking OpenObex version... ./configure: line 2657: openobex-config: command not found

configure: error: OpenObex library version is too old.

```

I've got 
libopenobex1 and libopenobex1-dev installed, so I'm quite in the blue about what to do. :confused:

Any hints?

---

### Post by SSamiK on 2008-10-18
Just a little update: It seems tsemgr is no longer maintained, and that openobex-config is removed in the newest openobex package. I got around this by downloading an rpm I found throught google, converted it with alien to a deb and installed. It works, but my search for a decent application to my Sony ericsson will have to go on. ;)

---

