---
title: "cross compile gtk+ need gdk-pixbuf-csource"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by kbm1008 on 2009-05-05
I'm attempting to cross compile gtk+ on a Ubuntu 7.10 (ltib for target is trying to compile).  The compile fails because gdk-pixbuf-csource is not installed on the Ubuntu host.  I've been trying to locate gdk-pixbuf-csource but haven't found a Gutsy package that contains it.  Can someone give me a pointer?  I know that I need to upgrade to Hardy but I'm in a time crunch on this project and need to finish this one part before doing the upgrade.  Many thanks.

---

### Post by fatalfeel on 2010-07-08
In Ubuntu 10.4 Desktop and "root" login

apt-get install build-essential libncurses5-dev 

apt-get install autoconf

apt-get install libtool

apt-get install gettext

apt-get install libglib2.0-dev

apt-get install libgtk2.0-dev

 
just assign ac_cv_path as follows---->
 
 
make clean
 
export PREFIX=/usr/gtkdfb
 
export LDFLAGS="-L$PREFIX/lib -Wl,-rpath,$PREFIX/lib"
 
export CPPFLAGS="-I$PREFIX/include"
 
export PKG_CONFIG_PATH=$PREFIX/lib/pkgconfig
 
echo gio_can_sniff=yes>arm-linux.cache
 
echo ac_cv_path_GTK_UPDATE_ICON_CACHE=/usr/bin/gtk-update-icon-cache>>arm-linux.cache
 
echo ac_cv_path_GDK_PIXBUF_CSOURCE=/usr/bin/gdk-pixbuf-csource>>arm-linux.cache
 
CC=arm-linux-gcc ./configure --host=arm-linux --prefix=$PREFIX --with-gdktarget=directfb --without-x --disable-modules --with-included-loaders=ani,bmp,gif,ico,png,pnm,ras,tga,wbmp,xbm,xpm --enable-static=yes --enable-shared=no --without-libtiff --without-libjpeg --disable-glibtest --cache-file=arm-linux.cache
 
make
 
make install 
 
 
 
[http://www.wretch.cc/blog/fatalfeel](http://www.wretch.cc/blog/fatalfeel)

---

