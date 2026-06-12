---
title: "Intel HDA - Feisty Fawn SONY VAIO VGN Fe 41s"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by phifgo on 2007-05-01
I haVe  successfully deleted WINDOWS Vista and installed Feisty Fawn on my sony vaio laptop. everything works well, but my microphone doesn't work. I have an Intel HDA.soundcard

I've read on a guide, that I have to compile and install alsa-drdiver. alsa-utils, alsa-lib
I could install only the lib  and driver

when i compile  the alsa-utils package. the result is

>  
root@phifghetto:/usr/src/alsa/alsa-utils-1.0.14rc2# sh configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux
checking host system type... i686-pc-linux
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for cross-compiler... gcc
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.12... found.
checking for snd_ctl_open in -lasound... yes
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for initscr in -lncurses... no
checking for initscr in -lcurses... no
configure: error: this packages requires a curses library
root@phifghetto:/usr/src/alsa/alsa-utils-1.0.14rc2# 


can anybody hlep me?
Phifgo

thanks in advance

---

### Post by phifgo on 2007-05-01
I'd  executed  root@phifghetto:/usr/src/alsa/alsa-utils-1.0.14rc2# apt-get install curses*

and  after that I can configure (sh configure)
but now  when I execute "make"
it shows me  2 errors at the end
here is the make command output:
> 
root@phifghetto:/usr/src/alsa/alsa-utils-1.0.14rc2# make
Making all in include
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14rc2/include'
make  all-am
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14rc2/include'
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14rc2/include'
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14rc2/include'
Making all in alsactl
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14rc2/alsactl'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14rc2/alsactl'
Making all in alsaconf
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14rc2/alsaconf'
Making all in po
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14rc2/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14rc2/alsaconf/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14rc2/alsaconf'
make: *** [all-recursive] Error 1


help me plz
thank in advance
Phifgo

---

### Post by thorei on 2007-05-08
Hi, I had exactly the same problem. I don't know whether I had the problem with the missing curses library, but my output when doing make was the same. I'm running Feisty on my laptop but I have no sound with my ATI SB450 soundchip. I installed new alsa and I got the same error when I did the make of alsa-utils.
Try this:
make clean
then get the gettext package with synaptic or whatever (only gettext-base was installed by default)
then ./configure and make install, leave make out (apparently there's no need for it)
worked for me, I now have new alsa
I found that solution here:
[http://www.linuxquestions.org/questions/showthread.php?t=294058](http://www.linuxquestions.org/questions/showthread.php?t=294058)

---

