---
title: "Cannot install HTK  HMM toolkit on hardy"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by anilcr on 2009-03-08
the configure works well but the make gives me following errors
```

anil@anil-desktop:~/Download/htk$ make all
(cd HTKTools && make all) \
	  || case "" in *k*) fail=yes;; *) exit 1;; esac;
make[1]: Entering directory `/home/anil/Download/htk/HTKTools'
if [ ! -d /usr/bin -a X_ = X_yes ] ; then mkdir -p /usr/bin ; fi
if [ xHSLab = xHSLab ] ; then \
		gcc -o HSLab -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I../HTKLib HSLab.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm -lX11 ; \
		else \
		gcc -o HSLab -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I../HTKLib HSLab.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm ; fi
make[1]: Leaving directory `/home/anil/Download/htk/HTKTools'
anil@anil-desktop:~/Download/htk$ make all
(cd HTKTools && make all) \
	  || case "" in *k*) fail=yes;; *) exit 1;; esac;
make[1]: Entering directory `/home/anil/Download/htk/HTKTools'
if [ ! -d /usr/bin -a X_ = X_yes ] ; then mkdir -p /usr/bin ; fi
if [ xHSLab = xHSLab ] ; then \
		gcc -o HSLab -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I../HTKLib HSLab.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm -lX11 ; \
		else \
		gcc -o HSLab -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I../HTKLib HSLab.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm ; fi
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.4/../../../libX11.so when searching for -lX11
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.4/../../../libX11.a when searching for -lX11
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libX11.so when searching for -lX11
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libX11.a when searching for -lX11
/usr/bin/ld: skipping incompatible /usr/lib/libX11.so when searching for -lX11
/usr/bin/ld: skipping incompatible /usr/lib/libX11.a when searching for -lX11
/usr/bin/ld: cannot find -lX11
collect2: ld returned 1 exit status
make[1]: *** [HSLab] Error 1
make[1]: Leaving directory `/home/anil/Download/htk/HTKTools'
make: *** [htktools] Error 1

```

help please, thanks in advance

---

### Post by yeats on 2009-03-08
Are there instructions that come with the package?  perhaps a README?  This is the type of error that a "./configure" script should catch before you run "make" (though you're saying it didn't).  You might also try

```
sudo make all
```

---

### Post by anilcr on 2009-03-08
yes i do have readme:
```

Compiling & Installing HTK under UNIX/Linux, OS X or Cygwin
===========================================================

After unpacking the sources, cd to the htk directory.  

There are now two ways to install HTK, the "traditional" and the
"new".  Up to now HTK has always installed its tools as they were
built, and installed them to a directory such as "bin.linux" so that
binaries for different architectures can be installed in a home
directory say.  If you want to install in this way, please add the
option "--enable-trad-htk" when you run configure.

The "new" method installs by default into /usr/local/bin (equivalent
to a configure option of "--prefix=/usr/local").

1. decide which of the above methods you wish to use
2. cd to htk, then run ./configure (with appropriate options, run
   "./configure --help" if unsure).
   If you don't want to build the programs in HLMTools add the 
   --disable-hlmtools option.
3. make all
4. make install

Running "make install" will install them.  This step may need to be
done as root, if you are not installing them in your home directory.

Notes for particular Unix variants:
Solaris: if "make" isn't installed you may need to add /opt/sfw/bin
and /usr/ccs/bin to your path and run "./configure MAKE=gmake" with
any other options you require.  Then run "gmake" instead of "make",
alternatively you can create a symbolic link called "make" somewhere
it your path to /opt/sfw/bin/gmake


HDecode
=======

If you are also building HDecode (available from the HTK website, under a
different licence from HTK), you will firstly need to unpack the HDecode
source code (in the same directory in which you unpacked the HTK
sources). Follow the steps above for building HTK first, then add
these steps to the build process:

5. make hdecode
6. make install-hdecode

```
I also have Xorg development tools available

