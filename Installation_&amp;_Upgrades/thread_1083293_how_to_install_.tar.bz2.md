---
title: "how to install .tar.bz2 ???"
date: 2009-02-28
forum: Installation &amp; Upgrades
---

### Post by Will4 on 2009-02-28
Hey guys, i need to install GParted and the package i just download is a .tar.bz2

how do i install it?? some help??

Thank you...

---

### Post by taurus on 2009-02-28
Gparted is in the repos so install it from there unless you have a reason to build it from source.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install gparted
gksudo gparted
```

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Will4 on 2009-02-28
Thanks taurus,

i just download last version of GParted from [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=125754](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=125754)

i wonder if i can install it? because the version i have 0.3.5 does not rename partitions. I have a 40 Gb HD and want to create a ntfs partition and i can't with the Gparted i have on 8.04. 
Some one said i could get the latest version and install it, is that possible?

Thanks

---

### Post by taurus on 2009-02-28
Did you remember to unmount the partition that you want to create a ntfs filesystem on?

Yes, you can remove the old version (that you installed from the repos) from your machine.  Then, build and install a newer version if you want.

---

### Post by Will4 on 2009-02-28
I did and nothing!! I think is for the version not having the feature. 
I would very much appreciate if you help me with the "build and install" thing because i don't know how to unpack a .tar.bz2 and install it. could you tell me??

Thank you...

---

### Post by taurus on 2009-02-28
Okay, remove the older version from your machine first either with synaptic, add/remove, or apt-get/aptitude.

Then, open a terminal and run, assuming you have saved gparted-0.4.3.tar.bz2 to your desktop.

```
cd ~/Desktop
tar xvjf gparted-0.4.3.tar.bz2
cd gparted-0.4.3
./configure
```
Post the whole output of the last command.

---

### Post by Will4 on 2009-02-28
after i

[FONT=monospace] [/FONT]> cd ~/Desktop
 tar xvjf gparted-0.4.3.tar.bz2[FONT=monospace]

as sudo of course
it says this

[/FONT]> gparted-0.4.3/
gparted-0.4.3/config.guess
gparted-0.4.3/Makefile.in
gparted-0.4.3/po/
gparted-0.4.3/po/uk.po
gparted-0.4.3/po/fi.po
gparted-0.4.3/po/it.po
gparted-0.4.3/po/oc.po
gparted-0.4.3/po/zh_CN.po
gparted-0.4.3/po/sv.po
gparted-0.4.3/po/ca.po
gparted-0.4.3/po/ChangeLog
gparted-0.4.3/po/el.po
gparted-0.4.3/po/rw.po
gparted-0.4.3/po/th.po
gparted-0.4.3/po/POTFILES.skip
gparted-0.4.3/po/tr.po
gparted-0.4.3/po/pt_BR.po
gparted-0.4.3/po/vi.po
gparted-0.4.3/po/sk.po
gparted-0.4.3/po/ar.po
gparted-0.4.3/po/gu.po
gparted-0.4.3/po/nb.po
gparted-0.4.3/po/cs.po
gparted-0.4.3/po/bg.po
gparted-0.4.3/po/gl.po
gparted-0.4.3/po/ko.po
gparted-0.4.3/po/eu.po
gparted-0.4.3/po/pa.po
gparted-0.4.3/po/mk.po
gparted-0.4.3/po/lt.po
gparted-0.4.3/po/dz.po
gparted-0.4.3/po/ne.po
gparted-0.4.3/po/sl.po
gparted-0.4.3/po/pl.po
gparted-0.4.3/po/si.po
gparted-0.4.3/po/hu.po
gparted-0.4.3/po/Makefile.in.in
gparted-0.4.3/po/LINGUAS
gparted-0.4.3/po/ja.po
gparted-0.4.3/po/POTFILES.in
gparted-0.4.3/po/zh_TW.po
gparted-0.4.3/po/lv.po
gparted-0.4.3/po/ru.po
gparted-0.4.3/po/en_GB.po
gparted-0.4.3/po/fr.po
gparted-0.4.3/po/he.po
gparted-0.4.3/po/pt.po
gparted-0.4.3/po/en_CA.po
gparted-0.4.3/po/es.po
gparted-0.4.3/po/nl.po
gparted-0.4.3/po/de.po
gparted-0.4.3/po/zh_HK.po
gparted-0.4.3/mkinstalldirs
gparted-0.4.3/src/
gparted-0.4.3/src/Win_GParted.cc
gparted-0.4.3/src/fat32.cc
gparted-0.4.3/src/jfs.cc
gparted-0.4.3/src/OperationDetail.cc
gparted-0.4.3/src/Makefile.in
gparted-0.4.3/src/OperationCheck.cc
gparted-0.4.3/src/OperationResizeMove.cc
gparted-0.4.3/src/ufs.cc
gparted-0.4.3/src/Partition.cc
gparted-0.4.3/src/FS_Info.cc
gparted-0.4.3/src/linux_swap.cc
gparted-0.4.3/src/Dialog_Partition_New.cc
gparted-0.4.3/src/OperationFormat.cc
gparted-0.4.3/src/DialogManageFlags.cc
gparted-0.4.3/src/Utils.cc
gparted-0.4.3/src/GParted_Core.cc
gparted-0.4.3/src/Dialog_Partition_Copy.cc
gparted-0.4.3/src/xfs.cc
gparted-0.4.3/src/DialogFeatures.cc
gparted-0.4.3/src/ext3.cc
gparted-0.4.3/src/OperationCreate.cc
gparted-0.4.3/src/main.cc
gparted-0.4.3/src/Dialog_Progress.cc
gparted-0.4.3/src/Operation.cc
gparted-0.4.3/src/OperationDelete.cc
gparted-0.4.3/src/fat16.cc
gparted-0.4.3/src/ntfs.cc
gparted-0.4.3/src/ext2.cc
gparted-0.4.3/src/OperationCopy.cc
gparted-0.4.3/src/ext4.cc
gparted-0.4.3/src/Device.cc
gparted-0.4.3/src/OperationLabelPartition.cc
gparted-0.4.3/src/hfsplus.cc
gparted-0.4.3/src/HBoxOperations.cc
gparted-0.4.3/src/Dialog_Partition_Info.cc
gparted-0.4.3/src/Makefile.am
gparted-0.4.3/src/Frame_Resizer_Base.cc
gparted-0.4.3/src/FileSystem.cc
gparted-0.4.3/src/Dialog_Partition_Label.cc
gparted-0.4.3/src/Frame_Resizer_Extended.cc
gparted-0.4.3/src/Dialog_Partition_Resize_Move.cc
gparted-0.4.3/src/Dialog_Disklabel.cc
gparted-0.4.3/src/reiserfs.cc
gparted-0.4.3/src/reiser4.cc
gparted-0.4.3/src/Dialog_Base_Partition.cc
gparted-0.4.3/src/DrawingAreaVisualDisk.cc
gparted-0.4.3/src/TreeView_Detail.cc
gparted-0.4.3/src/hfs.cc
gparted-0.4.3/intltool-merge.in
gparted-0.4.3/missing
gparted-0.4.3/ChangeLog
gparted-0.4.3/config.sub
gparted-0.4.3/depcomp
gparted-0.4.3/m4/
gparted-0.4.3/m4/intltool.m4
gparted-0.4.3/doc/
gparted-0.4.3/doc/Makefile.in
gparted-0.4.3/doc/Makefile.am
gparted-0.4.3/doc/gparted.8
gparted-0.4.3/gnome-doc-utils.make
gparted-0.4.3/data/
gparted-0.4.3/data/Makefile.in
gparted-0.4.3/data/icons/
gparted-0.4.3/data/icons/Makefile.in
gparted-0.4.3/data/icons/hicolor_apps_scalable_gparted.svg
gparted-0.4.3/data/icons/Makefile.am
gparted-0.4.3/data/icons/hicolor_apps_48x48_gparted.png
gparted-0.4.3/data/icons/hicolor_apps_22x22_gparted.png
gparted-0.4.3/data/icons/hicolor_apps_16x16_gparted.png
gparted-0.4.3/data/icons/hicolor_apps_32x32_gparted.png
gparted-0.4.3/data/icons/hicolor_apps_24x24_gparted.png
gparted-0.4.3/data/Makefile.am
gparted-0.4.3/COPYING
gparted-0.4.3/aclocal.m4

bzip2: Compressed file ends unexpectedly;
    perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: EOF inesperado en el archivo
tar: EOF inesperado en el archivo
tar: El error no es recuperable: salida ahora

after that i 

> cd gparted-0.4.3/ 
[FONT=monospace]./configure[/FONT]
bash: ./configure: No such file or folder

rather it gives me two options 

> config.guess  config.sub 

what to do next??


[FONT=monospace][/FONT]

---

### Post by Will4 on 2009-02-28
sorry I just realized it didn't download well... sorry I'll do the same now... SORRY

---

### Post by Will4 on 2009-02-28
OK here i am,

this is what i got 

> checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
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
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for gksu... gksu
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... no
checking for intltool >= 0.35.5... 0.37.1 found
checking for xgettext... no
checking for msgmerge... no
checking for msgfmt... (cached) no
configure: error: GNU gettext tools not found; required for intltool

---

### Post by taurus on 2009-02-28
You need to install gettext first and then run the ./configure again.

```
sudo apt-get update
sudo apt-get install gettext
./configure
```

---

### Post by Will4 on 2009-02-28
OK i did install gettext and ran ./configure. This is what it shows

> checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
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
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for gksu... gksu
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for intltool >= 0.35.5... 0.37.1 found
checking for xgettext... (cached) /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for uuid_generate in -luuid... no
configure: error: *** uuid library (libuuid) not found

Sorry it takes to long for me to respond, i use dial-up so downloads are taking forever, i am from Cuba. SORRY
Thank you for helping me...

---

### Post by taurus on 2009-02-28
Now you have to install libuuid1.

```
sudo apt-get install libuuid1
./configure
```

---

### Post by Will4 on 2009-02-28
now i get this, the last few lines are the only ones that changed so i give you those

> checking for uuid_generate in -luuid... yes
checking for dlopen in -ldl... yes
checking for libparted >= 1.7.1... configure: error: *** Requires libparted >= 1.7.1.  Perhaps development header files missing?

---

### Post by taurus on 2009-02-28
```
sudo apt-get install libparted1.8-dev
./configure
```

---

### Post by Will4 on 2009-02-28
Hey taurus,
i don't know how i got the thing installed and after running ./configure it gave me this
> 
config.status: creating Makefile
config.status: creating compose/Makefile
config.status: creating data/Makefile
config.status: creating data/icons/Makefile
config.status: creating doc/Makefile
config.status: creating help/Makefile
config.status: creating include/Makefile
config.status: creating src/Makefile
config.status: creating po/Makefile.in
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: executing intltool commands
config.status: executing po/stamp-it commands

================ Final configuration ===================
          Installing into prefix  :  /usr/local

            Build documentation?  :  yes

 If all settings are OK, type make and make install 
========================================================

What do i do next? Thank you very much for your help
Do i have GParted installed now?

---

### Post by taurus on 2009-02-28
Not yet.  I think you've got a little too excited for getting ./configure working.  Now, you need to run the make first and if there is no error, then install it.

```
make
```
It could take a little of time to compile the thing.  Then run this command to actually install it.

```
sudo make install
```
If everything is working the way it should, the new gparted should be in /usr/local/bin.

```
ls -la /usr/local/bin
```

---

### Post by Will4 on 2009-02-28
OK i did run 
> make
it took a while yes...
then i ran 
> make install
it seamed to run well without errors and said something of GParted being at /usr/local/sbin/
I ran 
> ls -la /usr/local/sbin
and got this
> total 7403
drwxr-xr-x  2 root root     104 2009-02-28 23:07 .
drwxr-xr-x 11 root root     288 2009-01-20 22:32 ..
-rwxr-xr-x  1 root root    1098 2009-02-28 23:07 gparted
-rwxr-xr-x  1 root root 7568951 2009-02-28 23:07 gpartedbin

What next??
Thank you very much...

---

### Post by taurus on 2009-02-28
Just fire up that new baby and see what it does.

```
gksudo gparted
```

---

### Post by Will4 on 2009-02-28
WOWOWOWOWOWOW!!!!

We got it!! 
it brings the labeling feature but not the ntfs, the one to format in NTFS, which i think i need to install separately... Thank you very much buddy...
when do we have the SOLVED button fixed in the forums?? I would love to let others know about!!

Thank you taurus...

---

### Post by fobronco on 2009-03-13
I get this error:
configure: error: *** uuid library (libuuid) not found

and then i run:sudo apt-get install libuuid1

and get:
Leser pakkelister ... Ferdig
Skaper oversikt over avhengighetsforhold       
Reading state information ... Ferdig    
libuuid1 er allerede nyeste versjon.
0 oppgraderte, 0 nylig installerte, 0 å fjerne og 8 ikke oppgradert.

allreddy  installed??

---

