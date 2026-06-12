---
title: "Installing kslimp3-1.0"
date: 2008-08-11
forum: General Help
---

### Post by xsilvergs on 2008-08-11
Hi
Still very new to Ubuntu but getting there.

I'm trying to install kslimp3 but having one last problem (I hope). I have ./configure and then it asks me to "make" so I make but get this message:

make  all-recursive
make[1]: Entering directory `/home/tony/kslimp3-1.0'
Making all in kslimp3
make[2]: Entering directory `/home/tony/kslimp3-1.0/kslimp3'
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -pedantic -W -Wpointer-arith -Wmissing-prototypes -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -O2 -fno-exceptions -fno-check-new  -MT vfdview.o -MD -MP -MF ".deps/vfdview.Tpo" \
	  -c -o vfdview.o `test -f 'vfdview.cpp' || echo './'`vfdview.cpp; \
	then mv -f ".deps/vfdview.Tpo" ".deps/vfdview.Po"; \
	else rm -f ".deps/vfdview.Tpo"; exit 1; \
	fi
cc1plus: warning: command line option "-Wmissing-prototypes" is valid for Ada/C/ObjC but not for C++
In file included from vfdview.cpp:27:
vfdview.h:67: error: extra &#8216;;&#8217;
make[2]: *** [vfdview.o] Error 1
make[2]: Leaving directory `/home/tony/kslimp3-1.0/kslimp3'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tony/kslimp3-1.0'
make: *** [all] Error 2

Can anybody help please?

---

### Post by xsilvergs on 2008-08-11
I've now made it worse. When I ./configure it finishes with:

checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE libraries installed. This will fail.
So, check this please and use another prefix!

How do I cure this please?

---

