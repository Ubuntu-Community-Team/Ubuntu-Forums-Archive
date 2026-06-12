---
title: "[SOLVED] error at make Ksynaptics? help"
date: 2008-08-20
forum: Hardware
---

### Post by desideratha on 2008-08-20
Hi all

I am trying to isntall ksynaptics to controll my touchpad in a laptop 
after many tries and having to install libraries I get this message


In if /bin/bash ../../libtool --silent --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/include/kde -I/usr/share/qt3/include -I.  -I/usr/include/synaptics  -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION  -MT ksynaptics.lo -MD -MP -MF ".deps/ksynaptics.Tpo" -c -o ksynaptics.lo ksynaptics.cpp; \
	then mv -f ".deps/ksynaptics.Tpo" ".deps/ksynaptics.Plo"; else rm -f ".deps/ksynaptics.Tpo"; exit 1; fi
In file included from ksynaptics.cpp:29:
touchpad.h:27:23: error: synaptics.h: No such file or directory
In file included from ksynaptics.cpp:29:
touchpad.h:29: error: 'Synaptics' is not a namespace-name
touchpad.h:29: error: expected namespace-name before ';' token
touchpad.h:47: error: 'TapType' has not been declared
touchpad.h:59: error: 'ScrollTrigger' does not name a type
touchpad.h:60: error: 'Button' does not name a type
touchpad.h:71: error: 'TapType' has not been declared
touchpad.h:81: error: 'ScrollTrigger' has not been declared
touchpad.h:82: error: 'TapType' has not been declared
touchpad.h:82: error: 'Button' has not been declared
make: *** [ksynaptics.lo] Error 1

Please help

thanks

---

### Post by desideratha on 2008-08-20
Actually I got it to compile, before I was missing a bunch o lib
however after ./configure, make and make install I get this messange


*************** Important *************************

This module contains unreleased software.

The software may compile and work, but it may just
as well neither compile nor work.

****************************************************

make[2]: Leaving directory `/home/andres/ksynaptics-0.3.3'

and the program never loads when I invoke ksynaptics at a command line

what am I doing wrong=?

---

### Post by LateNiteTV on 2008-08-20
> **desideratha said:**
> Actually I got it to compile, before I was missing a bunch o lib
however after ./configure, make and make install I get this messange


*************** Important *************************

[B]This module contains unreleased software.

The software may compile and work, but it may just
as well neither compile nor work.[/B]
****************************************************

make[2]: Leaving directory `/home/andres/ksynaptics-0.3.3'

and the program never loads when I invoke ksynaptics at a command line

what am I doing wrong=?

id say thats pretty self explanitory.

---

### Post by desideratha on 2008-08-20
I understand that, so how can I disable my touchpad? if neither ksynaptics nor qsynaptics seem to work in Kde4?

thanks

---

