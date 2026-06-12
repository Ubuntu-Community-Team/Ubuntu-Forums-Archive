---
title: "Could not compile kdesvn 1.0.5"
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by VMbuseck on 2009-06-03
Because of a change in the format the version 1.0.4 from the ubuntu packages is no longer compatible with tortoise svn 1.6.2.

For that reason I tried to compile 1.0.5 from the sources:

```
root@xxxx:/data/software/kdesvn-1.0.5# cmake /data/software/kdesvn-1.0.5
-- Found KDE3 include dir: /usr/include/kde
-- Found KDE3 library dir: /usr/lib
-- Found KDE3 dcopidl preprocessor: /usr/bin/dcopidl
-- Found KDE3 dcopidl2cpp preprocessor: /usr/bin/dcopidl2cpp
-- Found KDE3 kconfig_compiler preprocessor: /usr/bin/kconfig_compiler
-- Found meinproc: /usr/bin/meinproc
-- Found gnu msgfmt: /usr/bin/msgfmt
CMake Error at src/svnqt/cmakemodules/FindSubversion.cmake:58 (MESSAGE):
  Error: no apu-config found
Call Stack (most recent call first):
  CMakeLists.txt:25 (INCLUDE)

.
.
.
```

But I could not find a **apu** package:

```
root@xxxx:/data/software/kdesvn-1.0.5# apt-cache search apu
katapult - item launcher for KDE
kanif - cluster management and administration swiss army knife
libi18n-charset-perl - Perl module for mapping character set names to IANA names
libunicode-maputf8-perl - Perl module for conversing between any character sets and UTF8
openmsx-catapult - GUI for openMSX
pcaputils - specialized libpcap utilities
wapua - Web browser for WAP WML pages
zope-ldapuserfolder - LDAP user and group source for Zope/Plone
```

Any suggestions ?

---

### Post by Partyboi2 on 2009-06-04
Hi, try installing the  libaprutil1-dev package
```
sudo apt-get install libaprutil1-dev
```

---

### Post by VMbuseck on 2009-06-04
Solved by installing the packages libaprutil1-dev and libsvn-dev.

Thanks a lot !

---

