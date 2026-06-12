---
title: "Problem Installing gyachi-1.1.0 in ubuntu 9.10"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by Apoorvbarwa on 2009-05-20
i downloaded gyachi-1.1.0.tar.gz after unpacking in the terminal i wrote

root@apoorv-desktop:/home/apoorv/gyachi-1.1.0# ./autogen.sh
this gives error
searching for GNU gettext intl directory...
 -> /usr/share/gettext/intl ... found it
copying gettext intl files ...
running aclocal ...
aclocal: configure.ac: 12: macro `AM_DISABLE_STATIC' not found in library
aclocal: configure.ac: 13: macro `AM_PROG_LIBTOOL' not found in library
aclocal: macro `AM_PROG_MKDIR_P' required but not defined
aclocal: macro `AM_PROG_MKDIR_P' required but not defined
aclocal: configure.ac: 25: macro `AM_PATH_GTK_2_0' not found in library
aclocal: configure.ac: 26: macro `AM_PATH_GLIB_2_0' not found in library
aclocal failed, stopping.
i dont know what this was so i downloaded the
gyachi-1.1.0-1.src.rpm
then i logged on as root 
in the terminal i wrote 
root@apoorv-desktop:/home/apoorv# rpm -i gyachi-1.1.0-1.src.rpm
then i got
warning: user hosler does not exist - using root
warning: group hosler does not exist - using root
warning: user hosler does not exist - using root
warning: group hosler does not exist - using root
Here firstly there is no user that i created by the name hosler so i dont know what is happening
I have Ubuntu 9.10 Interpid
Please help me out here.......with any of the two options

---

### Post by loell on 2009-05-20
the website isn't updated for a long time now, but you can have this package.

[gyachi_1.1.71-1~intrepid1_i386.deb]("http://https://launchpad.net/~loell/+archive/ppa/+files/gyachi_1.1.71-1~intrepid1_i386.deb")

---

