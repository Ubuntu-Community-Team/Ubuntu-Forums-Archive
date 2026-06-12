---
title: "hp dv9548us intel-hda mute light stuck on"
date: 2007-10-01
forum: Hardware &amp; Laptops
---

### Post by brokentire on 2007-10-01
I have Ubuntu 4.10-beta installed.

The sound card and drivers load ok.

However my mute light indicator beside my keyboard is ORANGE instead of blue thus my sound is muted....any idea's how to correct this? ps my multimedia remote doesn't correct this.

---

### Post by aldeby on 2007-10-02
Sorry I haven't understood if you can hear sounds when playing an mp3/ogg song or a movie or not.
In case you can hear sounds and music just swipe your finger on the light right after the laptop switches on and you will notice the light changes its colour. 
The fact is that linux currently does not handle well those switches colours, for example my wifi switch led is always amber, although wireless works perfectly.

In case you cannot hear any sound you probably have and Intel ICH8 chipset and you have to install manually the latest alsa drivers, unfortunately this is a very common and well known problem, fortunately the solution is as well easy. 

These commands will do the job and your light will definitely trun blue after unmuting the audio:

```
# apt-get update && apt-get install mercurial build-essential libncurses5 automake autoconf

$ hg clone [http://hg.alsa-project.org/alsa-driver](http://hg.alsa-project.org/alsa-driver) alsa-driver
$ hg clone [http://hg.alsa-project.org/alsa-kernel](http://hg.alsa-project.org/alsa-kernel) alsa-kernel

$ cd alsa-driver
$ ./hgcompile

$ sudo make install-modules

$ hg clone [http://hg.alsa-project.org/alsa-utils](http://hg.alsa-project.org/alsa-utils) alsa-utils
$ cd alsa-utils
$ ./hgcompile
$ sudo make install

$ sudo alsaconf

it may be worth removing ubuntu alsa module too 
$ sudo mv /lib/modules/2.6.22-12-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko /tmp
$ sudo depmod -a

now reboot

```

Have a nice cup of Ubuntu!

---

### Post by brokentire on 2007-10-02
everything worked but 'alsaconf' command not found


but at least now the light is blue....but the icon for speaker volume now shows its muted.

---

### Post by Ayuthia on 2007-10-02
> **brokentire said:**
> everything worked but 'alsaconf' command not found


but at least now the light is blue....but the icon for speaker volume now shows its muted.
This might be a dumb question, but have you clicked on the speaker icon to see which channel it is using?

---

### Post by brokentire on 2007-10-02
it says after double clicking:
No volume contr
l GStreamer plugins and/or devices found.

---

### Post by aldeby on 2007-10-02
i see, the amber light was there because no audio daemon was installed, now it is but since alsaconf did not configure the correct device and audio mixer you get that error.

Have you run these commands with sudo?
```

sudo make install-modules
sudo alsaconf
```

anyway I missed to tell you to install also** alsa-utils** **package** which brings you alsaconf tool

```

hg clone http://hg.alsa-project.org/alsa-utils alsa-utils
cd alsa-utils
./hgcompile
sudo make install

it may be worth removing ubuntu alsa module too 
$ sudo mv /lib/modules/2.6.22-12-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko /tmp
$ sudo depmod -a
```

