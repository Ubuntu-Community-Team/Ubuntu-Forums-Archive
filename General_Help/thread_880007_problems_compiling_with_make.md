---
title: "problems compiling with make"
date: 2008-08-04
forum: General Help
---

### Post by l0fls on 2008-08-04
attemtping to compile airsnort and i get a problem when i follow the install file that came with it its only instructions are
./configure
make
make install

```
[COLOR="Red"]jimmy@jimmy-laptop:/usr/local/src$ cd /usr/local/src/airsnort-0.2.7e[/COLOR]
[COLOR="Red"]
jimmy@jimmy-laptop:/usr/local/src/airsnort-0.2.7e$ ./configure[/COLOR]
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.0.0... yes
checking PACKAGE_CFLAGS... -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1  
checking PACKAGE_LIBS... -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating man/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
[COLOR="Red"]jimmy@jimmy-laptop:/usr/local/src/airsnort-0.2.7e$ make[/COLOR]
make  all-recursive
make[1]: Entering directory `/usr/local/src/airsnort-0.2.7e'
Making all in src
make[2]: Entering directory `/usr/local/src/airsnort-0.2.7e/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local//locale"\" -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1      -g -O2 -MT callbacks.o -MD -MP -MF ".deps/callbacks.Tpo" -c -o callbacks.o callbacks.c; \
	then mv -f ".deps/callbacks.Tpo" ".deps/callbacks.Po"; else rm -f ".deps/callbacks.Tpo"; exit 1; fi
callbacks.c:9:18: error: pcap.h: No such file or directory
makeIn file included from PacketSource.h:31,
                 from callbacks.c:24:
/usr/include/linux/wireless.h:660: error: expected specifier-qualifier-list before ‘__s32’
/usr/include/linux/wireless.h:673: error: expected specifier-qualifier-list before ‘__u16’
/usr/include/linux/wireless.h:687: error: expected specifier-qualifier-list before ‘__s32’
/usr/include/linux/wireless.h:698: error: expected specifier-qualifier-list before ‘__u8’
/usr/include/linux/wireless.h:714: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:727: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:754: error: expected specifier-qualifier-list before ‘__u8’
/usr/include/linux/wireless.h:816: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:830: error: expected specifier-qualifier-list before ‘__u16’
/usr/include/linux/wireless.h:844: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:852: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:861: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:873: error: expected specifier-qualifier-list before ‘__u16’
/usr/include/linux/wireless.h:896: error: ‘IFNAMSIZ’ undeclared here (not in a function)
/usr/include/linux/wireless.h:911: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:955: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:1059: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:1077: error: expected specifier-qualifier-list before ‘__u16’
In file included from callbacks.c:24:
PacketSource.h:153: error: expected specifier-qualifier-list before ‘pcap_t’
PacketSource.h:178: warning: ‘struct pcap_pkthdr’ declared inside parameter list
PacketSource.h:178: warning: its scope is only this definition or declaration, which is probably not what you want
PacketSource.h:179: warning: ‘struct pcap_pkthdr’ declared inside parameter list
callbacks.c:79: error: ‘PCAP_ERRBUF_SIZE’ undeclared here (not in a function)
callbacks.c: In function ‘fillDeviceList’:
callbacks.c:121: error: storage size of ‘ir’ isn’t known
callbacks.c:129: error: ‘IFF_LOOPBACK’ undeclared (first use in this function)
callbacks.c:129: error: (Each undeclared identifier is reported only once
callbacks.c:129: error: for each function it appears in.)
make[2]: *** [callbacks.o] Error 1
make[2]: Leaving directory `/usr/local/src/airsnort-0.2.7e/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/airsnort-0.2.7e'
make: *** [all] Error 2 

```


:confused:
first time compiling help plz

---

### Post by mc4man on 2008-08-04
Search in synaptic for libpcap and install the -dev package
Maybe libpcap0.8-dev  ( and or ....0.7-dev, if 0.8 doesn't work)

edit ver. above from/for Hardy

---

### Post by l0fls on 2008-08-04
i got the -dev package still seems to be a problem when i make

same readout in terminal...

---

### Post by mc4man on 2008-08-04
I'll give it a go,  
there's a .deb here (for hardy)
[http://www.getdeb.net/search.php?keywords=AirSnort](http://www.getdeb.net/search.php?keywords=AirSnort)

edit: can get a bit further along but then a roadblock so to speak. A quick search shows
[http://ubuntuforums.org/showthread.php?t=851621&page=2](http://ubuntuforums.org/showthread.php?t=851621&page=2)

use the .deb link above for hardy or some other app

---

### Post by l0fls on 2008-08-04
even after i used .deb to install how to i find the application to open and run airsnort

---

### Post by ibuclaw on 2008-08-04
open a terminal and type in:
```
airsnort
```
or "air" and press the tab key twice to auto-complete or show a list of possible commands.

Regards
Iain

---

### Post by Titan8990 on 2008-08-04
Also there "whereis" command can be useful here. Example:

jordan@einstein:~$ whereis wireshark
wireshark: /usr/bin/wireshark /usr/lib/wireshark /usr/share/wireshark /usr/share/man/man1/wireshark.1.gz

---

