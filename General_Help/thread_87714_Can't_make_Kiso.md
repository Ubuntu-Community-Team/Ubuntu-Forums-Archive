---
title: "Can't make Kiso"
date: 2005-11-08
forum: General Help
---

### Post by slimg on 2005-11-08
When i execute "make" in kiso folder after a successful ./config i get this error, im a noob so i really have a hard time understanding the error, seems to me that the gpp headers in the make script is outdated, heres the output:

robert@lisa:~/kiso-0.8.2.1$ make
Makefile:819: warning: overriding commands for target `clean-bcheck'
Makefile:797: warning: ignoring old commands for target `clean-bcheck'
Makefile:824: warning: overriding commands for target `bcheck-am'
Makefile:802: warning: ignoring old commands for target `bcheck-am'
Makefile:856: warning: overriding commands for target `clean-bcheck'
Makefile:819: warning: ignoring old commands for target `clean-bcheck'
Makefile:861: warning: overriding commands for target `bcheck-am'
Makefile:824: warning: ignoring old commands for target `bcheck-am'
make  all-recursive
make[1]: Entering directory `/home/robert/kiso-0.8.2.1'
Makefile:819: warning: overriding commands for target `clean-bcheck'
Makefile:797: warning: ignoring old commands for target `clean-bcheck'
Makefile:824: warning: overriding commands for target `bcheck-am'
Makefile:802: warning: ignoring old commands for target `bcheck-am'
Makefile:856: warning: overriding commands for target `clean-bcheck'
Makefile:819: warning: ignoring old commands for target `clean-bcheck'
Makefile:861: warning: overriding commands for target `bcheck-am'
Makefile:824: warning: ignoring old commands for target `bcheck-am'
Making all in doc
make[2]: Entering directory `/home/robert/kiso-0.8.2.1/doc'
Making all in .
make[3]: Entering directory `/home/robert/kiso-0.8.2.1/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/robert/kiso-0.8.2.1/doc'
Making all in en
make[3]: Entering directory `/home/robert/kiso-0.8.2.1/doc/en'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/robert/kiso-0.8.2.1/doc/en'
Making all in de
make[3]: Entering directory `/home/robert/kiso-0.8.2.1/doc/de'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/robert/kiso-0.8.2.1/doc/de'
make[2]: Leaving directory `/home/robert/kiso-0.8.2.1/doc'
Making all in po
make[2]: Entering directory `/home/robert/kiso-0.8.2.1/po'
rm -f hu.gmo; : -o hu.gmo ./hu.po
test ! -f hu.gmo || touch hu.gmo
make[2]: Leaving directory `/home/robert/kiso-0.8.2.1/po'
Making all in src
make[2]: Entering directory `/home/robert/kiso-0.8.2.1/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wwrite-strings -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -MT dirops.o -MD -MP -MF ".deps/dirops.Tpo" -c -o dirops.o dirops.cpp; \
then mv -f ".deps/dirops.Tpo" ".deps/dirops.Po"; else rm -f ".deps/dirops.Tpo"; exit 1; fi
dirops.cpp:7:26: error: cdio/iso9660.h: Ingen slik fil eller filkatalog
In file included from /usr/include/c++/4.0.2/backward/iostream.h:31,
                 from dirops.cpp:24:
/usr/include/c++/4.0.2/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
dirops.cpp: In function &#8216;QString readoutheader(QString, QString)&#8217;:
dirops.cpp:371: error: &#8216;iso9660_t&#8217; was not declared in this scope
dirops.cpp:371: error: &#8216;p_iso&#8217; was not declared in this scope
dirops.cpp:372: error: &#8216;iso9660_open&#8217; was not declared in this scope
dirops.cpp:377: error: &#8216;iso9660_ifs_get_volume_id&#8217; was not declared in this scope
dirops.cpp:378: error: &#8216;iso9660_ifs_get_system_id&#8217; was not declared in this scope
dirops.cpp:379: error: &#8216;iso9660_ifs_get_publisher_id&#8217; was not declared in this scope
dirops.cpp:380: error: &#8216;iso9660_ifs_get_preparer_id&#8217; was not declared in this scope
dirops.cpp:381: error: &#8216;iso9660_ifs_get_application_id&#8217; was not declared in this scope
make[2]: *** [dirops.o] Error 1
make[2]: Leaving directory `/home/robert/kiso-0.8.2.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/robert/kiso-0.8.2.1'
make: *** [all] Error 2

---

### Post by mlomker on 2005-11-09
It isn't you.  I've seen a couple threads regarding that package and it doesn't look like it will compile on Ubuntu.

---

### Post by slimg on 2005-11-12
Thanks to another thread i found my solution:

Installed the [kiso deb]("http://www.podulator.com/debs/kiso/kiso_0.8.2-1_i386.deb")
and installed the currently unstable but necessary [libiso9660-4]("http://packages.debian.org/unstable/libs/libiso9660-4")

---

