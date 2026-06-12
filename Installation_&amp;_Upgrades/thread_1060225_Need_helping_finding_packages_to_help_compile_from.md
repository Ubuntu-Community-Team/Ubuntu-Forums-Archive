---
title: "Need helping finding packages to help compile from source"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by beastrace91 on 2009-02-04
I am trying to compile [Cheese Webcam Booth](http://projects.gnome.org/cheese/) from source but I need the following packages: ```
checking for CHEESE... configure: error: Package requirements (  glib-2.0 >= 2.16.0   gobject-2.0 >= 2.12.0   gio-2.0 >= 2.16.0   gtk+-2.0 >= 2.10.0   gdk-2.0 >= 2.12.0   libgnomeui-2.0 >= 2.20.0   gconf-2.0 >= 2.16.0   gstreamer-0.10 >= 0.10.20   gstreamer-plugins-base-0.10 >= 0.10.20   gnome-vfs-2.0 >= 2.18.0   libebook-1.2 >= 1.12.0   cairo >= 1.4.0   dbus-1 >= 1.0   dbus-glib-1 >= 0.7   hal >= 0.5.9   pangocairo >= 1.18.0   librsvg-2.0 >= 2.18.0) were not met:

No package 'glib-2.0' found
No package 'gobject-2.0' found
No package 'gio-2.0' found
No package 'gtk+-2.0' found
No package 'gdk-2.0' found
No package 'libgnomeui-2.0' found
No package 'gconf-2.0' found
No package 'gstreamer-0.10' found
No package 'gstreamer-plugins-base-0.10' found
No package 'gnome-vfs-2.0' found
No package 'libebook-1.2' found
No package 'cairo' found
No package 'dbus-1' found
No package 'dbus-glib-1' found
No package 'hal' found
No package 'pangocairo' found
No package 'librsvg-2.0' found

```

Anyone shed some light on where I can get some/all of these please?

Thanks,
~Jeff

---

### Post by Partyboi2 on 2009-02-04
Cheese is in the intrepid repo. You can install by searching for 'cheese' in synaptic or install using apt-get
```
sudo apt-get install cheese
```If you still need to compile for some reason you can pull in all the dev packages required to compile by using
```
 sudo apt-get build-dep cheese
```

---

### Post by arfanahmedcheema on 2011-08-10
hecking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for UDEV... yes
checking operating system... Linux
checking sys/videoio.h usability... no
checking sys/videoio.h presence... no
checking for sys/videoio.h... no
checking X11/extensions/XTest.h usability... no
checking X11/extensions/XTest.h presence... no
checking for X11/extensions/XTest.h... no
checking for CHEESE... no
configure: error: Package requirements (  glib-2.0 >= 2.28.0   gobject-2.0 >= 2.28.0   gdk-pixbuf-2.0   gstreamer-0.10 >= 0.10.32   gstreamer-plugins-base-0.10 >= 0.10.32   cairo >= 1.10.0   pangocairo >= 1.28.0   clutter-1.0 >= 1.6.1   clutter-gst-1.0 >= 1.0.0   mx-1.0   gudev-1.0
  ) were not met:

No package 'gdk-pixbuf-2.0' found
No package 'gstreamer-0.10' found
No package 'gstreamer-plugins-base-0.10' found
No package 'cairo' found
No package 'pangocairo' found
No package 'clutter-1.0' found
No package 'clutter-gst-1.0' found
No package 'mx-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables CHEESE_CFLAGS
and CHEESE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


then i tried below and it works
./configure CHEESE_CFLAGS="-march=core2 -O2 -pipe -fomit-frame-pointer" CHEESE_LIBS=/usr CHEESE_GTK_CFLAGS="-march=core2 -o2 -pipe -fomit-frame-pointer" CHEESE_GTK_LIBS=/usr

it will configure completely but when i make it, it give below error!!!!!!!
make  all-recursive
make[1]: Entering directory `/home/ahmed/Downloads/cheese-3.0.1'
Making all in libcheese
make[2]: Entering directory `/home/ahmed/Downloads/cheese-3.0.1/libcheese'
glib-genmarshal \
        --prefix=_cheese_marshal \
        --header \
    ./cheese-marshal.list > xgen-mh \
    && (cmp -s xgen-mh cheese-marshal.h || cp -f xgen-mh cheese-marshal.h) \
    && rm -f xgen-mh \
    && echo timestamp > stamp-marshal
glib-mkenums \
        --template ./cheese-enum-types.h.in \
    ../libcheese/cheese-widget.h > xgen-eh \
    && (cmp -s xgen-eh cheese-enum-types.h || cp -f xgen-eh cheese-enum-types.h) \
    && rm -f xgen-eh \
    && echo timestamp > stamp-enum-types
make  all-am
make[3]: Entering directory `/home/ahmed/Downloads/cheese-3.0.1/libcheese'
/bin/bash ../libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..  -DDATADIR=\"/usr/local/share\" -DPREFIX=\""/usr/local"\" -DSYSCONFDIR=\""/usr/local/etc"\" -DLIBDIR=\""/usr/local/lib"\" -DPACKAGE_DATADIR=\""/usr/local/share/cheese"\" -DPACKAGE_LOCALEDIR=\""/usr/local/share/locale"\" -DAPPNAME_DATA_DIR=\"/usr/local/share/cheese\" -DGNOME_DESKTOP_USE_UNSTABLE_API=1 -march=core2 -O2 -pipe -fomit-frame-pointer -march=core2 -o2 -pipe -fomit-frame-pointer  -march=core2 -O2 -pipe -fomit-frame-pointer -g -O2 -Wall -DGSEAL_ENABLE -MT libcheese_la-cheese-fileutil.lo -MD -MP -MF .deps/libcheese_la-cheese-fileutil.Tpo -c -o libcheese_la-cheese-fileutil.lo `test -f 'cheese-fileutil.c' || echo './'`cheese-fileutil.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -DDATADIR=\"/usr/local/share\" -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DLIBDIR=\"/usr/local/lib\" -DPACKAGE_DATADIR=\"/usr/local/share/cheese\" -DPACKAGE_LOCALEDIR=\"/usr/local/share/locale\" -DAPPNAME_DATA_DIR=\"/usr/local/share/cheese\" -DGNOME_DESKTOP_USE_UNSTABLE_API=1 -march=core2 -O2 -pipe -fomit-frame-pointer -march=core2 -o2 -pipe -fomit-frame-pointer -march=core2 -O2 -pipe -fomit-frame-pointer -g -O2 -Wall -DGSEAL_ENABLE -MT libcheese_la-cheese-fileutil.lo -MD -MP -MF .deps/libcheese_la-cheese-fileutil.Tpo -c cheese-fileutil.c  -fPIC -DPIC -o .libs/libcheese_la-cheese-fileutil.o
cc1: fatal error: .libs/libcheese_la-cheese-fileutil.d: No such file or directory
compilation terminated.
make[3]: *** [libcheese_la-cheese-fileutil.lo] Error 1
make[3]: Leaving directory `/home/ahmed/Downloads/cheese-3.0.1/libcheese'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/ahmed/Downloads/cheese-3.0.1/libcheese'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ahmed/Downloads/cheese-3.0.1'
make: *** [all] Error 2

---

### Post by steve11911 on 2011-08-12
I am always uncomfortable linking dated pages but the cheese website still links this post:

[http://ubuntuforums.org/showthread.php?t=486722](http://ubuntuforums.org/showthread.php?t=486722)

If you get in real trouble there are a bevy of Ubuntu cheese loving contacts here:

[http://www.omgubuntu.co.uk/2010/12/cheese-webcam-gets-some-crazy-new-effects/](http://www.omgubuntu.co.uk/2010/12/cheese-webcam-gets-some-crazy-new-effects/)

The development looks strong-several updates this year-your chances of getting this up and running look good.

---

