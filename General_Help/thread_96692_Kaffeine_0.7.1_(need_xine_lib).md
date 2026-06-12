---
title: "Kaffeine 0.7.1 (need xine lib)"
date: 2005-11-29
forum: General Help
---

### Post by floyd27 on 2005-11-29
Hi..
My stock kaffeine stopped working so i deleted it and got the new 0.7.1..
I tried to ./configure but i get this eror..

checking for XINE-LIB version >= 1.0.0... no
*** The xine-config script installed by XINE could not be found
*** If XINE was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the XINE_CONFIG environment variable to the
*** full path to xine-config.
configure: error: *** Please install xine-lib first ***
roderick@ubuntu:~/Desktop/kaffeine-0.7.1$


Anyone know whats wrong here?
Any help would be great. I just want kaffeine to work i dont care whjat version it is.. BTW. i dont know wht the stock one broke. I would just open for a split second then stop. I was using the gstreamer engine. 

thanx

---

### Post by floyd27 on 2005-11-29
im still trying.
i upgraded to KDE 2.5 just now..
I got this error..

You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kaffeine: Depends: kdelibs4 (>= 4:3.4.0) but it is not installable
            Depends: libqt3c102-mt (>= 3:3.3.3) but it is not installable
            Depends: libxine1 (>= 1-rc3a) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
roderick@ubuntu:~$

Any ideas ..?

---

### Post by floyd27 on 2005-11-29
I did a sudo apt-get -f install.

./configure (went well)
make (gives me this)

/bin/sh ../../libtool --silent --tag=CXX --mode=link g++  -Wnon-virtual-dtor -Wno-long-long -Wundef -fasynchronous-unwind-tables -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wno-non-virtual-dtor -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common   -L/usr/X11R6/lib -o libkmediapart.la -rpath /usr/lib -L/usr/lib -L/usr/share/qt3/lib -L/usr/X11R6/lib    -lXtst -L/usr/lib -lxine -lz -lnsl -lpthread -lrt -version-info 0:1:0 -no-undefined -Wl,--no-undefined -Wl,--allow-shlib-undefined mrl.lo kmediapart.lo playlistimport.lo http.lo -lkparts
grep: /lib/libacl.la: No such file or directory
/bin/sed: can't read /lib/libacl.la: No such file or directory
libtool: link: `/lib/libacl.la' is not a valid libtool archive
make[4]: *** [libkmediapart.la] Error 1
make[4]: Leaving directory `/home/roderick/Desktop/kaffeine-0.7.1/kaffeine/player-parts'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/roderick/Desktop/kaffeine-0.7.1/kaffeine/player-parts'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/roderick/Desktop/kaffeine-0.7.1/kaffeine'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/roderick/Desktop/kaffeine-0.7.1'
make: *** [all] Error 2
roderick@ubuntu:~/Desktop/kaffeine-0.7.1$

---

### Post by getaceres on 2005-11-29
You have to install the libxine-dev,kdebase-dev and libtool packages to compile it.

---

### Post by floyd27 on 2005-12-01
I tried but still i get the same error?

---

### Post by mephisto786 on 2005-12-03
Running ubuntu with all of kubuntu apps loaded (except the language translation docs) it seems clear that both totem and kaffeine are seriously buggy in this release....for me, its totem crashing a second after it pops up and kaffeine not quite playing anything at the moment and causing konqueror to pop up repeatedly whenever a disk is installed.....lots of comments in the forum about these...my solution? install ogle. Its only a few months till dapper hits and hopefully this gstreamer video/dvd wierdness will just be a bad memory.  On Hoary, it was the constantly crashing home folder .... sometimes unstable is just that....:razz:

---

### Post by limit223 on 2005-12-04
Make sure you did install all these packages before compilation: libxine1c2 libxine-dev, libqt3, libqt3-dev, libqt3-headers, libacl1, libacl1-dev
This is my final output of ./configure:

