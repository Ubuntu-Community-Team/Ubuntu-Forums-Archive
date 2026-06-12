---
title: "GTK+ install problem :("
date: 2005-12-30
forum: Installation &amp; Upgrades
---

### Post by missing on 2005-12-30
Hello. 

I've installed, glib-2.8.4
./configure 
make 
rm -rf /install-prefix/include/glib.h /install-prefix/include/gmodule.h 
make install 
pkg-config --cflags glib-2.0.pc 
pkg-config --libs glib-2.0.pc

, when I do: ./configure in the atk-1.10.1 package I get the following error:

checking for pkg-config... (cached) /usr/local/bin/pkg-config
checking for GLIB - version >= 2.0.0...
*** 'pkg-config --modversion glib-2.0' returned 2.8.4, but GLIB (2.8.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.0.0 or better is required. The latest version of
*** GLIB is always available from [ftp://ftp.gtk.org/](ftp://ftp.gtk.org/). If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.

so in terminal i type  export LD_LIBRARY_PATH=/usr/local/lib

, when I do: ./configure in the gtk+-2.8.9 package I get the following error:

checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 2.7.1    atk >= 1.0.1    pango >= 1.9.0    cairo >= 0.9.2) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the BASE_DEPENDENCIES_CFLAGS and BASE_DEPENDENCIES_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.

what can i do now? Please explain step by step. i'm new in linux :(

---

### Post by fordfan753 on 2005-12-30
Is there a reason you're compiling them instead of just getting them from the repositories?

---

### Post by kaamos on 2005-12-30
Try installing the package libglib2.0-dev

The errors that the configure scripts spits out almost always indicate missing developement libraries. So if you get an error like this, open synaptic, search for the package and look out for packages ending with "-dev".

Hope this helps. :)

edit: Whoa, yea a bit easier is to install both libraries and apps from repositories. Looks here [https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)

---

### Post by missing on 2005-12-30
i don't know, i just want try it myself. I'm third day in linux, so i want learn more :) I tried to install video driver, mplayer and etc. And now i want to install GTK+ 2.9.8 it needs for my tvtuner software.

sorry for my english :(

---

### Post by fordfan753 on 2005-12-30
You probably mean GTK 2.8.9 which should be in the Ubuntu repositories, but if you want to compile it I say go for it! Third day in Linux and you're already learning some cool stuff. I can't count the amount of times compiling something has got me out of a lot of trouble, especially on RPM based distros. As for the problem, I think that maybe there's an old version of libglib2.0 laying around, you might not be able to remove it since I imagine GTK would complain a bit about it.

Before you go hunting through synaptic, just try
```
sudo ldconfig
```

---

### Post by W8eR_CZech on 2007-10-20
I tried to install the same version of GLib and it works

---

