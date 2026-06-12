---
title: "Problem regarding configuring X server in ubuntu hardy"
date: 2009-09-16
forum: Installation &amp; Upgrades
---

### Post by amey1288 on 2009-09-16
Hello all ,

          I am configuring X server.I configured it by following the link below:

           [http://www.x.org/wiki/Development/git](http://www.x.org/wiki/Development/git)

          But when I started X server ( which was configured without any dependencies left)
          I encountered the following error:

         (EE) XKB: Couldn't open rules file /opt/gfx-test/share/X11/xkb/rules/base
         XKB: Failed to compile keymap 
         Keyboard initialization failed. This could be a missing or incorrect setup of         xkeyboard-config.

Fatal server error:
Failed to activate core devices.


So I tried to configure the xkeyboard-config package but faced the following error:

intltoolize: 'intltool-extract.in' exists: use '--force' to overwrite
intltoolize: 'intltool-merge.in' exists: use '--force' to overwrite
intltoolize: 'intltool-update.in' exists: use '--force' to overwrite
intltoolize: 'po/Makefile.in.in' exists: use '--force' to overwrite
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal 
configure.in:47: warning: macro `AM_GLIB_GNU_GETTEXT' not found in library
autoreconf: configure.in: tracing
autoreconf: configure.in: not using Libtool
autoreconf: running: /usr/bin/autoconf
autoreconf: configure.in: not using Autoheader
autoreconf: running: automake --add-missing --copy --no-force
rules/Makefile.am:184: `%'-style pattern rules are a GNU make extension
autoreconf: Leaving directory `.'
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for xkbcomp... /usr/bin/xkbcomp
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... none
checking for intltool >= 0.30... 0.37.1 found
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
./configure: line 3877: AM_GLIB_GNU_GETTEXT: command not found
configure: creating ./config.status
config.status: creating po/Makefile.in
config.status: creating Makefile
config.status: creating compat/Makefile
config.status: creating geometry/Makefile
config.status: creating geometry/digital_vndr/Makefile
config.status: creating geometry/sgi_vndr/Makefile
config.status: creating keycodes/Makefile
config.status: creating keycodes/digital_vndr/Makefile
config.status: creating keycodes/sgi_vndr/Makefile
config.status: creating keymap/Makefile
config.status: creating keymap/digital_vndr/Makefile
config.status: creating keymap/sgi_vndr/Makefile
config.status: creating keymap/sun_vndr/Makefile
config.status: creating semantics/Makefile
config.status: creating rules/Makefile
config.status: creating rules/bin/Makefile
config.status: creating rules/compat/Makefile
config.status: creating rules/extras/Makefile
config.status: creating symbols/Makefile
config.status: creating symbols/digital_vndr/Makefile
config.status: creating symbols/fujitsu_vndr/Makefile
config.status: creating symbols/hp_vndr/Makefile
config.status: creating symbols/macintosh_vndr/Makefile
config.status: creating symbols/nec_vndr/Makefile
config.status: creating symbols/sgi_vndr/Makefile
config.status: creating symbols/sony_vndr/Makefile
config.status: creating symbols/sun_vndr/Makefile
config.status: creating symbols/xfree68_vndr/Makefile
config.status: creating symbols/extras/Makefile
config.status: creating types/Makefile
config.status: creating xkeyboard-config.spec
config.status: creating docs/Makefile
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing po/stamp-it commands
config.status: error: po/Makefile is not ready.

I tried to install po but I faced errors for that also. So please help in this regard.

P.S. ( I am using ubuntu Hardy )

Thanks,
Amey

---