checking for Qt... libraries /usr/share/qt3/lib, headers /usr/share/qt3/include using -mt
checking for moc... /usr/share/qt3/bin/moc
checking for uic... /usr/share/qt3/bin/uic
checking whether uic supports -L ... yes
checking whether uic supports -nounload ... yes
checking if Qt needs -ljpeg... no
checking for rpath... yes
checking for KDE... libraries /usr/lib, headers /usr/include/kde
checking if UIC has KDE plugins available... yes
checking for KDE paths... defaults
checking for dcopidl... /usr/bin/dcopidl
checking for dcopidl2cpp... /usr/bin/dcopidl2cpp
checking for mcopidl... /usr/bin/mcopidl
checking for artsc-config... /usr/bin/artsc-config
checking for meinproc... /usr/bin/meinproc
checking for kconfig_compiler... /usr/bin/kconfig_compiler
checking for dcopidlng... /usr/bin/dcopidlng
checking for xmllint... /usr/bin/xmllint
checking whether g++ supports -fvisibility=hidden... yes
checking if Qt is patched for -fvisibility... no
checking for XTestFakeMotionEvent in -lXtst... yes
checking for XineramaQueryExtension in -lXinerama... yes
checking for xine-config... /usr/bin/xine-config
checking for XINE-LIB version >= 1.0.0... yes
checking for strsep... yes
checking for strpbrk... yes
checking for setenv... yes
checking linux/dvb/frontend.h usability... yes
checking linux/dvb/frontend.h presence... yes
checking for linux/dvb/frontend.h... yes
checking for pkg-config... yes
checking for pkg-config... /usr/bin/pkg-config
checking for gstreamer-0.8 >= 0.8.4
                          gstreamer-interfaces-0.8 >= 0.8.4... yes
checking GST_CFLAGS... -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -pthread -I/usr/include/gstreamer-0.8 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2
checking GST_LIBS... -Wl,--export-dynamic -pthread -lgstinterfaces-0.8 -lgstreamer-0.8 -lgobject-2.0 -lgmodule-2.0 -ldl -lgthread-2.0 -lxml2 -lz -lm -lglib-2.0
checking for gstreamer-plugins-0.8 >= 0.8.4... yes
checking GST_PLUGINS_CFLAGS... -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -pthread -I/usr/include/gstreamer-0.8 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2
checking GST_PLUGINS_LIBS... -Wl,--export-dynamic -pthread -lgstreamer-0.8 -lgobject-2.0 -lgmodule-2.0 -ldl -lgthread-2.0 -lxml2 -lz -lm -lglib-2.0
checking if doc should be compiled... yes
checking if kaffeine should be compiled... yes
checking if mimetypes should be compiled... yes
checking if misc should be compiled... yes
checking if po should be compiled... yes
checking if protocols should be compiled... yes
checking if servicemenus should be compiled... yes
configure: creating ./config.status
fast creating Makefile
fast creating doc/Makefile
fast creating doc/en/Makefile
fast creating doc/man/Makefile
fast creating doc/man/de/Makefile
fast creating doc/man/en/Makefile
fast creating doc/zh_CN/Makefile
can't open ./doc/zh_CN/Makefile.in: No such file or directory
fast creating kaffeine/Makefile
fast creating kaffeine/dvb/Makefile
fast creating kaffeine/dvbclient/Makefile
fast creating kaffeine/player-parts/Makefile
fast creating kaffeine/player-parts/dummy-part/Makefile
can't open ./kaffeine/player-parts/dummy-part/Makefile.in: No such file or directory
fast creating kaffeine/player-parts/gstreamer-part/Makefile
fast creating kaffeine/player-parts/kaffeine-part/Makefile
fast creating mimetypes/Makefile
fast creating mimetypes/application/Makefile
fast creating misc/Makefile
fast creating po/Makefile
fast creating protocols/Makefile
fast creating servicemenus/Makefile
config.pl: fast created 20 file(s).
config.status: creating config.h
config.status: executing depfiles commands

-------------------------------------------------------
Kaffeine Configure results:

Build with DVB support:                             yes
Build GStreamer player-part:                        yes
-------------------------------------------------------


Your GCC supports symbol visibility, but the patch for Qt supporting visibility
was not included. Therefore, GCC symbol visibility support remains disabled.

For better performance, consider including the Qt visibility supporting patch
located at:

[http://bugs.kde.org/show_bug.cgi?id=109386](http://bugs.kde.org/show_bug.cgi?id=109386)

and recompile all of Qt and KDE. Note, this is entirely optional and
everything will continue to work just fine without it.

And kaffeine 0.7.1 installation was fine!

---

### Post by wouterla on 2005-12-11
Hi,

I just got the same error compile KMediaFactory. It was easily fixed by  doing 'apt-get install libacl1-dev'. And then the same for libattr1-dev, that was missing too.

hth,

Wouter

---