---

### Post by anilcr on 2009-03-08
sudo doesn't do the trick

---

### Post by yeats on 2009-03-08
I'm wondering if there's an architecture issue here.  I see all the "x86_64" references, but it seems like all the files that should suffice are deemed incompatible.  To confirm, you are running Ubuntu 64-bit (seems that configure should catch this too)?

---

### Post by anilcr on 2009-03-08
yes I am, I also have x86-dev installed ( check that it has -m32 switch ) any problem with that you think?
BTW, this worked on my friend's Intrepid system not working here.

---

### Post by yeats on 2009-03-08
>  yes I am, I also have x86-dev installed ( check that it has -m32 switch ) any problem with that you think?
BTW, this worked on my friend's Intrepid system not working here. 

Yes - try -m64 instead and see if that works...

---

### Post by anilcr on 2009-03-08
does not work
```

anil@anil-desktop:~/Download/htk$ make all
(cd HTKLib && make HTKLib.a) \
	  || case "" in *k*) fail=yes;; *) exit 1;; esac;
make[1]: Entering directory `/home/anil/Download/htk/HTKLib'
gcc  -m64 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I.    -c -o HAdapt.o HAdapt.c
HAdapt.c: In function ‘UpdateAccCache’:
HAdapt.c:1003: warning: cast from pointer to integer of different size
HAdapt.c: In function ‘UpdateBaseAccs’:
HAdapt.c:1040: warning: cast from pointer to integer of different size
HAdapt.c:1055: warning: cast from pointer to integer of different size
HAdapt.c: In function ‘UpdateBaseAccsWithPaac’:
HAdapt.c:1091: warning: cast from pointer to integer of different size
gcc  -m64 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I.    -c -o HArc.o HArc.c
HArc.c: In function ‘PrintArc’:
HArc.c:214: warning: cast from pointer to integer of different size
gcc  -m64 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I.    -c -o HAudio.o HAudio.c
gcc  -m64 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I.    -c -o HDict.o HDict.c
HDict.c: In function ‘VocabHash’:
HDict.c:61: warning: cast from pointer to integer of different size
gcc  -m64 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I.    -c -o HExactMPE.o HExactMPE.c
HExactMPE.c: In function ‘DoCorrectness’:
HExactMPE.c:271: warning: cast from pointer to integer of different size
HExactMPE.c:288: warning: value computed is not used
HExactMPE.c: In function ‘DoExactCorrectness’:
HExactMPE.c:664: warning: cast from pointer to integer of different size
gcc  -m64 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I.    -c -o HFB.o HFB.c
HFB.c: In function ‘StepForward’:
HFB.c:1770: warning: cast from pointer to integer of different size
HFB.c:1771: warning: cast to pointer from integer of different size
gcc  -m64 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I.    -c -o HFBLat.o HFBLat.c
HFBLat.c: In function ‘GetNoContextPhone’:
HFBLat.c:174: warning: cast from pointer to integer of different size
HFBLat.c:213: warning: cast from pointer to integer of different size
HFBLat.c: In function ‘SetCorrectness’:
HFBLat.c:255: warning: cast from pointer to integer of different size
HFBLat.c:304: warning: cast from pointer to integer of different size
HFBLat.c:334: warning: cast from pointer to integer of different size
HFBLat.c:403: warning: cast from pointer to integer of different size
HFBLat.c: In function ‘SetCorrectnessAsError’:
HFBLat.c:546: warning: cast from pointer to integer of different size
HFBLat.c:597: warning: cast from pointer to integer of different size
HFBLat.c:626: warning: cast from pointer to integer of different size
HFBLat.c: In function ‘StepForward’:
HFBLat.c:1397: warning: cast from pointer to integer of different size
HFBLat.c:1398: warning: cast to pointer from integer of different size
HFBLat.c: In function ‘DoAllMixUpdates’:
HFBLat.c:1069: warning: ‘mammi’ may be used uninitialized in this function
gcc  -m64 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I.    -c -o HLabel.o HLabel.c
gcc  -m64 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I.    -c -o HLat.o HLat.c
HLat.c: In function ‘CalcStats’:
HLat.c:907: warning: cast from pointer to integer of different size
HLat.c:907: warning: cast to pointer from integer of different size
HLat.c: In function ‘ApplyNGram2LabLat’:
HLat.c:1792: warning: cast from pointer to integer of different size
gcc  -m64 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I.    -c -o HLM.o HLM.c
HLM.c: In function ‘ReadNGrams’:
HLM.c:404: warning: cast to pointer from integer of different size
HLM.c:427: warning: cast from pointer to integer of different size
HLM.c: In function ‘ReadMatBigram’:
HLM.c:673: warning: cast from pointer to integer of different size
HLM.c:675: warning: cast to pointer from integer of different size
HLM.c: In function ‘GetLMProb’:
HLM.c:767: warning: cast from pointer to integer of different size
HLM.c:772: warning: cast from pointer to integer of different size
HLM.c:803: warning: cast from pointer to integer of different size
HLM.c:804: warning: cast from pointer to integer of different size
HLM.c: In function ‘LMTrans’:
HLM.c:917: warning: cast from pointer to integer of different size
gcc  -m64 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I.    -c -o HMap.o HMap.c
HMap.c: In function ‘MAPUpdateModels’:
HMap.c:432: warning: cast from pointer to integer of different size
gcc  -m64 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I.    -c -o HMath.o HMath.c
gcc  -m64 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I.    -c -o HMem.o HMem.c
HMem.c: In function ‘AllocBlock’:
HMem.c:109: warning: format ‘%u’ expects type ‘unsigned int’, but argument 2 has type ‘size_t’
HMem.c: In function ‘CreateHeap’:
HMem.c:235: warning: format ‘%u’ expects type ‘unsigned int’, but argument 4 has type ‘size_t’
HMem.c:235: warning: format ‘%u’ expects type ‘unsigned int’, but argument 6 has type ‘size_t’
HMem.c:235: warning: format ‘%u’ expects type ‘unsigned int’, but argument 7 has type ‘size_t’
HMem.c: In function ‘New’:
HMem.c:342: warning: format ‘%u’ expects type ‘unsigned int’, but argument 3 has type ‘size_t’
HMem.c:353: warning: format ‘%u’ expects type ‘unsigned int’, but argument 3 has type ‘size_t’
HMem.c:353: warning: format ‘%u’ expects type ‘unsigned int’, but argument 4 has type ‘size_t’
HMem.c:377: warning: format ‘%u’ expects type ‘unsigned int’, but argument 3 has type ‘size_t’
HMem.c: In function ‘Dispose’:
HMem.c:440: warning: format ‘%u’ expects type ‘unsigned int’, but argument 3 has type ‘size_t’
HMem.c:483: warning: format ‘%u’ expects type ‘unsigned int’, but argument 3 has type ‘size_t’
HMem.c:492: warning: format ‘%u’ expects type ‘unsigned int’, but argument 3 has type ‘size_t’
HMem.c:492: warning: format ‘%u’ expects type ‘unsigned int’, but argument 4 has type ‘size_t’
HMem.c: In function ‘PrintHeapStats’:
HMem.c:513: warning: format ‘%6u’ expects type ‘unsigned int’, but argument 3 has type ‘size_t’
HMem.c:513: warning: format ‘%-3u’ expects type ‘unsigned int’, but argument 4 has type ‘size_t’
HMem.c:513: warning: format ‘%9u’ expects type ‘unsigned int’, but argument 5 has type ‘size_t’
HMem.c:513: warning: format ‘%9u’ expects type ‘unsigned int’, but argument 6 has type ‘size_t’
gcc  -m64 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I.    -c -o HModel.o HModel.c
HModel.c: In function ‘NewMacro’:
HModel.c:3386: warning: cast from pointer to integer of different size
HModel.c: In function ‘FindMacroStruct’:
HModel.c:3450: warning: cast from pointer to integer of different size
HModel.c:3458: warning: cast from pointer to integer of different size
HModel.c: In function ‘SetIndexes’:
HModel.c:3967: warning: cast to pointer from integer of different size
HModel.c:3970: warning: cast from pointer to integer of different size
HModel.c: In function ‘PutBaseClass’:
HModel.c:2958: warning: ‘comp’ may be used uninitialized in this function
HModel.c:2958: warning: ‘stream’ may be used uninitialized in this function
gcc  -m64 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I.    -c -o HNet.o HNet.c
HNet.c: In function ‘GetSubLat’:
HNet.c:333: warning: cast from pointer to integer of different size
HNet.c: In function ‘PrintNode’:
HNet.c:1616: warning: cast from pointer to integer of different size
HNet.c:1616: warning: format ‘%05d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
HNet.c: In function ‘PrintLinks’:
HNet.c:1645: warning: cast from pointer to integer of different size
HNet.c:1646: warning: format ‘%05d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
HNet.c: In function ‘FindWordNode’:
HNet.c:2002: warning: cast to pointer from integer of different size
gcc  -m64 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I.    -c -o HParm.o HParm.c
HParm.c: In function ‘OpenAsChannel’:
HParm.c:4141: warning: ‘initRows’ may be used uninitialized in this function
gcc  -m64 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I.    -c -o HRec.o HRec.c
HRec.c: In function ‘ProcessObservation’:
HRec.c:717: warning: ‘tok.align’ is used uninitialized in this function
HRec.c:618: note: ‘tok.align’ was declared here
HRec.c:717: warning: ‘tok.path’ is used uninitialized in this function
HRec.c:618: note: ‘tok.path’ was declared here
HRec.c:717: warning: ‘tok.lm’ is used uninitialized in this function
HRec.c:618: note: ‘tok.lm’ was declared here
gcc  -m64 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I.    -c -o HShell.o HShell.c
gcc  -m64 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I.    -c -o HSigP.o HSigP.c
gcc  -m64 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I.    -c -o HTrain.o HTrain.c
HTrain.c: In function ‘DumpAccsParallel’:
HTrain.c:1467: warning: dereferencing type-punned pointer will break strict-aliasing rules
HTrain.c: In function ‘LoadAccsParallel’:
HTrain.c:1644: warning: cast from pointer to integer of different size
HTrain.c:1644: warning: cast to pointer from integer of different size
gcc  -m64 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I.    -c -o HUtil.o HUtil.c
gcc  -m64 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I.    -c -o HVQ.o HVQ.c
gcc  -m64 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I.    -c -o HWave.o HWave.c
HWave.c: In function ‘OpenWaveInput’:
HWave.c:998: warning: ‘commchunk2.nSamples’ may be used uninitialized in this function
HWave.c:998: note: ‘commchunk2.nSamples’ was declared here
gcc  -m64 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I.    -c -o strarr.o strarr.c
if [ -f HTKLib.a ] ; then  /bin/rm HTKLib.a ; fi
ar rv HTKLib.a HGraf.o esig_asc.o esig_edr.o esignal.o esig_nat.o HAdapt.o HArc.o HAudio.o HDict.o HExactMPE.o HFB.o HFBLat.o HLabel.o HLat.o HLM.o HMap.o HMath.o HMem.o HModel.o HNet.o HParm.o HRec.o HShell.o HSigP.o HTrain.o HUtil.o HVQ.o HWave.o strarr.o
ar: creating HTKLib.a
a - HGraf.o
a - esig_asc.o
a - esig_edr.o
a - esignal.o
a - esig_nat.o
a - HAdapt.o
a - HArc.o
a - HAudio.o
a - HDict.o
a - HExactMPE.o
a - HFB.o
a - HFBLat.o
a - HLabel.o
a - HLat.o
a - HLM.o
a - HMap.o
a - HMath.o
a - HMem.o
a - HModel.o
a - HNet.o
a - HParm.o
a - HRec.o
a - HShell.o
a - HSigP.o
a - HTrain.o
a - HUtil.o
a - HVQ.o
a - HWave.o
a - strarr.o
ranlib HTKLib.a
make[1]: Leaving directory `/home/anil/Download/htk/HTKLib'
(cd HTKTools && make all) \
	  || case "" in *k*) fail=yes;; *) exit 1;; esac;
make[1]: Entering directory `/home/anil/Download/htk/HTKTools'
if [ ! -d /usr/local/bin.linux -a X_yes = X_yes ] ; then mkdir -p /usr/local/bin.linux ; fi
if [ xHSLab = xHSLab ] ; then \
		gcc -o HSLab -m64 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I../HTKLib HSLab.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm -lX11 ; \
		else \
		gcc -o HSLab -m64 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I../HTKLib HSLab.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm ; fi
