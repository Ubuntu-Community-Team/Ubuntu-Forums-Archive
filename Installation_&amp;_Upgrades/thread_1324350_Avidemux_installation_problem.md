---
title: "Avidemux installation problem"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by coucoucbm on 2009-11-12
Hi everybody,
I tried to install Avidemux using this tutorial/thread ([http://ubuntuforums.org/showthread.php?t=203898](http://ubuntuforums.org/showthread.php?t=203898)) but when I reached this command:

[COLOR="Red"]make -f Makefile.dist[/COLOR]

this is what i got:

[COLOR="Red"]mohamed@mohamed-laptop:~/avidemux_2.4_branch$ make -f Makefile.distThis Makefile is only for the CVS repository
This will be deleted before making the distribution

*** Version check disabled ***
*** Creating acinclude.m4
make[2]: Entering directory `/home/mohamed/avidemux_2.4_branch'
make[2]: Leaving directory `/home/mohamed/avidemux_2.4_branch'
*** Creating list of subdirectories
make[2]: Entering directory `/home/mohamed/avidemux_2.4_branch'
cd . && make -f admin/Makefile.common subdirs
make[3]: Entering directory `/home/mohamed/avidemux_2.4_branch'
make[3]: Leaving directory `/home/mohamed/avidemux_2.4_branch'
make[2]: Leaving directory `/home/mohamed/avidemux_2.4_branch'
*** Creating configure.files
*** Creating configure.in
make[2]: Entering directory `/home/mohamed/avidemux_2.4_branch'
cd . && make -f admin/Makefile.common configure.in ;
make[3]: Entering directory `/home/mohamed/avidemux_2.4_branch'
make[3]: Leaving directory `/home/mohamed/avidemux_2.4_branch'
make[2]: Leaving directory `/home/mohamed/avidemux_2.4_branch'
*** Creating aclocal.m4
./admin/cvs.sh: 601: aclocal: not found
make[1]: *** [cvs] Error 1
make: *** [all] Error 2
mohamed@mohamed-laptop:~/avidemux_2.4_branch$ 
[/COLOR]

Any help on how to fix this? I'm using Intrepid
thanks

---

### Post by SadaraX on 2009-11-16
Hello coucoubm.

I can see a couple of problems with your attempt to install.  What version of Ubuntu are you running? (Because if it is recent, you may be doing extra work that you do not need.)

If you just want the program (and you don't care about compiling it yourself), [you can usually just install it]("http://www.avidemux.org/admWiki/index.php?title=Install_Ubuntu").

The current stable version of Avidemux is 2.5, [which has a tutorial here which I just updated]("http://www.avidemux.org/admWiki/index.php?title=Install_2.5#Manually_Getting_Dependencies_.28Linux_Only.29") ([http://www.avidemux.org/admWiki/index.php?title=Install_2.5#Manually_Getting_Dependencies_.28Linux_Only.29](http://www.avidemux.org/admWiki/index.php?title=Install_2.5#Manually_Getting_Dependencies_.28Linux_Only.29)).

If this information does not help, reply to the thread with more information.

---

