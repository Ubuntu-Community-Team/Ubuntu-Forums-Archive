---
title: "Midnight Commander"
date: 2009-02-16
forum: Installation &amp; Upgrades
---

### Post by PFRules on 2009-02-16
**Hi everyone!**

I'm Mario and I'm newbie in Linux (Ubuntu to be precise).

I want to install Midnight Commander in my Intrepid Ibex (8.10) distro but **_I don't have Internet access_**. So I downloaded the required libraries in tar.gz format.

Dependencies are as follows:

**mc 4.6.1 --> glib 2.16.6 --> gettext 0.17**

I do ./configure gettext with the following output:

---------------------------------------------------
...
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating installpaths
config.status: creating po/Makefile
config.status: executing po-directories commands
---------------------------------------------------

But when I make, I get:

---------------------------------------------------
...
make[3]: leaving directory `/home/mds/src/req-lib/gettext-0.17/gettext-tools/gnulib-lib'
Making all in libgrep
make[3]: entering directory `/home/mds/src/req-lib/gettext-0.17/gettext-tools/libgrep'
make[3]: Did nothing at `all'.
make[3]: leaving directory `/home/mds/src/req-lib/gettext-0.17/gettext-tools/libgrep'
Making all in src
make[3]: entering directory `/home/mds/src/req-lib/gettext-0.17/gettext-tools/src'
make  all-am
make[4]: entering directory `/home/mds/src/req-lib/gettext-0.17/gettext-tools/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -std=gnu99 -DLOCALEDIR=\"/usr/local/share/locale\" -DBISON_LOCALEDIR=\"\" -DLOCALE_ALIAS_PATH=\"/usr/local/share/locale\" -DUSEJEXE=0 -DGETTEXTJEXEDIR=\"/usr/local/lib/gettext\" -DGETTEXTJAR=\"/usr/local/share/gettext/gettext.jar\" -DLIBDIR=\"/usr/local/lib\" -DGETTEXTDATADIR=\"/usr/local/share/gettext\" -DPROJECTSDIR=\"/usr/local/share/gettext/projects\" -DHAVE_CONFIG_H -I. -I..  -I. -I. -I.. -I.. -I../libgrep -I../gnulib-lib -I../gnulib-lib -I../intl -I../../gettext-runtime/intl   -g -O2 -c -o write-catalog.lo write-catalog.c
 gcc -std=gnu99 -DLOCALEDIR=\"/usr/local/share/locale\" -DBISON_LOCALEDIR=\"\" -DLOCALE_ALIAS_PATH=\"/usr/local/share/locale\" -DUSEJEXE=0 -DGETTEXTJEXEDIR=\"/usr/local/lib/gettext\" -DGETTEXTJAR=\"/usr/local/share/gettext/gettext.jar\" -DLIBDIR=\"/usr/local/lib\" -DGETTEXTDATADIR=\"/usr/local/share/gettext\" -DPROJECTSDIR=\"/usr/local/share/gettext/projects\" -DHAVE_CONFIG_H -I. -I.. -I. -I. -I.. -I.. -I../libgrep -I../gnulib-lib -I../gnulib-lib -I../intl -I../../gettext-runtime/intl -g -O2 -c write-catalog.c  -fPIC -DPIC -o .libs/write-catalog.o
In function 'open',
    inlined from 'msgdomain_list_print' at write-catalog.c:223:
/usr/include/bits/fcntl2.h:51: error: call to '__open_missing_mode' declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[4]: *** [write-catalog.lo] Error 1
make[4]: leaving directory `/home/mds/src/req-lib/gettext-0.17/gettext-tools/src'
make[3]: *** [all] Error 2
make[3]: leaving directory `/home/mds/src/req-lib/gettext-0.17/gettext-tools/src'
make[2]: *** [all-recursive] Error 1
make[2]: leaving directory `/home/mds/src/req-lib/gettext-0.17/gettext-tools'
make[1]: *** [all] Error 2
make[1]: leaving directory `/home/mds/src/req-lib/gettext-0.17/gettext-tools'
make: *** [all-recursive] Error 1
---------------------------------------------------

Obviously, when I try to ./configure glib, I get:

---------------------------------------------------
...
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... no
configure: error:
*** You must have either have gettext support in your C library, or use the
*** GNU gettext library. ([http://www.gnu.org/software/gettext/gettext.html](http://www.gnu.org/software/gettext/gettext.html)
---------------------------------------------------

Help please! What do I need to succesfully make mc???

Thanks in advance guys!

[B]Mario.
[email]mario_mds@hotmail.com[/email][/B]

P.S: I execute all of the above commands in 'sudo' mode.

---

### Post by Phlee on 2009-02-16
It looks like you need to install some dependencys before you will get it to compile correctly.

---

### Post by cariboo on 2009-02-16
Why not just go [here]("http://packages.ubuntu.com/intrepid/mc") and download the mc deb and dependencies? As well as the recommended files.

Jim

---

### Post by kerry_s on 2009-02-16
> **cariboo907 said:**
> Why not just go [here]("http://packages.ubuntu.com/intrepid/mc") and download the mc deb and dependencies? As well as the recommended files.

Jim

i agree, just put them all in the same place and run> sudo dpkg -i *.deb

---

