---
title: "Streamtuner"
date: 2008-09-13
forum: General Help
---

### Post by jamillikan on 2008-09-13
For whatever reason, streamtuner now shows blank entries.  I understand this is because of a change in Shoutcast.  Could someone please find a solution and post it here?

Thanks.  This is an urgent request.

:guitar:

---

### Post by AlesUbu123 on 2008-09-13
Oh no... :frown:
I feared this moment. Unfortunately, streamtuner development stopped last december. I hope someone with enough knowledge will look into this soon. 
In the meanwhile you could try tunapie and amarok's shoutcast abilities - if they work.

BR.

---

### Post by KevNice on 2008-09-15
The one for Amarok works, and it is actually a bit better. Waaaay more genres and stations to choose from.

---

### Post by jamillikan on 2008-09-15
Thank you.  I tried your suggestion and, yes, it is better.  I appreciate your tip.:guitar:

---

### Post by wobster on 2008-09-17
I read that the shoutcast plugin accesses "http://www.shoutcast.com". Changing the URL in the sources to "http://classic.shoutcast.com/"
works like a charm.

---

### Post by jamillikan on 2008-09-17
How do you do that, please?

---

### Post by mocha on 2008-09-20
[http://bugs.archlinux.org/task/11463?project=1&order=dateopened&sort=desc]("http://bugs.archlinux.org/task/11463?project=1&order=dateopened&sort=desc")

Some brief instructions to fix this:

sudo su (become root)
apt-get build-dep streamtuner
apt-get source streamtuner
cd streamtuner....
download patch in above link to streamtuner dir
patch -p1 < name_of_patchfile
./configure
make
make install

---

### Post by jamillikan on 2008-09-20
Thank you.  I can verify this works like a charm with Gutsy.  You rock!  You simply don't know how much I appreciate this.

I got the source from the Ubuntu repositories, applied the patch following your directions, then did ./configure, make, sudo make install and I was good as new!

Whew!  What a relief.  In the meantime, I was using Tunapie and Audacious which work great, too, for those interested.  Perhaps Streamtuner is the forerunner of Tunapie and I have the feeling XMMS may have been the forerunner of Audacious.  Who knows?  But now both work and you are the best!

---

### Post by DOUGman on 2008-09-21
Works great in Hardy..

---

### Post by brisamrus on 2008-09-22
Thanks for the info. Would it be possible to expand on the solution just a little. When I try it in Hardy, I run into trouble with the first command. Not sure what I'm missing. Any suggestions? Thanks.

> apt-get build-dep streamtuner
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Build-dependencies for streamtuner could not be satisfied.

---

### Post by bigjig on 2008-09-23
Hi, Can someone please help me on this? I am desperate to get this working.
I have been using linux for a while but still am a amateur.

I have followed the above instructions but the get some errors and I dont know how to get any further. Looking for some help soon, Cheers.

jig@Demon:~/Desktop# apt-get source streamtuner
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for streamtuner

jig@Demon:~/Desktop$ cd streamtuner-0.11.0/
jig@Demon:~/Desktop/streamtuner-0.11.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fl32... no
checking for af77... no
checking for fort77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for lf95... no
checking for g95... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
appending configuration tag "F77" to libtool
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... no
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking for string.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking for sys/types.h... (cached) yes
checking for sys/stat.h... (cached) yes
checking regex.h usability... yes
checking regex.h presence... yes
checking for regex.h... yes
checking for unistd.h... (cached) yes
checking for strcmp... yes
checking for strlen... yes
checking for strcpy... yes
checking for getopt... yes
checking for rename... yes
checking for unlink... yes
checking for mkdir... yes
checking for m4... m4
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.0.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error: unable to find the GLib library
jig@Demon:~/Desktop/streamtuner-0.11.0$ apt-get build-dep streamtuner
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
jig@Demon:~/Desktop/streamtuner-0.11.0$ sudo apt-get build-dep streamtuner
[sudo] password for jig: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for streamtuner
jig@Demon:~/Desktop/streamtuner-0.11.0$ apt-get source streamtuner
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for streamtuner
jig@Demon:~/Desktop/streamtuner-0.11.0$ sudo apt-get source streamtuner
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for streamtuner
jig@Demon:~/Desktop/streamtuner-0.11.0$ sudo apt-get build-dep streamtuner
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for streamtuner
jig@Demon:~/Desktop/streamtuner-0.11.0$ ./config
bash: ./config: No such file or directory
jig@Demon:~/Desktop/streamtuner-0.11.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fl32... no
checking for af77... no
checking for fort77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for lf95... no
checking for g95... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
appending configuration tag "F77" to libtool
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... no
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking for string.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking for sys/types.h... (cached) yes
checking for sys/stat.h... (cached) yes
checking regex.h usability... yes
checking regex.h presence... yes
checking for regex.h... yes
checking for unistd.h... (cached) yes
checking for strcmp... yes
checking for strlen... yes
checking for strcpy... yes
checking for getopt... yes
checking for rename... yes
checking for unlink... yes
checking for mkdir... yes
checking for m4... m4
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.0.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error: unable to find the GLib library
jig@Demon:~/Desktop/streamtuner-0.11.0$ make
make: *** No targets specified and no makefile found. Stop.

---

### Post by mocha on 2008-09-23
To the person that can't get the build dependancies, do you not have all of the repositories enabled??  I think that may be the problem, probably some of the build deps are in "restricted" or "multiverse" or whatever they call them.  You can enable all of the repositories though Synaptic.  Another thing, you need to be root to do this.  That's why I said to do sudo su before proceeding, or you can just run all the commands with sudo before them.

To the other posters that mentioned Tunapie, are you using the version from the Hardy repository?  Because I had the same problem with it not getting the Shoutcast listings so I grabbed the source and changed "www.shoutcast.com" to "classic.shoutcast.com" in 2 different source files then compiled it and the listings started working again.  It's strange that you did not have problems with it even after the Shoutcast server name change..

---

### Post by etnlIcarus on 2008-09-27
*Bump* 

Could someone compile a list of streamtuner-like apps, please? Preferably something which is presently maintained?

I tried tunepie but I'm not particularly fond of it.

---

### Post by jamillikan on 2008-09-27
You might want to try Amarok.  Tunapie uses Audacious to play which is also very XMMS-like.  Amarok and Audacious are both nice.  

Hope this helps!

---

### Post by etnlIcarus on 2008-09-28
Tunepia can play using whatever audio app you set it to. That said, Tunapie has a horrible interface.

As for Amarok, I'm really trying to avoid having to run the Qt libs and, in the case of Amarok; install half of KDE.

---

### Post by jamillikan on 2008-09-28
Oh, I'm sorry you feel that way but wish you the best with your efforts.

Be well.

---

### Post by lunadog on 2008-12-11
> **etnlIcarus said:**
> Tunepia can play using whatever audio app you set it to. That said, Tunapie has a horrible interface.

As for Amarok, I'm really trying to avoid having to run the Qt libs and, in the case of Amarok; install half of KDE.

Sorry to resurrect an old thread, but as the author of Tunapie, I would be grateful if you could say how the GUI is horrible, so it could be fixed.. I take it you have used the new version (2.x)?

I have tried to make the gui as easy as possible so everything you need is on one screen, and only less used features are hidden as context menus.

James

Edit: personally I think the way search "works" in Streamtuner is completely odd and unintuitive, but each to their own!

---

### Post by etnlIcarus on 2008-12-11
> **lunadog said:**
> Sorry to resurrect an old thread, but as the author of Tunapie, I would be grateful if you could say how the GUI is horrible, so it could be fixed.. I take it you have used the new version (2.x)?

I have tried to make the gui as easy as possible so everything you need is on one screen, and only less used features are hidden as context menus.

James

Edit: personally I think the way search "works" in Streamtuner is completely odd and unintuitive, but each to their own!

Well it's been a few months so I don't really remember much but as a starting point, I do recall it used wxwidgets, which does a pretty horrible job of emulating gtk+ widgets and settings. Honestly don't remember much of tunepie besides that.

That said, I've never claimed Streamtuner to be perfect, either.

---

### Post by lunadog on 2008-12-11
> **etnlIcarus said:**
> Well it's been a few months so I don't really remember much but as a starting point, I do recall it used wxwidgets, which does a pretty horrible job of emulating gtk+ widgets and settings. Honestly don't remember much of tunepie besides that.

That said, I've never claimed Streamtuner to be perfect, either.


Yes.. I guess that won't be changing for a while as it was written using Boa Constructor which also uses wxPython.. 

Ah well.. maybe someday I will look at recoding it with pygtk.. I have helped with the Aldrin project which uses that toolkit, so it should be possible! :)

