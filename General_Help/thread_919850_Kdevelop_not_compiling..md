---
title: "Kdevelop not compiling."
date: 2008-09-14
forum: General Help
---

### Post by JusticeJanitor on 2008-09-14
Allright, I pretty new to Kubuntu and C++ programing. The thing is, for once of my classes at university, I have to use a linux based OS and Kdevelop for C++ programing. Being a Windows guy (please don't kill me) I'me pretty lost here, I managed to install kubundu in dual-boot on my laptop. I also managed to instal Kdevelop, Autoconf and Automake. Now, when I try to compile a Simple Hello World Program, I get an Exited with Status 77 message. 

Here is the whole thing : 

cd '/home/vicot23/labos_cpp/xfgsdfg' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make -f Makefile.cvs && mkdir '/home/vicot23/labos_cpp/xfgsdfg/debug' && cd '/home/vicot23/labos_cpp/xfgsdfg/debug' && CXXFLAGS="-O0 -g3" "/home/vicot23/labos_cpp/xfgsdfg/configure" --enable-debug=full && cd '/home/vicot23/labos_cpp/xfgsdfg/debug/./src' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make -k xfgsdfg
aclocal
configure.in:8: warning: macro `AM_PROG_LIBTOOL' not found in library
autoheader
automake
autoconf
installing -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
configure: error: C++ compiler cannot create executables
See `config.log' for more details.
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... 
*** Exited with status: 77 ***

---