you may also appreciate having a look at my blog for configuring other devices of HP Pavilion laptops [http://aldeby.wordpress.com/]("http://aldeby.wordpress.com/")

---

### Post by brokentire on 2007-10-02
I get this when I enter sudo make install:
(after ./hgcompile in the alsa-utils directory)

make: *** No rule to make target `install'.  Stop.

---

### Post by aldeby on 2007-10-02
it seems ./hgcompile had some problems compiling. 
Can you please doublecheck?
Delete alsa-utils directory and start again paying attention to the last lines shown after running ./hgcompile stops.

---

### Post by brokentire on 2007-10-02
./configure: line 6192: syntax error near unexpected token `1.0.12'
./configure: line 6192: `AM_PATH_ALSA(1.0.12)'

---

### Post by aldeby on 2007-10-02
uhm... seems that the problem is in the configure script. 
anyway I would try with the old version of alsa-utils via 
```
sudo apt-get install alsa-utils
``` 
and see if that enables you to configure you to configure your audio device.

---

### Post by brokentire on 2007-10-02
did:
sudo apt-get install alsa-utils
sudo alsaconf


still got:
sudo: alsaconf: command not found

---

### Post by aldeby on 2007-10-02
that's weird!
however I uploaded it here [http://ubuntuforums.org/attachment.php?attachmentid=45098&stc=1&d=1191335504]("http://ubuntuforums.org/attachment.php?attachmentid=45098&stc=1&d=1191335504")
in fact is just a script to configure your soundcard.
once you download it type **tar -xf alsaconf.tar ** and then** sudo ./alsaconf**

---

### Post by brokentire on 2007-10-02
nothing happens (apparently) when I try ./alsaconf

---

### Post by aldeby on 2007-10-02
ok, let's follow the INSTALL instructions step by step: 
since you have already installed the driver (I assume)

we are at step #6

go into alsa-driver folder, then

6) Run the './snddevices' script to create new sound devices in /dev directory.
   Skip this step, if you have already /dev/snd/* files, or if you're
   using a DEVFS or udev. 
(do not skip this)
```
sudo ./snddevices
```

go to alsa-utils folder, then type

```

cd alsaconf
chmod u+x alsaconf 
sudo ./alsaconf

```

this should be step #7

7) Edit your kernel module config (either /etc/modprobe.conf or
   /etc/modules.conf, depending on the kernel version). If you are not
   sure, what to do, you may try the alsaconf script available in
   the alsa-utils package.

If any error appears do no hesitate to post it.

---

### Post by brokentire on 2007-10-02
I am in the alsa-driver folder

but there is NO subdirectory of alsaconf

---

### Post by brokentire on 2007-10-02
did step 6
the directory of alsaconf is there

but the file to chmod isnt

---

### Post by aldeby on 2007-10-02
I guess we should make it.
type ```
make
```in alsaconf folder, then chmod it and run it

---

### Post by brokentire on 2007-10-02
after sudo make:
make: *** No targets specified and no makefile found.  Stop.

after ls:

alsaconf.8  alsaconf.fr.8  alsaconf.in  Makefile.am  Makefile.in  po

---

### Post by aldeby on 2007-10-02
uhm, there should have been also a file named **Makefile**,
have you run ./hgcompile in alsa-utils folder (its parent directory)?

---

### Post by brokentire on 2007-10-02
yes I have but still no Makefile

---

### Post by brokentire on 2007-10-02
there is a waring message when I do that in the parent directory....how would I give you the output when I execute that command?

---

### Post by aldeby on 2007-10-02
select the lines with the mouse and right click, then copy

---

### Post by aldeby on 2007-10-02
just for you to try, Realtek has released a bundled version of latest beta alsa drivers. If we don't manage to come to a conclusion just try and see if that works (sometimes does, but not everybody reported it to work).
Here is the link [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2")

---

### Post by brokentire on 2007-10-02
Copying file po/insert-header.sin
Copying file po/quot.sed
Copying file po/remove-potcdate.sin
Copying file m4/gettext.m4
Copying file m4/iconv.m4
Copying file m4/lib-ld.m4
Copying file m4/lib-link.m4
Copying file m4/lib-prefix.m4
Copying file m4/nls.m4
Copying file m4/po.m4
Copying file m4/progtest.m4
Updating configure.in (backup is in configure.in~)

Please run 'aclocal -I m4' to regenerate the aclocal.m4 file.
You need aclocal from GNU automake 1.9 (or newer) to do this.
Then run 'autoconf' to regenerate the configure file.

You might also want to copy the convenience header file gettext.h
from the /usr/share/gettext directory into your package.
It is a wrapper around <libintl.h> that implements the configure --disable-nls
option.

Press Return to acknowledge the previous two paragraphs.
configure.in:30: error: possibly undefined macro: AM_PATH_ALSA
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
CFLAGS=-O2 -Wall -pipe -g
./configure 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for cross-compiler... gcc
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
./configure: line 6192: syntax error near unexpected token `1.0.12'
./configure: line 6192: `AM_PATH_ALSA(1.0.12)'
brokentire@brokentire-laptop:~/alsa-utils$

---

### Post by aldeby on 2007-10-02
I really can't understand why it prompts you with that error.
Today snapshot should be broken.
You could try with a previous version, such as [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15rc1.tar.bz2]("ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15rc1.tar.bz2")

please save the file in a directory where there isn't another alsa-utils folder

```
tar xjf alsa-utils-1.0.15rc1.tar.bz2
cd alsa-utils
./configure
make 
sudo make install
```

then you should have installed alsaconf, or at least you should be able to find it in alsa-utils/alsaconf directory, or at least you should find the Makefile (since in rc1 version  the configure file is not broken)

---

### Post by brokentire on 2007-10-02
installing from [http://www.realtek.com.tw/downloads/...etDown=false#2](http://www.realtek.com.tw/downloads/...etDown=false#2)

then what?

---

### Post by brokentire on 2007-10-02
Libraries have been installed in:
   /usr/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/src'
make[2]: Leaving directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/src'
make[1]: Leaving directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/src'
Making install in modules
make[1]: Entering directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/modules'
Making install in mixer
make[2]: Entering directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/modules/mixer'
Making install in simple
make[3]: Entering directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/modules/mixer/simple'
make[4]: Entering directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/modules/mixer/simple'
test -z "/usr/lib/alsa-lib/smixer" || mkdir -p -- "/usr/lib/alsa-lib/smixer"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'smixer-sbase.la' '/usr/lib/alsa-lib/smixer/smixer-sbase.la'
libtool: install: warning: relinking `smixer-sbase.la'
(cd /home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/modules/mixer/simple; /bin/bash ../../../libtool  --tag=CC --mode=relink gcc -g -O2 -W -Wall -g -O2 -o smixer-sbase.la -rpath /usr/lib/alsa-lib/smixer -module -avoid-version sbase.lo ../../../src/libasound.la )
gcc -shared  .libs/sbase.o  -L/usr/lib -lasound  -Wl,-soname -Wl,smixer-sbase.so -o .libs/smixer-sbase.so
/usr/bin/install -c .libs/smixer-sbase.soT /usr/lib/alsa-lib/smixer/smixer-sbase.so
/usr/bin/install -c .libs/smixer-sbase.lai /usr/lib/alsa-lib/smixer/smixer-sbase.la
PATH="$PATH:/sbin" ldconfig -n /usr/lib/alsa-lib/smixer
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/alsa-lib/smixer

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'smixer-ac97.la' '/usr/lib/alsa-lib/smixer/smixer-ac97.la'
libtool: install: warning: relinking `smixer-ac97.la'
(cd /home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/modules/mixer/simple; /bin/bash ../../../libtool  --tag=CC --mode=relink gcc -g -O2 -W -Wall -g -O2 -o smixer-ac97.la -rpath /usr/lib/alsa-lib/smixer -module -avoid-version ac97.lo sbasedl.lo ../../../src/libasound.la )
gcc -shared  .libs/ac97.o .libs/sbasedl.o  -L/usr/lib -lasound  -Wl,-soname -Wl,smixer-ac97.so -o .libs/smixer-ac97.so
/usr/bin/install -c .libs/smixer-ac97.soT /usr/lib/alsa-lib/smixer/smixer-ac97.so
/usr/bin/install -c .libs/smixer-ac97.lai /usr/lib/alsa-lib/smixer/smixer-ac97.la
PATH="$PATH:/sbin" ldconfig -n /usr/lib/alsa-lib/smixer
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/alsa-lib/smixer

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'smixer-hda.la' '/usr/lib/alsa-lib/smixer/smixer-hda.la'
libtool: install: warning: relinking `smixer-hda.la'
(cd /home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/modules/mixer/simple; /bin/bash ../../../libtool  --tag=CC --mode=relink gcc -g -O2 -W -Wall -g -O2 -o smixer-hda.la -rpath /usr/lib/alsa-lib/smixer -module -avoid-version hda.lo sbasedl.lo ../../../src/libasound.la )
gcc -shared  .libs/hda.o .libs/sbasedl.o  -L/usr/lib -lasound  -Wl,-soname -Wl,smixer-hda.so -o .libs/smixer-hda.so
/usr/bin/install -c .libs/smixer-hda.soT /usr/lib/alsa-lib/smixer/smixer-hda.so
/usr/bin/install -c .libs/smixer-hda.lai /usr/lib/alsa-lib/smixer/smixer-hda.la
PATH="$PATH:/sbin" ldconfig -n /usr/lib/alsa-lib/smixer
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/alsa-lib/smixer

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/modules/mixer/simple'
make[3]: Leaving directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/modules/mixer/simple'
make[3]: Entering directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/modules/mixer'
make[4]: Entering directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/modules/mixer'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/modules/mixer'
make[3]: Leaving directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/modules/mixer'
make[2]: Leaving directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/modules/mixer'
make[2]: Entering directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/modules'
make[3]: Entering directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/modules'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/modules'
make[2]: Leaving directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/modules'
make[1]: Leaving directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/modules'
Making install in aserver
make[1]: Entering directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/aserver'
make[2]: Entering directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/aserver'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'aserver' '/usr/bin/aserver'
/usr/bin/install -c .libs/aserver /usr/bin/aserver
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/aserver'
make[1]: Leaving directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/aserver'
Making install in alsalisp
make[1]: Entering directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/alsalisp'
make[2]: Entering directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/alsalisp'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/alsalisp'
make[1]: Leaving directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/alsalisp'
Making install in test
make[1]: Entering directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/test'
make[2]: Entering directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/test'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/test'
make[1]: Leaving directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/test'
Making install in utils
make[1]: Entering directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/utils'
make[2]: Entering directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/utils'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/aclocal" || mkdir -p -- "/usr/share/aclocal"
 /usr/bin/install -c -m 644 'alsa.m4' '/usr/share/aclocal/alsa.m4'
test -z "/usr/lib/pkgconfig" || mkdir -p -- "/usr/lib/pkgconfig"
 /usr/bin/install -c -m 644 'alsa.pc' '/usr/lib/pkgconfig/alsa.pc'
make[2]: Leaving directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/utils'
make[1]: Leaving directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14/utils'
make[1]: Entering directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14'
make[2]: Entering directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14'
make[1]: Leaving directory `/home/brokentire/Desktop/realtek-linux-audiopack-4.06c/alsa-lib-1.0.14'
Compile ALSA Utility......
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for cross-compiler... gcc
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.12... found.
checking for snd_ctl_open in -lasound... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for initscr in -lncurses... no
checking for initscr in -lcurses... no
configure: error: this packages requires a curses library
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
Remove Folder.....
./install: 101: alsaconf: not found

---

### Post by aldeby on 2007-10-02
when you have unpacked the driver from realtek 
```
 tar xjf realtek-linux-audiopack-4.06c.tar.bz2
cd realtek-linux-audiopack-4.06
sudo ./install

```
follow the screen, eventually it should prompt you with alsaconf.
at the end you won't hear any sound, but after reboot try unmuting the speakers.

---

### Post by aldeby on 2007-10-02
OK it says you need ncurses-dev library
> 
configure: error: this packages requires a curses library


so type ```

sudo apt-get install libncurses5-dev
```
and try again

---

### Post by brokentire on 2007-10-02
after doing posting #28 got this error:

configure: error: this packages requires a curses library
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
Remove Folder.....
./install: 101: alsaconf: not found

---

### Post by aldeby on 2007-10-02
libncurses library is required, follow post 29 :)

---

### Post by brokentire on 2007-10-02
found card and configured

now going to reboot

---

### Post by brokentire on 2007-10-02
after running ./install it ran alsaconf found my card...rebooted...same prob...mute light orange not blue

---

### Post by aldeby on 2007-10-02
did you remember to delete ubuntu's module?

sudo mv /lib/modules/2.6.22-12-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko /tmp
sudo depmod -a

---

### Post by brokentire on 2007-10-02
did that

then tryed to run sudo alsaconf again.....still no sound and orange mute light

---

### Post by aldeby on 2007-10-02
unfortunately I have no more advices...

you might want to repeat these steps with latest drivers (the one you downloaded via **hg**) and then run alsaconf and depmod -a. 

you can get rid of the alsa-utils you downloaded via **hg** since today build is broken, and not useful at all.

also read INSTALL file you can find in alsa-driver folder.

usually when alsa drivers are installed correctly the light turns blue, it is amber only when there are issues with the drivers (muting the speakers via software currently does not turn it amber)

---

### Post by aldeby on 2007-10-02
have a look also in this thread:
[http://ubuntuforums.org/showthread.php?t=512059&goto=newpost]("http://ubuntuforums.org/showthread.php?t=512059&goto=newpost")

I can assure you that these problems with intel based HP Pavilion dv6*** and dv9*** will be definetly fixed by next release of alsa drivers, which I hope will be ready for 7.10 Ubuntu Gutsy.

---

