---
title: "Glib problem!! for GTK+ install,pls help"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by ivikas on 2009-02-11
hello, 

      i want to try out GTK+.so from their website i downloaded the following source files

Pango 1.20.0

Glib  2.18.0

I have done a clean install of above two like this

./configure---reported clean
make
make install

And now when i tries to install gtk+-2.14.0, the installed old version
is taking up and new one is ignored.I don't know where the new one(Glib  2.18.0) is installed and set path to this

This is what ./configure script of gtk+-2.14.0 outputs
```

checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
checking for GLIB - version >= 2.17.6... 
*** 'pkg-config --modversion glib-2.0' returned 2.18.0, but GLIB (2.16.6)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.17.6 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/pub/gtk/.

```

So, it will be highly appreciated if anyone can help me to get it up and running.

Thanks in advance,
Vikas

---

### Post by neoideo on 2009-10-05
> **ivikas said:**
> hello, 

      i want to try out GTK+.so from their website i downloaded the following source files

Pango 1.20.0

Glib  2.18.0

I have done a clean install of above two like this

./configure---reported clean
make
make install

And now when i tries to install gtk+-2.14.0, the installed old version
is taking up and new one is ignored.I don't know where the new one(Glib  2.18.0) is installed and set path to this

This is what ./configure script of gtk+-2.14.0 outputs
```

checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
checking for GLIB - version >= 2.17.6... 
*** 'pkg-config --modversion glib-2.0' returned 2.18.0, but GLIB (2.16.6)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.17.6 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/pub/gtk/.

```So, it will be highly appreciated if anyone can help me to get it up and running.

Thanks in advance,
Vikas
i have the same problem when trying to install gtk 2.18 from their website, i dont know why i keeps detecting the old glib
```

*** 'pkg-config --modversion glib-2.0' returned 2.22.1, but GLIB (2.20.1)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.21.3 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/pub/gtk/.


```and i installed the latest glib
```

neoideo@neoideo-desktop:~/Desktop/gtk+-2.18.1$ pkg-config --modversion glib-2.0
2.22.1


```

---

### Post by neoideo on 2009-10-05
ok solved,

if you still have the problem

reinstall pango and glib this way

```

sudo ./configure --prefix=/usr
sudo make
sudo make install

```

---

### Post by timmih on 2011-11-05
> ok solved,

if you still have the problem

reinstall pango and glib this way

that didnt work for me :(

---

