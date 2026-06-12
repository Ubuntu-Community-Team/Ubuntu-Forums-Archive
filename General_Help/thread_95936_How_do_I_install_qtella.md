---
title: "How do I install qtella?"
date: 2005-11-27
forum: General Help
---

### Post by charlie2900 on 2005-11-27
I just installed ubuntu 5.10.. This is the first time i've used anything other than windows. Everything has been ok so far.. I want to install qtella file sharing, my question is how do i create a directory file and install the program, since there is no exe file to run from.. Sorry, but im just confused with this. Thx

---

### Post by aysiu on 2005-11-27
I'd say follow the instructions on the [qtella website](http://qtella.sourceforge.net/): > Installation
Since the Qtella package uses automake and autoconf, compilation and installation of Qtella is quite easy. All you need are the Qt libraries compiled with thread support. You can check whether these libraries exists by typing "locate qt-mt". If locate does not list the libraries you need to download Qt from [http://www.trolltech.com](http://www.trolltech.com) and compile it with thread support first. If Qt is compiled with thread support, you are able to compile and install Qtella as follows:

1. tar xzf qtella-VERSION.tar.gz
2. cd qtella-VERSION
3. ./configure
4. make
5. make install (as root)

You are now able to run Qtella by typing "qtella". When starting Qtella for the first time you should open the configuration tab first. Here you can configure the directory names for completed and incompleted downloads, the maximum number of uploads, etc.  If you run into problems, ask here.

---

### Post by gwenbasil on 2006-05-10
Hey -- I searched 'qtella' and found *other* issues but not my issue. I'm new to linux, so I'm unused to anything but windows' very automatic installations.

When I configure, I get this error:
> checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/ben-kokolios/qtella-0.7.0/missing: Unknown `--run' option
Try `/home/ben-kokolios/qtella-0.7.0/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for ranlib... :
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details.


C++ complier cannot create executables? From my lay-pov, that seems like that may cause/be causing other past or future installation issues as well...

Thanks for any help.

---

### Post by gwenbasil on 2006-05-10
never mind... another thread solved that problem... I've notched up to the 
> Qt's moc not found! If you have installed Qt in an
unusual place, please use the "--with-qt-moc=" option

issue, now, that seems to be flummoxing a handful of folks on a related thread. Thanks anyway.

---