/usr/bin/ld: i386 architecture of input file `../HTKLib/HTKLib.a(HGraf.o)' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `../HTKLib/HTKLib.a(esignal.o)' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `../HTKLib/HTKLib.a(esig_nat.o)' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `../HTKLib/HTKLib.a(esig_asc.o)' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `../HTKLib/HTKLib.a(esig_edr.o)' is incompatible with i386:x86-64 output
collect2: ld returned 1 exit status
make[1]: *** [HSLab] Error 1
make[1]: Leaving directory `/home/anil/Download/htk/HTKTools'
make: *** [htktools] Error 1

```
:(

---

### Post by yeats on 2009-03-08
Okay, try:

```
make clean
```

and do a new ./configure - then post the output here...

---

### Post by anilcr on 2009-03-08
here is the ./configure
```

anil@anil-desktop:~/Download/htk$ ./configure
checking whether make sets $(MAKE)... yes
checking for gawk... no
checking for mawk... mawk
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ranlib... ranlib
checking for main in -lX11... yes
checking for main in -lm... yes
checking how to run the C preprocessor... gcc -E
checking for X... libraries , headers 
checking for egrep... grep -E
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
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking float.h usability... yes
checking float.h presence... yes
checking for float.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for memory.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking whether gcc needs -traditional... no
checking for working memcmp... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for working strtod... yes
checking return type of signal handlers... void
checking for vprintf... yes
checking for _doprnt... no
checking for floor... yes
checking for gettimeofday... yes
checking for memmove... yes
checking for memset... yes
checking for modf... yes
checking for pow... yes
checking for socket... yes
checking for sqrt... yes
checking for strchr... yes
checking for strcspn... yes
checking for strrchr... yes
checking for strspn... yes
checking for strstr... yes
checking for strtol... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
configure: creating ./config.status
config.status: creating HTKLib/Makefile
config.status: creating HTKTools/Makefile
config.status: creating HLMLib/Makefile
config.status: creating HLMTools/Makefile
config.status: creating HTKLVRec/Makefile
config.status: creating Makefile
**************************************************

HTK is now ready to be built.

Type "make all" to build the HTK libraries
and tools.

Then "make install" to install them.

The tools will be installed in /usr/local/bin

Build notes: Language Modelling tools will be
built. HDecode will not be built. You can build
it manually later by running 'make hdecode
install-hdecode'

**************************************************

```

---

### Post by anilcr on 2009-03-08
help!

---

### Post by yeats on 2009-03-08
```
checking for X... libraries , headers 

```

Since the configure script isn't throwing any errors here, you can assume that all prerequisites are installed, albeit not necessarily in the place(s) where the make script looks for them.  Looking at your original make output:

```
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.4/../../../libX11.so when searching for -lX11
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.4/../../../libX11.a when searching for -lX11
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libX11.so when searching for -lX11
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libX11.a when searching for -lX11
/usr/bin/ld: skipping incompatible /usr/lib/libX11.so when searching for -lX11
/usr/bin/ld: skipping incompatible /usr/lib/libX11.a when searching for -lX11
/usr/bin/ld: cannot find -lX11

```

you might look in the /usr/bin/ld directory for all the X11 libraries, then you can create a symbolic link in that directory to the correct location of the "lX11" file.  I'm not familiar with this particular file (or the program you're trying to install), but this is standard troubleshooting procedure.  It may also be the case that "lX11" is not the actual name of the file, but a variable the make script uses to store that information....

