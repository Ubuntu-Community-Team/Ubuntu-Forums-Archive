---
title: "Building c++ software using automake and g++"
date: 2005-11-11
forum: General Help
---

### Post by kristian on 2005-11-11
Ever since updating to breezy and after a reinstall with breezy I've had problems to build c++ software with automake and g++.

Example:
If I build a simple program with g++ signal.cc main.cc -o simple everything is fine. But when I use automake to build it I get strange errors like:
./signal.h:22: error: field '_message' has incomplete type
./signal.h:14: error: default argument for parameter of type 'std::string' has type 'const char [1]'

I've also recieved some hundreed lines of errors regarding the standard c++ headers in other projects.

Anyone that can help me?

---

### Post by nszabolcs on 2005-11-11
very strange

do you have more than one gcc installed?
what is the version of automake?

---

### Post by nagilum on 2005-11-11
It's hard to tell what goes wrong without knowing the source and your Makefile.am and configure.ac files.

---

### Post by kristian on 2005-11-11
I have only have one gcc version installed (4.0.2) and automake 1.9.6-1

configure.in:
AC_INIT(src/main.cc)
AC_CONFIG_AUX_DIR(scripts)
AM_INIT_AUTOMAKE(testProject, 0.0.1)
AM_CONFIG_HEADER(src/config.h)

AC_PROG_LIBTOOL
AC_PROG_INSTALL
AC_PROG_MAKE_SET

AC_PROG_CXX
AC_LANG_CPLUSPLUS

AC_HEADER_STDC

AC_OUTPUT([
Makefile
src/Makefile
src/tools/Makefile
])

src/tools/Makefile.am:
noinst_HEADERS = exception.h i18n.h reciever.h remote.h signal.h thread.h
noinst_LTLIBRARIES = libTools.la

libTools_la_SOURCES = \
        exception.cc \
        remote.cc \
        signal.cc

signal.h:
#ifndef _SIGNAL_H
#define _SIGNAL_H

#include <string>

class Signal
{
        public:
                Signal(unsigned int type, std::string message = "");
                ~Signal();

                unsigned int getType();
                std::string getMessage();

        private:
                unsigned int _type;
                std::string _message;
};

#endif

---

### Post by nagilum on 2005-11-13
Looks ok to me and the source itself compiles fine. If I use automake there are dozens lines of errors regarding the c++ std headers, as you described. I'm afraid I can't help you with this since I've never built libraries with c++ before, sorry.

---

### Post by nszabolcs on 2005-11-13
i'm not familiar with automake, but this should work fine.
can it be that automake defines some macros that mess with the c++ std lib ?

---

