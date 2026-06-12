---
title: "Need major help installing gtk+ on ubuntu"
date: 2009-10-14
forum: Installation &amp; Upgrades
---

### Post by bevilacq12 on 2009-10-14
I'm using Ubuntu 8.04, and I need to install gtk+ 2.18.2 for a development project.  I am fairly new to Linux, and do not know much about the operating system besides basic functionality and configure/make/make install type things.  

The application I am trying to install requires gtk, so my first thought was to use apt-get to download it.  The install of libgtk2.0-dev was successful, but the program I am trying to run would not compile with it - the make fails due to my version of gtkadjustment.h not having definitions for gtk_adjustment_set_upper and gtk_adjustment_set_step.  I tried every variant of gtk on apt-get that I could find, and none fixed this issue.

Google-ing for gtkadjustment.h, I saw that newer versions definitely have those two terms defined, so I decided to download and install a newer gtk+ version myself.  I got gtk+ 2.18.2 and so-called installation instructions from the gtk+ website and set to work.  2 days and countless frustration later, I still cannot get it installed.  I have had so many problems along the way it is unbelievable.  I don't even remember the exact list of problems I surmounted, but here is my current installation order, and the current show-stopping problem.

Steps from a fresh Ubuntu 8.04 install:
sudo apt-get update
sudo apt-get install g++
pkg-config-0.23
make-3.81
jpeg-6b
sudo apt-get install zlib1g-dev
libpng-1.2.40
tiff-v3.5.7
freetype-2.3.11
libxml2-2.7.6
fontconfig-2.7.0
gettext-0.17
glib-2.22.2
export PKG_CONFIG_PATH=/usr/local/lib/include
export LD_LIBRARY_PATH=/usr/local/lib
sudo apt-get install libx11-dev
pixman-0.16.2
cairo-1.8.8
pango-1.26.0
atk-1.28.0
sudo apt-get install libxrender-dev
sudo apt-get install libjpeg62-dev
sudo apt-get install x-dev
sudo apt-get install libxt-dev
sudo apt-get install libxext-dev
gtk+-2.18.2

./configure and make work fine for gtk+, but when I attempt sudo make install, I get the following error (after pages upon pages of correct-looking install stuff of course):

.....
libtool: finish: PATH="/usr/lib/kde4/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /usr/local/lib/gtk-2.0/2.10.0/immodules
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/gtk-2.0/2.10.0/immodules

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make  install-data-hook
make[4]: Entering directory `/home/cory/Desktop/drop/gtk+-2.18.2/modules/input'
/bin/bash /home/cory/Desktop/drop/gtk+-2.18.2/install-sh -d /usr/local/etc/gtk-2.0
../../gtk/gtk-query-immodules-2.0 > /usr/local/etc/gtk-2.0/gtk.immodules
Cannot load module /usr/local/lib/gtk-2.0/2.10.0/immodules/im-xim.so: /usr/local/lib/gtk-2.0/2.10.0/immodules/im-xim.so: undefined symbol: g_dgettext
/usr/local/lib/gtk-2.0/2.10.0/immodules/im-xim.so does not export GTK+ IM module API: /usr/local/lib/gtk-2.0/2.10.0/immodules/im-xim.so: undefined symbol: g_dgettext
make[4]: *** [install-data-hook] Error 1
make[4]: Leaving directory `/home/cory/Desktop/drop/gtk+-2.18.2/modules/input'
make[3]: *** [install-data-am] Error 2
make[3]: Leaving directory `/home/cory/Desktop/drop/gtk+-2.18.2/modules/input'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/cory/Desktop/drop/gtk+-2.18.2/modules/input'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/cory/Desktop/drop/gtk+-2.18.2/modules'
make: *** [install-recursive] Error 1

I've Google-ed for locations and phrases from that error, but have not been able to find a single thing that helped.  Worse yet, my system gets messed up at this point - simple things like gedit stop working even.  If I attempt to start gedit, I get a long error about Gtk+ theme and icon problems.

Hopefully someone can help me resolve this giant mess.  Maybe I'm going about this the entirely wrong way - if you know a simple way to install gtk+ (a version with _set_upper and _set_size in the gtkadjustment.h file of course), I'd obviously love to hear it.

---

