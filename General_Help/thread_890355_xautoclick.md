---
title: "xautoclick"
date: 2008-08-15
forum: General Help
---

### Post by slushpuppy on 2008-08-15
Hi,
   I tried building xautoclick([http://sourceforge.net/projects/xautoclick/](http://sourceforge.net/projects/xautoclick/)) from source. However, it produces this, 
> Checking for c compiler ... gcc
Checking for c++ compiler ... g++
Checking for GNU Make ... yes, using make
Checking for extra headers ... no
Checking for extra libraries ... no
Checking for gcc support of -MM option ... yes
Checking for g++ support of -MM option ... yes
Checking for inttypes.h ... yes
Checking for unistd.h ... yes
Checking for malloc.h ... yes
Checking for X11 header presence ... yes (using /usr/include)
Checking for X11 ... yes (using -L/usr/X11R6/lib -lX11 -lXext)
Checking for XTest extension ... no
X11 found, but is does not seem to have the XTest extension
No X11 dependant applications will be build

Debug symbols disabled.
All compiler warnings disabled.

Cleaning up source tree ... done

Generating config.mak ... done.

aAutoClick    : no
cAutoClick    : no
gAutoClick    : no
gAutoClick2   : no
qtAutoClick   : no

Installation to /usr/local

Now type 'make' to build.

slush@slush-laptop:~/Desktop/xautoclick-0.19-src$ make
make: Nothing to be done for `all'.


I have installed libxext6 and build-essentials, fakeroot and devscripts.



Solved:
I used:
 sudo apt-get install xorg-dev
and it works

---

