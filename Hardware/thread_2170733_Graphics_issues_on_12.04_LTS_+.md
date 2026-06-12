---
title: "Graphics issues on 12.04 LTS +"
date: 2013-08-27
forum: Hardware
---

### Post by alex fisher on 2013-08-27
Hi, I've been without Linux on my main machine (Dell Dimension - AMD Athlon 64x2 5600+ 2.8GHz) for a several of months due to a graphics issue after a os 12.04 LTS re-install.
I've tried multiple re-installs with various versions but always get bad graphics issues e.g. screen has colour blocks, Firefox locks when scrolling. On several occasions  I've had an error similar to:

Sorry, Ubuntu 12.04 has experienced an internal error - details:
EXECUTABLE PATH: /usr/lib/gnome-disk-utility/gdu-notification-daemon
PACKAGE: gnome-disk-utility 3.0.2-2ubuntu7
PROBLEM TYPE: Crash
TITLE: gdu-notification-daemon crashed with signal 5 in_libc_start_main()
APPORTVERSION: 2.0.1-0ubuntu17.1
ARCHITECTURE: i386
COREDUMP
CRASHCOUNTER: 1
DATE: Sat Jul 20
DEPENDICIES
DISASSEMBLY
DISTRORELEASE: Ubuntu 12.04
INSTALLATION MEDIA: Ubuntu 12.04.2 LTS "Precise Pangolin"-Release i386(20130212)
MARK FOR UPLOAD: True
NONFREE KERNEL MODULES: nvida
PACKAGE ARCHITECTURE: i386
PROCCMDLINE: /usr/lib/gnome-disk-utility/gdu-notification-daemon
PROCENVIRON: LANGUAGE=en_GB:en, PATH=(custom, no user), LANG=en_GB.UTF-8, SHELL=/bin/bash
PROCMAPS
PROCSTATUS
PROCVERSIONSIGNATURE: Ubuntu 3.5.0-23-35~precise1-generic 3.5.7.2
REGISTERS
SIGNAL: 5
SOURCEPACKAGE: gnome-disk-utility
STACKTRACE
STACKTRACETOP: ??(), _libc_start_main() from /lib/i386-linux-gnu/libc.so.6, ??()
TAGS: precise running-unity
THREADSTACKTRACE
UNAME: Linux 3.5.0-23-generic i686
UNREPORTABLEREASON: You have some obsolete package versions installed. Please upgrade the following packages & check if the problem still occurs:

dbus, dbus-x-11, dmsetup, libc-bin, libc6, libcups2, libdbus-1-3, libdbus-glib-1-2, libdevmapper-event1.02.1, libdevmapper1.02.1, libdrm-intel1, libdrm-nouveau1a, libdrm-radeon1, libdrm2, libgnutls26, libgudev-1.0-0, liblvm2app2

Any ideas really appreciated - Alex.

---