Hope that helps.

---

### Post by anilcr on 2009-03-08
ld is the linker. so its a program not a directory.

---

### Post by yeats on 2009-03-08
> **anilcr said:**
> ld is the linker. so its a program not a directory.

Of course ... sorry - I wasn't thinking.  I would still recommend my approach:  Try to find the correct file, then find where the make program is looking for it, then create a symbolic link to the right location.

---

### Post by Rechild12 on 2009-09-29
OK, using

```
sudo ./getlibs -p libx11-dev
```is one way around this. The getlibs file can be downloaded from [http://frozenfox.freehostia.com/cappy/](http://frozenfox.freehostia.com/cappy/)

---

### Post by junaidbaber on 2010-06-17
> **anilcr said:**
> the configure works well but the make gives me following errors
```

anil@anil-desktop:~/Download/htk$ make all
(cd HTKTools && make all) \
	  || case "" in *k*) fail=yes;; *) exit 1;; esac;
make[1]: Entering directory `/home/anil/Download/htk/HTKTools'
if [ ! -d /usr/bin -a X_ = X_yes ] ; then mkdir -p /usr/bin ; fi
if [ xHSLab = xHSLab ] ; then \
		gcc -o HSLab -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I../HTKLib HSLab.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm -lX11 ; \
		else \
		gcc -o HSLab -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I../HTKLib HSLab.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm ; fi
make[1]: Leaving directory `/home/anil/Download/htk/HTKTools'
anil@anil-desktop:~/Download/htk$ make all
(cd HTKTools && make all) \
	  || case "" in *k*) fail=yes;; *) exit 1;; esac;
make[1]: Entering directory `/home/anil/Download/htk/HTKTools'
if [ ! -d /usr/bin -a X_ = X_yes ] ; then mkdir -p /usr/bin ; fi
if [ xHSLab = xHSLab ] ; then \
		gcc -o HSLab -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I../HTKLib HSLab.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm -lX11 ; \
		else \
		gcc -o HSLab -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I../HTKLib HSLab.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm ; fi
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.4/../../../libX11.so when searching for -lX11
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.4/../../../libX11.a when searching for -lX11
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libX11.so when searching for -lX11
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libX11.a when searching for -lX11
/usr/bin/ld: skipping incompatible /usr/lib/libX11.so when searching for -lX11
/usr/bin/ld: skipping incompatible /usr/lib/libX11.a when searching for -lX11
/usr/bin/ld: cannot find -lX11
collect2: ld returned 1 exit status
make[1]: *** [HSLab] Error 1
make[1]: Leaving directory `/home/anil/Download/htk/HTKTools'
make: *** [htktools] Error 1

```

help please, thanks in advance

-----------------------------

Dear if you still facing the problem then try this

> sudo apt-get install libc6-dev-i386
then 
> make all
finally 
> sudo make install


it works for me. :)

---

### Post by dabraude on 2011-10-27
In 11.10 I got similar errors and fixed it with: 

sudo apt-get install build-essential libc6-i386 libc6-dev-i386 xorg-dev libx11-xcb-dev ia32-libs

(if you get an error reinstall libx11-dev - I did this through the package manger obtained through the software centre)

To do live recognition follow this link:
[http://ubuntuforums.org/showthread.p...3#post11341143](http://ubuntuforums.org/showthread.p...3#post11341143)

---