James

---

### Post by etnlIcarus on 2008-12-11
Okay, thought I'd go against being lazy for once and give tunapie another whirl.

[[IMG]http://img184.imageshack.us/img184/116/streampiero0.th.png[/IMG]](http://img184.imageshack.us/img184/116/streampiero0.png)

Note scale widgets, text entry fields, statusbar, some fonts, etc aren't even close to native. Not your fault but that is a limitation of wxwidgets. Listview headers are also off, I just noticed.

Toolbar is off as well. Can't configure text labels or turn the toolbar off (my personal preference).

Even if I could turn off the toolbar, there'd be no point as none of the functionality has been replicated in the menubar.

Can't configure listview headers; turning columns on/off and reordering them.

Not being able to tab between different streaming services (having to open preferences to change servers) also seems to be a weakness.

Now, for functionality above and beyond (ie something both tunapie and streamtuner could do with):

A search-field in the main UI.

Internal playback (perhaps through something standard like gstreamer).

A dynamic, "Most listened to", and, "Recent/History", list. You tend to browse streams in a similarly flippant manner to web-browsing; you're conservative in bookmarking/favouriting and you just know you're going to skip past something awesome and never find it again. Modern web-browsers, luckily, keep both history and your most visited sites for easy access.

---

### Post by lunadog on 2008-12-11
> **etnlIcarus said:**
> Okay, thought I'd go against being lazy for once and give tunapie another whirl.

[[IMG]http://img184.imageshack.us/img184/116/streampiero0.th.png[/IMG]](http://img184.imageshack.us/img184/116/streampiero0.png)

Note scale widgets, text entry fields, statusbar, some fonts, etc aren't even close to native. Not your fault but that is a limitation of wxwidgets. Listview headers are also off, I just noticed.

Toolbar is off as well. Can't configure text labels or turn the toolbar off (my personal preference).

Even if I could turn off the toolbar, there'd be no point as none of the functionality has been replicated in the menubar.

Can't configure listview headers; turning columns on/off and reordering them.

Not being able to tab between different streaming services (having to open preferences to change servers) also seems to be a weakness.

Now, for functionality above and beyond (ie something both tunapie and streamtuner could do with):

A search-field in the main UI.

Internal playback (perhaps through something standard like gstreamer).

A dynamic, "Most listened to", and, "Recent/History", list. You tend to browse streams in a similarly flippant manner to web-browsing; you're conservative in bookmarking/favouriting and you just know you're going to skip past something awesome and never find it again. Modern web-browsers, luckily, keep both history and your most visited sites for easy access.

Good points. I will add your suggestions to the TODO.

James

---

