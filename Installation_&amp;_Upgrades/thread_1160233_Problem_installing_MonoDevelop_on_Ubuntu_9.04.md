---
title: "Problem installing MonoDevelop on Ubuntu 9.04"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by jl2035 on 2009-05-15
I downloaded monodevelop-2.0.tar.bz2 package from [here]("http://monodevelop.com/Download"). The README file says I have to compile it using these commands:
1. ./configure --prefix=`pkg-config --variable=prefix mono`
2. make
3. make install

This is the ouput of the first command: 
```
jaka@LaptopJaka:~/Desktop/MonoDevelop/monodevelop-2.0$ ./configure --prefix=`pkg-config --variable=prefix mono`
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... no
checking for mono... /usr/bin/mono
checking for gmcs... /usr/bin/gmcs
checking for update-mime-database... /usr/bin/update-mime-database
checking for update-desktop-database... /usr/bin/update-desktop-database
checking for pkg-config... /usr/bin/pkg-config
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking pkg-config is at least version 0.9.0... yes
checking for UNMANAGED_DEPENDENCIES_MONO... yes
checking for mono... /usr/bin/mono
checking for gmcs... /usr/bin/gmcs
checking for MONO_ADDINS... yes
checking for MONO_ADDINS_SETUP... yes
checking for MONO_ADDINS_GUI... yes
checking for GLIB_SHARP... yes
checking for GTK_SHARP... yes
checking for GLADE_SHARP... yes
checking for MONODOC... configure: error: Package requirements (monodoc >= 1.0) were not met:

No package 'monodoc' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables MONODOC_CFLAGS
and MONODOC_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

jaka@LaptopJaka:~/Desktop/MonoDevelop/monodevelop-2.0$ 

```
When I type 'make' it just says:
```
make: *** No targets specified and no makefile found.  Stop.
```

So... what am I doing wrong?  By the way I'm using Kubuntu.

---

### Post by directhex on 2009-05-15
I'll ask: why are you building from source when it's in the archive?

---

### Post by jl2035 on 2009-05-15
> **directhex said:**
> I'll ask: why are you building from source when it's in the archive?

OK, I get it but I don't know, how to use that build...  Finally I got an idea of installing using the apt-get command.. It's installed and works now - I can't belive this! :)

We should move this thread to trash - it was a stupid problem! :D

---

