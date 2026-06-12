---
title: "How to remove old version of glib?"
date: 2008-10-18
forum: General Help
---

### Post by soarkaios on 2008-10-18
**So I'm trying to install this thing and it tells me that I need ATK for it, so I'm trying to install ATK but it keeps telling me this error and I have no idea how to remove the older version, lol. Any help ;o?**

checking for GLIB - version >= 2.0.0... 
*** 'pkg-config --modversion glib-2.0' returned 2.19.0, but GLIB (2.16.4)
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

---

### Post by Yellow Pasque on 2008-10-18
Have you installed libglib2.0-0-dev and run ldconfig?
```
sudo ldconfig -v | grep glib
```

---

### Post by soarkaios on 2008-10-19
Awesome, thanks. That worked for that install but when trying to install something else it gives me this error:

checking for jpeg_destroy_decompress in -ljpeg... no
configure: WARNING: *** JPEG loader will not be built (JPEG library not found) ***
configure: error:
*** Checks for JPEG loader failed. You can build without it by passing
*** --without-libjpeg to configure but some programs using GTK+ may
*** not work properly

Tried searching google, but nothing.
Sorry, I'm completely new to linux/ubuntu.

Thanks in advance.

---

### Post by Yellow Pasque on 2008-10-19
What program are you trying to build?
```
sudo apt-get install build-essential libjpeg62-dev
```

---

### Post by soarkaios on 2008-10-19
Trying to build GTK+. Thanks for all your help. 

After doing "sudo apt-get install build-essential libjpeg62-dev" it fixed the last error but gave me a new one;

> checking for jas_init in -ljasper... no
configure: error:
*** Checks for JPEG2000 loader failed. You can build without it by passing
*** --without-libjasper to configure

Am I doing something wrong or is there a quicker, easier way?

---

### Post by Yellow Pasque on 2008-10-19
Try:
```
sudo apt-get build-dep libgtk2.0-common
```

---

### Post by soarkaios on 2008-10-19
Still gives this same error

> checking for jas_init in -ljasper... no
configure: error:
*** Checks for JPEG2000 loader failed. You can build without it by passing
*** --without-libjasper to configure


Well, I'm off to bed. Thanks for any help in advance. Mucho love <3.

---

### Post by Yellow Pasque on 2008-10-19
When a configure script complains that it doesnt have something, it usually means that you should install the corresponding -dev package.

In your case:
```
sudo apt-get install libjasper-dev
```

---

