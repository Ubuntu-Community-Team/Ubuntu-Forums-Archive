---
title: "Problem install HTK on ubuntu 8.10"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by sodsada on 2009-03-10
Hi everybody i am trying to install htk-3.3 on my laptop there was the 
problem during **make all** i will show you this is my problem that i found.

root@keoouthay:/home/sodsada/htk/htk-3.3# ./configure
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
checking for X... no
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
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
configure: creating ./config.status
config.status: creating HTKLib/Makefile
config.status: creating HTKTools/Makefile
config.status: creating HLMLib/Makefile
config.status: creating HLMTools/Makefile
config.status: creating Makefile
**root@keoouthay:/home/sodsada/htk/htk-3.3# make all**
make[1]: entrant dans le répertoire « /home/sodsada/htk/htk-3.3/HTKLib »
gcc -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="linux"' -Wall -Wno-switch -g -O2 -I.    -c -o HModel.o HModel.c
HModel.c: In function ‘GetOption’:
HMode.c:607: erreur: invalid storage class for function ‘GetInputXForm’
HModel.c:648: attention : implicit declaration of function ‘GetInputXForm’
HModel.c:648: attention : assignment makes pointer from integer without a cast
HModel.c: Hors de toute fonction :
HModel.c:2334: erreur: conflicting types for ‘GetInputXForm’
HModel.c:648: erreur: previous implicit declaration of ‘GetInputXForm’ was here
make[1]: *** [HModel.o] Erreur 1
make[1]: quittant le répertoire « /home/sodsada/htk/htk-3.3/HTKLib »
make: *** [all] Erreur 1
root@keoouthay:/home/sodsada/htk/htk-3.3# 

can anyone help me

---

### Post by Partyboi2 on 2009-03-12
This was taken from the HTK website.


[LIST]
[*]> **I get a compilation error: HModel.c:607: error: invalid storage class for function 'GetInputXForm'**  This happens if you try to compile HTK 3.3 using GCC version 4.  You can find details about how to fix this  [here]("http://htk.eng.cam.ac.uk/pipermail/htk-developers/2006-February/000643.html").  Note that this has been fixed in 3.4 and we strongly recommend that you upgrade to the latest release.

[/LIST]

---

### Post by tati_vital on 2009-04-25
Hi,
 
I'm using HTK (version 3.4.1) and Ubuntu 8.10. I have a problem running "./configure" and "make all" related to datarootdir. Could anyone help me ?
 
Running ./configure:
 
[SIZE=2]tatiane@tatiane-vital:~/bin/htk$ ./configure[/SIZE]
[SIZE=2]checking whether make sets $(MAKE)... yes[/SIZE]
[SIZE=2]checking for gawk... no[/SIZE]
[SIZE=2]checking for mawk... mawk[/SIZE]
[SIZE=2]checking for gcc... gcc[/SIZE]
[SIZE=2]checking for C compiler default output file name... a.out[/SIZE]
[SIZE=2]checking whether the C compiler works... yes[/SIZE]
[SIZE=2]checking whether we are cross compiling... no[/SIZE]
[SIZE=2]checking for suffix of executables... [/SIZE]
[SIZE=2]checking for suffix of object files... o[/SIZE]
[SIZE=2]checking whether we are using the GNU C compiler... yes[/SIZE]
[SIZE=2]checking whether gcc accepts -g... yes[/SIZE]
[SIZE=2]checking for gcc option to accept ISO C89... none needed[/SIZE]
[SIZE=2]checking for a BSD-compatible install... /usr/bin/install -c[/SIZE]
[SIZE=2]checking whether ln -s works... yes[/SIZE]
[SIZE=2]checking for ranlib... ranlib[/SIZE]
[SIZE=2]checking for main in -lX11... no[/SIZE]
[SIZE=2]checking for main in -lm... yes[/SIZE]
[SIZE=2]checking how to run the C preprocessor... gcc -E[/SIZE]
[SIZE=2]checking for X... no[/SIZE]
[SIZE=2]checking for grep that handles long lines and -e... /bin/grep[/SIZE]
[SIZE=2]checking for egrep... /bin/grep -E[/SIZE]
[SIZE=2]checking for ANSI C header files... yes[/SIZE]
[SIZE=2]checking for sys/types.h... yes[/SIZE]
[SIZE=2]checking for sys/stat.h... yes[/SIZE]
[SIZE=2]checking for stdlib.h... yes[/SIZE]
[SIZE=2]checking for string.h... yes[/SIZE]
[SIZE=2]checking for memory.h... yes[/SIZE]
[SIZE=2]checking for strings.h... yes[/SIZE]
[SIZE=2]checking for inttypes.h... yes[/SIZE]
[SIZE=2]checking for stdint.h... yes[/SIZE]
[SIZE=2]checking for unistd.h... yes[/SIZE]
[SIZE=2]checking errno.h usability... yes[/SIZE]
[SIZE=2]checking errno.h presence... yes[/SIZE]
[SIZE=2]checking for errno.h... yes[/SIZE]
[SIZE=2]checking fcntl.h usability... yes[/SIZE]
[SIZE=2]checking fcntl.h presence... yes[/SIZE]
[SIZE=2]checking for fcntl.h... yes[/SIZE]
[SIZE=2]checking float.h usability... yes[/SIZE]
[SIZE=2]checking float.h presence... yes[/SIZE]
[SIZE=2]checking for float.h... yes[/SIZE]
[SIZE=2]checking limits.h usability... yes[/SIZE]
[SIZE=2]checking limits.h presence... yes[/SIZE]
[SIZE=2]checking for limits.h... yes[/SIZE]
[SIZE=2]checking malloc.h usability... yes[/SIZE]
[SIZE=2]checking malloc.h presence... yes[/SIZE]
[SIZE=2]checking for malloc.h... yes[/SIZE]
[SIZE=2]checking for memory.h... (cached) yes[/SIZE]
[SIZE=2]checking for stdlib.h... (cached) yes[/SIZE]
[SIZE=2]checking for string.h... (cached) yes[/SIZE]
[SIZE=2]checking sys/ioctl.h usability... yes[/SIZE]
[SIZE=2]checking sys/ioctl.h presence... yes[/SIZE]
[SIZE=2]checking for sys/ioctl.h... yes[/SIZE]
[SIZE=2]checking sys/socket.h usability... yes[/SIZE]
[SIZE=2]checking sys/socket.h presence... yes[/SIZE]
[SIZE=2]checking for sys/socket.h... yes[/SIZE]
[SIZE=2]checking sys/time.h usability... yes[/SIZE]
[SIZE=2]checking sys/time.h presence... yes[/SIZE]
[SIZE=2]checking for sys/time.h... yes[/SIZE]
[SIZE=2]checking for unistd.h... (cached) yes[/SIZE]
[SIZE=2]checking for an ANSI C-conforming const... yes[/SIZE]
[SIZE=2]checking for size_t... yes[/SIZE]
[SIZE=2]checking whether time.h and sys/time.h may both be included... yes[/SIZE]
[SIZE=2]checking whether struct tm is in sys/time.h or time.h... time.h[/SIZE]
[SIZE=2]checking whether gcc needs -traditional... no[/SIZE]
[SIZE=2]checking for working memcmp... yes[/SIZE]
[SIZE=2]checking for stdlib.h... (cached) yes[/SIZE]
[SIZE=2]checking for GNU libc compatible malloc... yes[/SIZE]
[SIZE=2]checking for working strtod... yes[/SIZE]
[SIZE=2]checking return type of signal handlers... void[/SIZE]
[SIZE=2]checking for vprintf... yes[/SIZE]
[SIZE=2]checking for _doprnt... no[/SIZE]
[SIZE=2]checking for floor... yes[/SIZE]
[SIZE=2]checking for gettimeofday... yes[/SIZE]
[SIZE=2]checking for memmove... yes[/SIZE]
[SIZE=2]checking for memset... yes[/SIZE]
[SIZE=2]checking for modf... yes[/SIZE]
[SIZE=2]checking for pow... yes[/SIZE]
[SIZE=2]checking for socket... yes[/SIZE]
[SIZE=2]checking for sqrt... yes[/SIZE]
[SIZE=2]checking for strchr... yes[/SIZE]
[SIZE=2]checking for strcspn... yes[/SIZE]
[SIZE=2]checking for strrchr... yes[/SIZE]
[SIZE=2]checking for strspn... yes[/SIZE]
[SIZE=2]checking for strstr... yes[/SIZE]
[SIZE=2]checking for strtol... yes[/SIZE]
[SIZE=2]checking build system type... i686-pc-linux-gnu[/SIZE]
[SIZE=2]checking host system type... i686-pc-linux-gnu[/SIZE]
[SIZE=2]configure: creating ./config.status[/SIZE]
[SIZE=2]config.status: creating HTKLib/Makefile[/SIZE]
[SIZE=2]config.status: WARNING: HTKLib/Makefile.in seems to ignore the --datarootdir setting[/SIZE]
[SIZE=2]config.status: creating HTKTools/Makefile[/SIZE]
[SIZE=2]config.status: WARNING: HTKTools/Makefile.in seems to ignore the --datarootdir setting[/SIZE]
[SIZE=2]config.status: creating HLMLib/Makefile[/SIZE]
[SIZE=2]config.status: WARNING: HLMLib/Makefile.in seems to ignore the --datarootdir setting[/SIZE]
[SIZE=2]config.status: creating HLMTools/Makefile[/SIZE]
[SIZE=2]config.status: WARNING: HLMTools/Makefile.in seems to ignore the --datarootdir setting[/SIZE]
[SIZE=2]config.status: creating HTKLVRec/Makefile[/SIZE]
[SIZE=2]config.status: WARNING: HTKLVRec/Makefile.in seems to ignore the --datarootdir setting[/SIZE]
[SIZE=2]config.status: creating Makefile[/SIZE]
[SIZE=2]config.status: WARNING: Makefile.in seems to ignore the --datarootdir setting[/SIZE]
[SIZE=2]**************************************************[/SIZE]
[SIZE=2]HTK is now ready to be built.[/SIZE]
[SIZE=2]Type "make all" to build the HTK libraries[/SIZE]
[SIZE=2]and tools.[/SIZE]
[SIZE=2]Then "make install" to install them.[/SIZE]
[SIZE=2]The tools will be installed in /usr/local/bin[/SIZE]
[SIZE=2]Build notes: Language Modelling tools will be[/SIZE]
[SIZE=2]built. HDecode will not be built. You can build[/SIZE]
[SIZE=2]it manually later by running 'make hdecode[/SIZE]
[SIZE=2]install-hdecode'[/SIZE]
[SIZE=2]**************************************************[/SIZE]
 
 
[SIZE=2]Running "make all"[/SIZE]
 
[SIZE=2][SIZE=2][SIZE=2]tatiane@tatiane-vital:~/bin/htk$ make all[/SIZE]
[SIZE=2](cd HTKLib && make HTKLib.a) \[/SIZE]
[SIZE=2]|| case "" in *k*) fail=yes;; *) exit 1;; esac;[/SIZE]
[SIZE=2]make[1]: Entrando no diretório `/home/tatiane/bin/htk/HTKLib'[/SIZE]
[SIZE=2]gcc -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="i686"' -Wall -Wno-switch -g -O2 -I. -DPHNALG -c -o HGraf.o HGraf.c[/SIZE]
[SIZE=2]HGraf.c:73:77: error: X11/Xlib.h: Arquivo ou diretório inexistente[/SIZE]
[SIZE=2]HGraf.c:74:23: error: X11/Xutil.h: Arquivo ou diretório inexistente[/SIZE]
[SIZE=2]HGraf.c:75:21: error: X11/Xos.h: Arquivo ou diretório inexistente[/SIZE]
[SIZE=2]HGraf.c:77:27: error: X11/keysymdef.h: Arquivo ou diretório inexistente[/SIZE]
[SIZE=2]HGraf.c:87: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token[/SIZE]
[SIZE=2]HGraf.c:88: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'rootW'[/SIZE]
[SIZE=2]HGraf.c:91: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'theCmap'[/SIZE]
[SIZE=2]HGraf.c:92: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'theGC'[/SIZE]
[SIZE=2]HGraf.c:93: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'gcs'[/SIZE]
[SIZE=2]HGraf.c:95: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token[/SIZE]
[SIZE=2]HGraf.c:96: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'report'[/SIZE]
[SIZE=2]HGraf.c:97: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'hints'[/SIZE]
[SIZE=2]HGraf.c:111: error: 'GXcopy' undeclared here (not in a function)[/SIZE]
[SIZE=2]HGraf.c:111: error: 'GXor' undeclared here (not in a function)[/SIZE]
[SIZE=2]HGraf.c:111: error: 'GXxor' undeclared here (not in a function)[/SIZE]
[SIZE=2]HGraf.c:111: error: 'GXinvert' undeclared here (not in a function)[/SIZE]
[SIZE=2]HGraf.c:151: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token[/SIZE]
[SIZE=2]HGraf.c: In function 'InstallFonts':[/SIZE]
[SIZE=2]HGraf.c:164: error: 'FontInfo' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:164: error: (Each undeclared identifier is reported only once[/SIZE]
[SIZE=2]HGraf.c:164: error: for each function it appears in.)[/SIZE]
[SIZE=2]HGraf.c:164: warning: implicit declaration of function 'XLoadQueryFont'[/SIZE]
[SIZE=2]HGraf.c:164: error: 'theDisp' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:167: error: 'DefaultFont' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c: At top level:[/SIZE]
[SIZE=2]HGraf.c:176: error: expected ')' before '*' token[/SIZE]
[SIZE=2]HGraf.c: In function 'HGetEvent':[/SIZE]
[SIZE=2]HGraf.c:219: error: 'XEvent' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:219: error: expected ';' before 'xev'[/SIZE]
[SIZE=2]HGraf.c:223: warning: implicit declaration of function 'XFlush'[/SIZE]
[SIZE=2]HGraf.c:223: error: 'theDisp' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:225: warning: implicit declaration of function 'XEventsQueued'[/SIZE]
[SIZE=2]HGraf.c:225: error: 'QueuedAfterFlush' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:226: warning: implicit declaration of function 'XNextEvent'[/SIZE]
[SIZE=2]HGraf.c:226: error: 'xev' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:228: error: 'theWindow' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:230: error: 'ButtonPress' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:235: error: 'ButtonRelease' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:240: error: 'MotionNotify' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:245: error: 'KeyPress' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:249: warning: implicit declaration of function 'DecodeKeyPress'[/SIZE]
[SIZE=2]HGraf.c:251: error: 'KeyRelease' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:257: error: 'Expose' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c: In function 'HEventsPending':[/SIZE]
[SIZE=2]HGraf.c:281: error: 'theDisp' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:281: error: 'QueuedAfterFlush' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c: In function 'HMousePos':[/SIZE]
[SIZE=2]HGraf.c:288: error: 'Window' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:288: error: expected ';' before 'root'[/SIZE]
[SIZE=2]HGraf.c:293: warning: implicit declaration of function 'XQueryPointer'[/SIZE]
[SIZE=2]HGraf.c:293: error: 'theDisp' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:293: error: 'theWindow' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:293: error: 'root' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:293: error: 'child' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c: In function 'InstallColours':[/SIZE]
[SIZE=2]HGraf.c:311: error: 'XColor' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:311: error: expected ';' before 'greyDef'[/SIZE]
[SIZE=2]HGraf.c:317: warning: implicit declaration of function 'XParseColor'[/SIZE]
[SIZE=2]HGraf.c:317: error: 'theDisp' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:317: error: 'theCmap' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:317: error: 'colourDef' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:320: warning: implicit declaration of function 'XAllocColor'[/SIZE]
[SIZE=2]HGraf.c:334: error: 'whiteDef' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:334: warning: implicit declaration of function 'XQueryColor'[/SIZE]
[SIZE=2]HGraf.c:335: error: 'blackDef' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:341: error: 'greyDef' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c: In function 'HSetColour':[/SIZE]
[SIZE=2]HGraf.c:361: warning: implicit declaration of function 'XSetForeground'[/SIZE]
[SIZE=2]HGraf.c:361: error: 'theDisp' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:361: error: 'gcs' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c: In function 'HSetGrey':[/SIZE]
[SIZE=2]HGraf.c:370: error: 'theDisp' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:370: error: 'gcs' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c: In function 'HDrawLines':[/SIZE]
[SIZE=2]HGraf.c:388: warning: implicit declaration of function 'XDrawLines'[/SIZE]
[SIZE=2]HGraf.c:388: error: 'theDisp' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:388: error: 'theWindow' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:388: error: 'theGC' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:388: error: 'XPoint' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:388: error: expected expression before ')' token[/SIZE]
[SIZE=2]HGraf.c: In function 'HDrawRectangle':[/SIZE]
[SIZE=2]HGraf.c:395: warning: implicit declaration of function 'XDrawRectangle'[/SIZE]
[SIZE=2]HGraf.c:395: error: 'theDisp' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:395: error: 'theWindow' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:395: error: 'theGC' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c: In function 'HFillRectangle':[/SIZE]
[SIZE=2]HGraf.c:402: warning: implicit declaration of function 'XFillRectangle'[/SIZE]
[SIZE=2]HGraf.c:402: error: 'theDisp' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:402: error: 'theWindow' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:402: error: 'theGC' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c: In function 'HDrawLine':[/SIZE]
[SIZE=2]HGraf.c:408: warning: implicit declaration of function 'XDrawLine'[/SIZE]
[SIZE=2]HGraf.c:408: error: 'theDisp' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:408: error: 'theWindow' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:408: error: 'theGC' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c: In function 'HFillPolygon':[/SIZE]
[SIZE=2]HGraf.c:414: warning: implicit declaration of function 'XFillPolygon'[/SIZE]
[SIZE=2]HGraf.c:414: error: 'theDisp' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:414: error: 'theWindow' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:414: error: 'theGC' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:414: error: 'XPoint' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:414: error: expected expression before ')' token[/SIZE]
[SIZE=2]HGraf.c: In function 'HDrawArc':[/SIZE]
[SIZE=2]HGraf.c:427: warning: implicit declaration of function 'XDrawArc'[/SIZE]
[SIZE=2]HGraf.c:427: error: 'theDisp' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:427: error: 'theWindow' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:427: error: 'theGC' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c: In function 'HFillArc':[/SIZE]
[SIZE=2]HGraf.c:440: warning: implicit declaration of function 'XFillArc'[/SIZE]
[SIZE=2]HGraf.c:440: error: 'theDisp' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:440: error: 'theWindow' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:440: error: 'theGC' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c: In function 'HPrintf':[/SIZE]
[SIZE=2]HGraf.c:451: warning: implicit declaration of function 'XDrawString'[/SIZE]
[SIZE=2]HGraf.c:451: error: 'theDisp' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:451: error: 'theWindow' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:451: error: 'theGC' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c: In function 'HCopyArea':[/SIZE]
[SIZE=2]HGraf.c:457: warning: implicit declaration of function 'XCopyArea'[/SIZE]
[SIZE=2]HGraf.c:457: error: 'theDisp' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:457: error: 'theWindow' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:457: error: 'theGC' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c: In function 'HPlotVector':[/SIZE]
[SIZE=2]HGraf.c:476: error: 'theDisp' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:476: error: 'theWindow' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:476: error: 'theGC' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c: In function 'HSetFontSize':[/SIZE]
[SIZE=2]HGraf.c:490: error: 'CurrentFont' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:490: error: 'DefaultFont' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:499: error: 'FontInfo' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:502: warning: implicit declaration of function 'XSetFont'[/SIZE]
[SIZE=2]HGraf.c:502: error: 'theDisp' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:502: error: 'gcs' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c: In function 'HSetLineWidth':[/SIZE]
[SIZE=2]HGraf.c:511: warning: implicit declaration of function 'XSetLineAttributes'[/SIZE]
[SIZE=2]HGraf.c:511: error: 'theDisp' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:511: error: 'gcs' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:511: error: 'LineSolid' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:511: error: 'JoinRound' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:511: error: 'FillSolid' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c: In function 'HSetXMode':[/SIZE]
[SIZE=2]HGraf.c:517: error: 'theGC' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:517: error: 'gcs' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c: In function 'CentreX':[/SIZE]
[SIZE=2]HGraf.c:523: warning: implicit declaration of function 'XTextWidth'[/SIZE]
[SIZE=2]HGraf.c:523: error: 'CurrentFont' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c: In function 'CentreY':[/SIZE]
[SIZE=2]HGraf.c:529: error: 'CurrentFont' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c: In function 'HTextWidth':[/SIZE]
[SIZE=2]HGraf.c:535: error: 'CurrentFont' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c: In function 'HTextHeight':[/SIZE]
[SIZE=2]HGraf.c:541: error: 'CurrentFont' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c: In function 'HDrawImage':[/SIZE]
[SIZE=2]HGraf.c:550: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token[/SIZE]
[SIZE=2]HGraf.c:550: error: 'xi' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:557: warning: implicit declaration of function 'XDestroyImage'[/SIZE]
[SIZE=2]HGraf.c:558: warning: implicit declaration of function 'XGetImage'[/SIZE]
[SIZE=2]HGraf.c:558: error: 'theDisp' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:558: error: 'theWindow' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:558: error: 'AllPlanes' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:558: error: 'XYPixmap' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:562: warning: implicit declaration of function 'XPutPixel'[/SIZE]
[SIZE=2]HGraf.c:564: warning: implicit declaration of function 'XPutImage'[/SIZE]
[SIZE=2]HGraf.c:564: error: 'theGC' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c: In function 'HFlush':[/SIZE]
[SIZE=2]HGraf.c:570: error: 'theDisp' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c: In function 'InitGCs':[/SIZE]
[SIZE=2]HGraf.c:780: error: 'XGCValues' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:780: error: expected ';' before 'values'[/SIZE]
[SIZE=2]HGraf.c:783: error: 'GCLineWidth' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:783: error: 'GCFunction' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:783: error: 'GCForeground' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:785: error: 'values' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:788: error: 'gcs' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:788: warning: implicit declaration of function 'XCreateGC'[/SIZE]
[SIZE=2]HGraf.c:788: error: 'theDisp' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:788: error: 'theWindow' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:790: error: 'GCPlaneMask' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c: In function 'InitGlobals':[/SIZE]
[SIZE=2]HGraf.c:800: warning: implicit declaration of function 'DefaultScreen'[/SIZE]
[SIZE=2]HGraf.c:800: error: 'theDisp' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:801: error: 'theCmap' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:801: warning: implicit declaration of function 'DefaultColormap'[/SIZE]
[SIZE=2]HGraf.c:802: error: 'rootW' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:802: warning: implicit declaration of function 'RootWindow'[/SIZE]
[SIZE=2]HGraf.c:803: error: 'theGC' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:803: warning: implicit declaration of function 'DefaultGC'[/SIZE]
[SIZE=2]HGraf.c:804: error: 'theVisual' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:804: warning: implicit declaration of function 'DefaultVisual'[/SIZE]
[SIZE=2]HGraf.c:805: warning: implicit declaration of function 'DisplayCells'[/SIZE]
[SIZE=2]HGraf.c:806: warning: implicit declaration of function 'DisplayWidth'[/SIZE]
[SIZE=2]HGraf.c:807: warning: implicit declaration of function 'DisplayHeight'[/SIZE]
[SIZE=2]HGraf.c:808: warning: implicit declaration of function 'DisplayPlanes'[/SIZE]
[SIZE=2]HGraf.c:809: warning: implicit declaration of function 'WhitePixel'[/SIZE]
[SIZE=2]HGraf.c:810: warning: implicit declaration of function 'BlackPixel'[/SIZE]
[SIZE=2]HGraf.c: In function 'MakeXGraf':[/SIZE]
[SIZE=2]HGraf.c:817: error: 'Window' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:817: error: expected ';' before 'window'[/SIZE]
[SIZE=2]HGraf.c:818: error: 'XSetWindowAttributes' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:818: error: expected ';' before 'setwinattr'[/SIZE]
[SIZE=2]HGraf.c:823: error: 'theDisp' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:823: warning: implicit declaration of function 'XOpenDisplay'[/SIZE]
[SIZE=2]HGraf.c:824: warning: implicit declaration of function 'XDisplayName'[/SIZE]
[SIZE=2]HGraf.c:828: error: 'parent' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:829: error: 'window' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:829: warning: implicit declaration of function 'XCreateSimpleWindow'[/SIZE]
[SIZE=2]HGraf.c:831: error: 'CWBackingStore' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:831: error: 'setwinattr' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:831: error: 'WhenMapped' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:832: warning: implicit declaration of function 'XChangeWindowAttributes'[/SIZE]
[SIZE=2]HGraf.c:834: error: 'hints' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:834: error: 'PPosition' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:834: error: 'PSize' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:834: error: 'PMaxSize' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:834: error: 'PMinSize' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:841: warning: implicit declaration of function 'XSetStandardProperties'[/SIZE]
[SIZE=2]HGraf.c:841: error: 'None' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:843: warning: implicit declaration of function 'XSelectInput'[/SIZE]
[SIZE=2]HGraf.c:843: error: 'ExposureMask' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:843: error: 'KeyPressMask' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:843: error: 'ButtonPressMask' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:844: error: 'ButtonReleaseMask' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:844: error: 'PointerMotionHintMask' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:844: error: 'PointerMotionMask' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:845: warning: implicit declaration of function 'XMapWindow'[/SIZE]
[SIZE=2]HGraf.c:845: error: 'theWindow' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:850: error: 'report' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:851: error: 'Expose' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:852: warning: implicit declaration of function 'XSendEvent'[/SIZE]
[SIZE=2]HGraf.c:852: error: 'False' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c: In function 'TermHGraf':[/SIZE]
[SIZE=2]HGraf.c:861: error: 'theDisp' undeclared (first use in this function)[/SIZE]
[SIZE=2]HGraf.c:862: warning: implicit declaration of function 'XCloseDisplay'[/SIZE]
[SIZE=2]make[1]: ** [HGraf.o] Erro 1[/SIZE]
[SIZE=2]make[1]: Saindo do diretório `/home/tatiane/bin/htk/HTKLib'[/SIZE]
[SIZE=2]make: ** [HTKLib/HTKLib.a] Erro 1[/SIZE]
[/SIZE][/SIZE]

---

### Post by Partyboi2 on 2009-04-25
tati_vital, have you go the libx11-dev package installed?

---

### Post by tati_vital on 2009-04-26
Partyboi2, thank you for your attention.
 
I verified my system and there are some folders (libx11-6, libx11-data, libx11-xcb1, libx86-1 and others) in path /usr/share/doc/. Can be a problem on version of libx11 ? I'm using a AMD 64 bits processor.

---

### Post by Partyboi2 on 2009-04-26
From a terminal can you post the output to
```
apt-cache policy libx11-dev
```

---

### Post by tati_vital on 2009-04-27
You are correct because the command return a response that was impossible found lib11-dev.
 
Response in Portuguese:
 
[SIZE=2]tatiane@tatiane-vital:/usr/share/doc$ apt-cache policy libx11-dev[/SIZE]
[SIZE=2]W: ImpossÃvel encontrar o pacote libx11-dev[/SIZE]
 
[SIZE=2][SIZE=2]tatiane@tatiane-vital:/usr/share/doc$ ls | grep libx[/SIZE]
[SIZE=2]libx11-6[/SIZE]
[SIZE=2]libx11-data[/SIZE]
[SIZE=2]libx11-xcb1[/SIZE]
[SIZE=2]libx86-1[/SIZE]
[SIZE=2]libxapian15[/SIZE]
[SIZE=2]libxau6[/SIZE]
[SIZE=2]libxaw7[/SIZE]
[SIZE=2]libxcb1[/SIZE]
[SIZE=2]libxcb-render0[/SIZE]
[SIZE=2]libxcb-render-util0[/SIZE]
[SIZE=2]libxcb-xlib0[/SIZE]
[SIZE=2]libxcomposite1[/SIZE]
[SIZE=2]libxcursor1[/SIZE]
[SIZE=2]libxdamage1[/SIZE]
[SIZE=2]libxdmcp6[/SIZE]
[SIZE=2]libxevie1[/SIZE]
[SIZE=2]libxext6[/SIZE]
[SIZE=2]libxfixes3[/SIZE]
[SIZE=2]libxfont1[/SIZE]
[SIZE=2]libxft2[/SIZE]
[SIZE=2]libxi6[/SIZE]
[SIZE=2]libxinerama1[/SIZE]
[SIZE=2]libxkbfile1[/SIZE]
[SIZE=2]libxklavier12[/SIZE]
[SIZE=2]libxml2[/SIZE]
[SIZE=2]libxml2-utils[/SIZE]
[SIZE=2]libxml-namespacesupport-perl[/SIZE]
[SIZE=2]libxml-parser-perl[/SIZE]
[SIZE=2]libxml-sax-expat-perl[/SIZE]
[SIZE=2]libxml-sax-perl[/SIZE]
[SIZE=2]libxml-simple-perl[/SIZE]
[SIZE=2]libxml-twig-perl[/SIZE]
[SIZE=2]libxml-xpath-perl[/SIZE]
[SIZE=2]libxmu6[/SIZE]
[SIZE=2]libxmuu1[/SIZE]
[SIZE=2]libxp6[/SIZE]
[SIZE=2]libxplc0.3.13[/SIZE]
[SIZE=2]libxpm4[/SIZE]
[SIZE=2]libxrandr2[/SIZE]
[SIZE=2]libxrender1[/SIZE]
[SIZE=2]libxres1[/SIZE]
[SIZE=2]libxslt1.1[/SIZE]
[SIZE=2]libxss1[/SIZE]
[SIZE=2]libxt6[/SIZE]
[SIZE=2]libxtrap6[/SIZE]
[SIZE=2]libxtst6[/SIZE]
[SIZE=2]libxv1[/SIZE]
[SIZE=2]libxxf86dga1[/SIZE]
[SIZE=2]libxxf86misc1[/SIZE]
[SIZE=2]libxxf86vm1[/SIZE]
[SIZE=2]python-libxml2[/SIZE]
 
[SIZE=2]Do you have a sugestion to solve this problem ?[/SIZE]
 
[SIZE=2]Thank you.[/SIZE]
[/SIZE]

---

### Post by Partyboi2 on 2009-04-27
I don't speak Portuguese but it looks like libx11-dev may not be installed. Open a terminal and try installing libx11-dev with
```
sudo apt-get install libx11-dev
```

---

### Post by tati_vital on 2009-04-28
I done the download of 2 versions of libx11-dev, but I didn`t have success.
 
tatiane@tatiane-vital:~$ sudo apt-get install libx11-dev_1.1.3-1ubuntu2_amd64.deb 
Reading package lists... Done 
Building dependency tree 
Reading state information... Done 
E: Couldn't find packagelibx11-dev_1.1.3-1ubuntu2_amd64.deb
tatiane@tatiane-vital:~$ sudo apt-get install libx11-dev_1.1.3-1ubuntu2_i386.deb 
Reading package lists... Done 
Building dependency tree 
Reading state information... Done 
E: Couldn't find package libx11-dev_1.1.3-1ubuntu2_amd64.deb
tatiane@tatiane-vital:~$ ls
bin Documents libx11-dev_1.1.3-1ubuntu2_amd64.deb Music PÃºblica
Desktop Examples libx11-dev_1.1.3-1ubuntu2_i386.deb MÃºsicas VÃ&shy;deos
Documentos Imagens Modelos

---

### Post by Partyboi2 on 2009-04-28
> **tati_vital said:**
> I done the download of 2 versions of libx11-dev, but I didn`t have success.
 
tatiane@tatiane-vital:~$ sudo apt-get install libx11-dev_1.1.3-1ubuntu2_amd64.deb 
Reading package lists... Done 
Building dependency tree 
Reading state information... Done 
E: Couldn't find packagelibx11-dev_1.1.3-1ubuntu2_amd64.deb
tatiane@tatiane-vital:~$ sudo apt-get install libx11-dev_1.1.3-1ubuntu2_i386.deb 
Reading package lists... Done 
Building dependency tree 
Reading state information... Done 
E: Couldn't find package libx11-dev_1.1.3-1ubuntu2_amd64.deb
tatiane@tatiane-vital:~$ ls
bin Documents libx11-dev_1.1.3-1ubuntu2_amd64.deb Music PÃºblica
Desktop Examples libx11-dev_1.1.3-1ubuntu2_i386.deb MÃºsicas VÃ*deos
Documentos Imagens Modelos
You do not need to add "_1.1.3-1ubuntu2_amd64.deb" to the end of the package when using apt-get, so only type
```
sudo apt-get install libx11-dev
```

---

### Post by tati_vital on 2009-04-29
I installed the lib11-dev (and other packages) and ran "./configure", "make all" and "make install", but I had a problem testing the HTKDEMO, like showed below:

tatiane@tatiane-vital:~/bin/htk/htk/samples/HTKDemo$ ./runDemo configs/monPlainM1S1.dcf
 Test Config File Read
 =====================
Parameter         Value
-----------------------

hsKind              p
covKind             d
nStreams            1
nMixes              1
Context             m
TiedState           n
VQ_clust            l
HERest_Iter         3
HERest_par_mode     n
Clean_up            y
Trace_tool_calls    y


HCopy               n
HList               n
HQuant              n
HLEd                n
HInit               y
HRest               y
HERest              y
HSmooth             n
HVite               y

Cleaning up directories
Done cleaning


./MakeProtoHMMSet protoconfs/proto_s1_m1_dc.pcf
 Proto Config File Read
 ======================
Parameter         Value
-----------------------

hsKind              p
covKind             d
nStates             3
nStreams            1
sWidths             26
mixes               1
parmKind            MFCC_E_D
vecSize             26
outDir              proto
hmmList             lists/bcplist

Can't open proto at ./MakeProtoHMMSet line 101, <> line 21.
Can't open hmms/hmm.0

Can be a problem in my installing ?

---

### Post by Partyboi2 on 2009-04-29
Create in the HTKDemo directorya  new directory called proto and  hmms/hmm.0
So change directory into the HTKDemo directory and create the directories with
```
mkdir proto
mkdir hmms
mkdir hmms/hmm.0
```then run .```
/runDemo configs/monPlainM1S1.dcf
``` again If it says it cannot open any of the following create the directory for them
```
hmms/hmm.1 
hmms/hmm.2
test
```

---

### Post by tati_vital on 2009-05-11
Partyboi2, Thank you for your support. Htk works in my system now.

---

### Post by romanhr on 2009-05-15
Hi, I already install libx11-dev but when i run make all it doesn't work

(cd HTKLib && make HTKLib.a) \
      || case "" in *k*) fail=yes;; *) exit 1;; esac;
make[1]: se ingresa al directorio `/bin/htk/htk/HTKLib'
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HGraf.o HGraf.c
En el archivo incluído de /usr/include/features.h:354,
                 from /usr/include/stdio.h:28,
                 from HShell.h:40,
                 from HGraf.c:54:
/usr/include/gnu/stubs.h:7:27: error: gnu/stubs-32.h: No existe el fichero ó directorio
make[1]: *** [HGraf.o] Error 1
make[1]: se sale del directorio `/bin/htk/htk/HTKLib'
make: *** [HTKLib/HTKLib.a] Error 1

It's said something about that the directory doesn't exist 

If anyone can help me i will appreciate

---

### Post by Partyboi2 on 2009-05-16
> **romanhr said:**
> Hi, I already install libx11-dev but when i run make all it doesn't work

(cd HTKLib && make HTKLib.a) \
      || case "" in *k*) fail=yes;; *) exit 1;; esac;
make[1]: se ingresa al directorio `/bin/htk/htk/HTKLib'
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HGraf.o HGraf.c
En el archivo incluído de /usr/include/features.h:354,
                 from /usr/include/stdio.h:28,
                 from HShell.h:40,
                 from HGraf.c:54:
/usr/include/gnu/stubs.h:7:27: error: gnu/stubs-32.h: No existe el fichero ó directorio
make[1]: *** [HGraf.o] Error 1
make[1]: se sale del directorio `/bin/htk/htk/HTKLib'
make: *** [HTKLib/HTKLib.a] Error 1

It's said something about that the directory doesn't exist 

If anyone can help me i will appreciate

Did you get any errors when you ran the ./configure command? Also do you have the libc6-dev installed?

---

### Post by romanhr on 2009-05-17
when i ran ./configure i have this, apparently i don't have any errors

```

root@roman-laptop:/bin/htk/htk# ./configure
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
checking for gcc option to accept ISO C89... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ranlib... ranlib
checking for main in -lX11... yes
checking for main in -lm... yes
checking how to run the C preprocessor... gcc -E
checking for X... libraries , headers 
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
config.status: WARNING:  HTKLib/Makefile.in seems to ignore the --datarootdir setting
config.status: creating HTKTools/Makefile
config.status: WARNING:  HTKTools/Makefile.in seems to ignore the --datarootdir setting
config.status: creating HLMLib/Makefile
config.status: WARNING:  HLMLib/Makefile.in seems to ignore the --datarootdir setting
config.status: creating HLMTools/Makefile
config.status: WARNING:  HLMTools/Makefile.in seems to ignore the --datarootdir setting
config.status: creating HTKLVRec/Makefile
config.status: WARNING:  HTKLVRec/Makefile.in seems to ignore the --datarootdir setting
config.status: creating Makefile
config.status: WARNING:  Makefile.in seems to ignore the --datarootdir setting
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
root@roman-laptop:/bin/htk/htk# aptitude search libc6-dev
i   libc6-dev                       - GNU C Library: Development Libraries and H
p   libc6-dev-i386                  - GNU C Library: 32bit development libraries

``` 

and libc6 it is installed

---

### Post by Partyboi2 on 2009-05-17
> **romanhr said:**
> when i ran ./configure i have this, apparently i don't have any errors

```

root@roman-laptop:/bin/htk/htk# ./configure
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
checking for gcc option to accept ISO C89... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ranlib... ranlib
checking for main in -lX11... yes
checking for main in -lm... yes
checking how to run the C preprocessor... gcc -E
checking for X... libraries , headers 
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
config.status: WARNING:  HTKLib/Makefile.in seems to ignore the --datarootdir setting
config.status: creating HTKTools/Makefile
config.status: WARNING:  HTKTools/Makefile.in seems to ignore the --datarootdir setting
config.status: creating HLMLib/Makefile
config.status: WARNING:  HLMLib/Makefile.in seems to ignore the --datarootdir setting
config.status: creating HLMTools/Makefile
config.status: WARNING:  HLMTools/Makefile.in seems to ignore the --datarootdir setting
config.status: creating HTKLVRec/Makefile
config.status: WARNING:  HTKLVRec/Makefile.in seems to ignore the --datarootdir setting
config.status: creating Makefile
config.status: WARNING:  Makefile.in seems to ignore the --datarootdir setting
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
root@roman-laptop:/bin/htk/htk# aptitude search libc6-dev
i   libc6-dev                       - GNU C Library: Development Libraries and H
p   libc6-dev-i386                  - GNU C Library: 32bit development libraries

```and libc6 it is installed
Are you using the 64bit version of Ubuntu?

---

### Post by romanhr on 2009-05-17
Yes i have Ubuntu 8.10 64bits

---

### Post by Partyboi2 on 2009-05-17
Try installing the  libc6-dev-i386 package.
```
sudo apt-get install libc6-dev-i386
```

---

### Post by romanhr on 2009-05-19
I installed this library and ran "./configure " "make all" "make install" and this is what i have
[LEFT]
root@roman-laptop:/bin/htk/htk# ./configure
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
checking for gcc option to accept ISO C89... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ranlib... ranlib
checking for main in -lX11... yes
checking for main in -lm... yes
checking how to run the C preprocessor... gcc -E
checking for X... libraries , headers 
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
config.status: WARNING:  HTKLib/Makefile.in seems to ignore the --datarootdir setting
config.status: creating HTKTools/Makefile
config.status: WARNING:  HTKTools/Makefile.in seems to ignore the --datarootdir setting
config.status: creating HLMLib/Makefile
config.status: WARNING:  HLMLib/Makefile.in seems to ignore the --datarootdir setting
config.status: creating HLMTools/Makefile
config.status: WARNING:  HLMTools/Makefile.in seems to ignore the --datarootdir setting
config.status: creating HTKLVRec/Makefile
config.status: WARNING:  HTKLVRec/Makefile.in seems to ignore the --datarootdir setting
config.status: creating Makefile
config.status: WARNING:  Makefile.in seems to ignore the --datarootdir setting
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
root@roman-laptop:/bin/htk/htk# make all
(cd HTKLib && make HTKLib.a) \
      || case "" in *k*) fail=yes;; *) exit 1;; esac;
make[1]: se ingresa al directorio `/bin/htk/htk/HTKLib'
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HGraf.o HGraf.c
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o esig_asc.o esig_asc.c
esig_asc.c: En la función &#8216;ReadAsciiEscape&#8217;:
esig_asc.c:2025: aviso: se descarta el valor de devolución de &#8216;fscanf&#8217;, se declaró con el atributo warn_unused_result
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o esig_edr.o esig_edr.c
esig_edr.c: En la función &#8216;ReadEdrRecord&#8217;:
esig_edr.c:309: aviso: puede ser que se utilice &#8216;flags&#8217; sin inicializar en esta función
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o esignal.o esignal.c
esignal.c: En la función &#8216;WriteHeader&#8217;:
esignal.c:1242: aviso: se descarta el valor de devolución de &#8216;fwrite&#8217;, se declaró con el atributo warn_unused_result
esignal.c: En la función &#8216;GetLine&#8217;:
esignal.c:1760: aviso: se descarta el valor de devolución de &#8216;fgets&#8217;, se declaró con el atributo warn_unused_result
esignal.c: En la función &#8216;GetLong&#8217;:
esignal.c:1808: aviso: se descarta el valor de devolución de &#8216;fgets&#8217;, se declaró con el atributo warn_unused_result
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o esig_nat.o esig_nat.c
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HAdapt.o HAdapt.c
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HArc.o HArc.c
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HAudio.o HAudio.c
HAudio.c: En la función &#8216;StartAudioInput&#8217;:
HAudio.c:2174: aviso: se descarta el valor de devolución de &#8216;read&#8217;, se declaró con el atributo warn_unused_result
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HDict.o HDict.c
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HExactMPE.o HExactMPE.c
HExactMPE.c: En la función &#8216;DoCorrectness&#8217;:
HExactMPE.c:288: aviso: no se utiliza el valor calculado
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HFB.o HFB.c
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HFBLat.o HFBLat.c
HFBLat.c: En la función &#8216;DoAllMixUpdates&#8217;:
HFBLat.c:1074: aviso: puede ser que se utilice &#8216;mammi&#8217; sin inicializar en esta función
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HLabel.o HLabel.c
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HLat.o HLat.c
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HLM.o HLM.c
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HMap.o HMap.c
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HMath.o HMath.c
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HMem.o HMem.c
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HModel.o HModel.c
HModel.c: En la función &#8216;PutBaseClass&#8217;:
HModel.c:2958: aviso: puede ser que se utilice &#8216;comp&#8217; sin inicializar en esta función
HModel.c:2958: aviso: puede ser que se utilice &#8216;stream&#8217; sin inicializar en esta función
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HNet.o HNet.c
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HParm.o HParm.c
HParm.c: En la función &#8216;OpenAsChannel&#8217;:
HParm.c:4151: aviso: puede ser que se utilice &#8216;initRows&#8217; sin inicializar en esta función
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HRec.o HRec.c
HRec.c: En la función &#8216;LatFromPaths&#8217;:
HRec.c:1520: aviso: puede ser que se utilice &#8216;labid&#8217; sin inicializar en esta función
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HShell.o HShell.c
HShell.c: En la función &#8216;NextArg&#8217;:
HShell.c:725: aviso: se descarta el valor de devolución de &#8216;strtod&#8217;, se declaró con el atributo warn_unused_result
HShell.c: En la función &#8216;KeyPressed&#8217;:
HShell.c:1489: aviso: se descarta el valor de devolución de &#8216;read&#8217;, se declaró con el atributo warn_unused_result
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HSigP.o HSigP.c
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HTrain.o HTrain.c
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HUtil.o HUtil.c
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HVQ.o HVQ.c
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o HWave.o HWave.c
HWave.c: En la función &#8216;GetWAVHeaderInfo&#8217;:
HWave.c:1062: aviso: se descarta el valor de devolución de &#8216;fread&#8217;, se declaró con el atributo warn_unused_result
HWave.c:1068: aviso: se descarta el valor de devolución de &#8216;fread&#8217;, se declaró con el atributo warn_unused_result
HWave.c:1069: aviso: se descarta el valor de devolución de &#8216;fread&#8217;, se declaró con el atributo warn_unused_result
HWave.c:1081: aviso: se descarta el valor de devolución de &#8216;fread&#8217;, se declaró con el atributo warn_unused_result
HWave.c:1082: aviso: se descarta el valor de devolución de &#8216;fread&#8217;, se declaró con el atributo warn_unused_result
HWave.c:1087: aviso: se descarta el valor de devolución de &#8216;fread&#8217;, se declaró con el atributo warn_unused_result
HWave.c:1097: aviso: se descarta el valor de devolución de &#8216;fread&#8217;, se declaró con el atributo warn_unused_result
HWave.c:1105: aviso: se descarta el valor de devolución de &#8216;fread&#8217;, se declaró con el atributo warn_unused_result
HWave.c:1108: aviso: se descarta el valor de devolución de &#8216;fread&#8217;, se declaró con el atributo warn_unused_result
HWave.c:1109: aviso: se descarta el valor de devolución de &#8216;fread&#8217;, se declaró con el atributo warn_unused_result
HWave.c:1110: aviso: se descarta el valor de devolución de &#8216;fread&#8217;, se declaró con el atributo warn_unused_result
HWave.c:1125: aviso: se descarta el valor de devolución de &#8216;fread&#8217;, se declaró con el atributo warn_unused_result
HWave.c: En la función &#8216;PutESIGHeaderInfo&#8217;:
HWave.c:1342: aviso: puede ser que se utilice &#8216;inList&#8217; sin inicializar en esta función
gcc  -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I. -DPHNALG   -c -o strarr.o strarr.c
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
make[1]: se sale del directorio `/bin/htk/htk/HTKLib'
(cd HTKTools && make all) \
      || case "" in *k*) fail=yes;; *) exit 1;; esac;
make[1]: se ingresa al directorio `/bin/htk/htk/HTKTools'
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
if [ xHSLab = xHSLab ] ; then \
        gcc -o HSLab -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HSLab.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm -lX11 ; \
        else \
        gcc -o HSLab -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HSLab.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm ; fi
HSLab.c: En la función &#8216;DoSpecial&#8217;:
HSLab.c:1596: aviso: se descarta el valor de devolución de &#8216;system&#8217;, se declaró con el atributo warn_unused_result
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.2/../../../libX11.so when searching for -lX11
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.2/../../../libX11.a when searching for -lX11
/usr/bin/ld: skipping incompatible /usr/lib/libX11.so when searching for -lX11
/usr/bin/ld: skipping incompatible /usr/lib/libX11.a when searching for -lX11
/usr/bin/ld: cannot find -lX11
collect2: ld devolvió el estado de salida 1
make[1]: *** [HSLab] Error 1
make[1]: se sale del directorio `/bin/htk/htk/HTKTools'
make: *** [htktools] Error 1
root@roman-laptop:/bin/htk/htk# make install
(cd HTKTools && make all) \
      || case "" in *k*) fail=yes;; *) exit 1;; esac;
make[1]: se ingresa al directorio `/bin/htk/htk/HTKTools'
if [ ! -d /usr/local/bin -a X_ = X_yes ] ; then mkdir -p /usr/local/bin ; fi
if [ xHSLab = xHSLab ] ; then \
        gcc -o HSLab -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HSLab.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm -lX11 ; \
        else \
        gcc -o HSLab -m32 -ansi -D_SVID_SOURCE -DOSS_AUDIO -D'ARCH="x86_64"' -Wall -Wno-switch -g -O2 -I../HTKLib -DPHNALG HSLab.c ../HTKLib/HTKLib.a -L/usr/X11R6/lib  -lm ; fi
HSLab.c: En la función &#8216;DoSpecial&#8217;:
HSLab.c:1596: aviso: se descarta el valor de devolución de &#8216;system&#8217;, se declaró con el atributo warn_unused_result
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.2/../../../libX11.so when searching for -lX11
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.2/../../../libX11.a when searching for -lX11
/usr/bin/ld: skipping incompatible /usr/lib/libX11.so when searching for -lX11
/usr/bin/ld: skipping incompatible /usr/lib/libX11.a when searching for -lX11
/usr/bin/ld: cannot find -lX11
collect2: ld devolvió el estado de salida 1
make[1]: *** [HSLab] Error 1
make[1]: se sale del directorio `/bin/htk/htk/HTKTools'
make: *** [htktools] Error 1
[LEFT]
[/LEFT]
[/LEFT]

---

### Post by Partyboi2 on 2009-05-19
What is the output for[FONT=monospace]
[/FONT]```
apt-cache policy libx11-dev
```

---

### Post by romanhr on 2009-05-19
This is the output 
```

root@roman-laptop:/home/roman# apt-cache policy libx11-dev
libx11-dev:
  Instalados: 2:1.1.5-2ubuntu1.1
  Candidato: 2:1.1.5-2ubuntu1.1
  Tabla de versión:
 *** 2:1.1.5-2ubuntu1.1 0
        500 http://ve.archive.ubuntu.com intrepid-updates/main Packages
        100 /var/lib/dpkg/status
     2:1.1.5-2ubuntu1 0
        500 http://ve.archive.ubuntu.com intrepid/main Packages


```

---

### Post by Rechild12 on 2009-09-29
Using

```
sudo ./getlibs -p libx11-dev
```is one way around this. The getlibs file can be downloaded from [http://frozenfox.freehostia.com/cappy/](http://frozenfox.freehostia.com/cappy/)

---

### Post by malathy on 2010-02-09
this is the perfect site i have ever come across
the advice u people posts are wasome
i have done till "make"
now if i do"make install"
i have all sort of this output
malathy-desktop:~/Desktop/htk> make install
(cd HTKTools && make all) \
      || case "" in *k*) fail=yes;; *) exit 1;; esac;
make[1]: Entering directory `/home/malathy/Desktop/htk/HTKTools'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/malathy/Desktop/htk/HTKTools'
(cd HTKTools && make install) \
    || case "" in *k*) fail=yes;; *) exit 1;; esac;
make[1]: Entering directory `/home/malathy/Desktop/htk/HTKTools'
if [ ! -d /usr/local/bin ] ; then mkdir /usr/local/bin ; fi
for program in HSLab HBuild HCompV HCopy HDMan HERest HHEd HInit HLEd     HList HLRescore HLStats HMMIRest HParse HQuant HRest HResults HSGen HSmooth HVite  ; do /usr/bin/install -c -m 755 ${program} /usr/local/bin ; done
/usr/bin/install: cannot create regular file `/usr/local/bin/HSLab': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/bin/HBuild': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/bin/HCompV': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/bin/HCopy': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/bin/HDMan': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/bin/HERest': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/bin/HHEd': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/bin/HInit': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/bin/HLEd': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/bin/HList': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/bin/HLRescore': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/bin/HLStats': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/bin/HMMIRest': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/bin/HParse': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/bin/HQuant': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/bin/HRest': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/bin/HResults': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/bin/HSGen': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/bin/HSmooth': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/bin/HVite': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/malathy/Desktop/htk/HTKTools'
make: *** [install-htktools] Error 1
malathy-desktop:~/Desktop/htk> 



PLS HELP ME 
i am struggling for more than a month

thanks in advance

---

### Post by johnaaronrose on 2010-05-04
Try:
sudo make install

For me this allowed creation of the various HL & HS files in /usr/local/bin, though I still got your earlier mesages. The reason that I compiled htk was that I did a full install of Lucid. However, simon (the kde speech to text app) immediately crashed.

---

### Post by bejimed on 2010-07-01
i had a problem when i try to test the htkdemo and type the command ./runDemo configs/monPlainM1S1.dcf .how ever ihas created the directory proto ; hmms/hmm.0 ,hmms/hmm.1  and hmms/hmm.2 into the TKdemo directory so please help me 

 Number of owners = 1
 SegLab   :  S
 maxIter  :  10
 epsilon  :  0.000100
 minSeg   :  3
 Updating :  Means Variances MixWeights/DProbs TransProbs

 - system is PLAIN
16 Observation Sequences Loaded
Starting Estimation Process
Iteration 1: Average LogP =  -804.22485
Iteration 2: Average LogP =  -786.82153  Change =    17.40332
Iteration 3: Average LogP =  -786.21497  Change =     0.60657
Iteration 4: Average LogP =  -786.21503  Change =    -0.00006
Estimation converged at iteration 5
Output written to directory hmms/hmm.0

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
                  KEEPDISTINCT               FALSE
                  SAVEGLOBOPTS                TRUE
                  TARGETKIND              MFCC_E_D



Calling HInit for HMM C
HInit -A -i 10 -L labels/bcplabs/mon -l C -o C -C toolconfs/hinit.conf -D -M hmms/hmm.0 -T 1 proto/C data/train/tr1.mfc data/train/tr2.mfc data/train/tr3.mfc data/train/tr4.mfc data/train/tr5.mfc data/train/tr6.mfc data/train/tr7.mfc 

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
#                 KEEPDISTINCT               FALSE
#                 SAVEGLOBOPTS                TRUE
#                 TARGETKIND              MFCC_E_D

Initialising  HMM proto/C . . . 
 States   :   2  3  4 (width)
 Mixes  s1:   1  1  1 ( 26  )
 Num Using:   0  0  0
 Parm Kind:  MFCC_E_D
 Number of owners = 1
 SegLab   :  C
 maxIter  :  10
 epsilon  :  0.000100
 minSeg   :  3
 Updating :  Means Variances MixWeights/DProbs TransProbs

 - system is PLAIN
90 Observation Sequences Loaded
Starting Estimation Process
Iteration 1: Average LogP =  -531.87134
Iteration 2: Average LogP =  -527.31677  Change =     4.55458
Iteration 3: Average LogP =  -526.60242  Change =     0.71439
Iteration 4: Average LogP =  -526.32343  Change =     0.27898
Iteration 5: Average LogP =  -526.26605  Change =     0.05737
Iteration 6: Average LogP =  -526.24451  Change =     0.02152
Iteration 7: Average LogP =  -526.23560  Change =     0.00892
Iteration 8: Average LogP =  -526.23364  Change =     0.00196
Iteration 9: Average LogP =  -526.22852  Change =     0.00513
Iteration 10: Average LogP =  -526.22852  Change =     0.00000
Estimation converged at iteration 11
Output written to directory hmms/hmm.0

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
                  KEEPDISTINCT               FALSE
                  SAVEGLOBOPTS                TRUE
                  TARGETKIND              MFCC_E_D



Calling HInit for HMM V
HInit -A -i 10 -L labels/bcplabs/mon -l V -o V -C toolconfs/hinit.conf -D -M hmms/hmm.0 -T 1 proto/V data/train/tr1.mfc data/train/tr2.mfc data/train/tr3.mfc data/train/tr4.mfc data/train/tr5.mfc data/train/tr6.mfc data/train/tr7.mfc 

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
#                 KEEPDISTINCT               FALSE
#                 SAVEGLOBOPTS                TRUE
#                 TARGETKIND              MFCC_E_D

Initialising  HMM proto/V . . . 
 States   :   2  3  4 (width)
 Mixes  s1:   1  1  1 ( 26  )
 Num Using:   0  0  0
 Parm Kind:  MFCC_E_D
 Number of owners = 1
 SegLab   :  V
 maxIter  :  10
 epsilon  :  0.000100
 minSeg   :  3
 Updating :  Means Variances MixWeights/DProbs TransProbs

 - system is PLAIN
68 Observation Sequences Loaded
Starting Estimation Process
Iteration 1: Average LogP =  -599.68671
Iteration 2: Average LogP =  -592.98328  Change =     6.70342
Iteration 3: Average LogP =  -592.21442  Change =     0.76883
Iteration 4: Average LogP =  -591.48163  Change =     0.73280
Iteration 5: Average LogP =  -591.14313  Change =     0.33848
Iteration 6: Average LogP =  -591.08777  Change =     0.05535
Iteration 7: Average LogP =  -591.05005  Change =     0.03773
Iteration 8: Average LogP =  -590.98999  Change =     0.06004
Iteration 9: Average LogP =  -590.98560  Change =     0.00441
Iteration 10: Average LogP =  -590.98558  Change =     0.00001
Estimation converged at iteration 11
Output written to directory hmms/hmm.0

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
                  KEEPDISTINCT               FALSE
                  SAVEGLOBOPTS                TRUE
                  TARGETKIND              MFCC_E_D



Calling HInit for HMM N
HInit -A -i 10 -L labels/bcplabs/mon -l N -o N -C toolconfs/hinit.conf -D -M hmms/hmm.0 -T 1 proto/N data/train/tr1.mfc data/train/tr2.mfc data/train/tr3.mfc data/train/tr4.mfc data/train/tr5.mfc data/train/tr6.mfc data/train/tr7.mfc 

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
#                 KEEPDISTINCT               FALSE
#                 SAVEGLOBOPTS                TRUE
#                 TARGETKIND              MFCC_E_D

Initialising  HMM proto/N . . . 
 States   :   2  3  4 (width)
 Mixes  s1:   1  1  1 ( 26  )
 Num Using:   0  0  0
 Parm Kind:  MFCC_E_D
 Number of owners = 1
 SegLab   :  N
 maxIter  :  10
 epsilon  :  0.000100
 minSeg   :  3
 Updating :  Means Variances MixWeights/DProbs TransProbs

 - system is PLAIN
16 Observation Sequences Loaded
Starting Estimation Process
Iteration 1: Average LogP =  -398.18735
Iteration 2: Average LogP =  -395.48718  Change =     2.70016
Iteration 3: Average LogP =  -395.26947  Change =     0.21771
Iteration 4: Average LogP =  -395.17661  Change =     0.09286
Iteration 5: Average LogP =  -395.17661  Change =     0.00000
Estimation converged at iteration 6
Output written to directory hmms/hmm.0

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
                  KEEPDISTINCT               FALSE
                  SAVEGLOBOPTS                TRUE
                  TARGETKIND              MFCC_E_D



Calling HInit for HMM L
HInit -A -i 10 -L labels/bcplabs/mon -l L -o L -C toolconfs/hinit.conf -D -M hmms/hmm.0 -T 1 proto/L data/train/tr1.mfc data/train/tr2.mfc data/train/tr3.mfc data/train/tr4.mfc data/train/tr5.mfc data/train/tr6.mfc data/train/tr7.mfc 

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
#                 KEEPDISTINCT               FALSE
#                 SAVEGLOBOPTS                TRUE
#                 TARGETKIND              MFCC_E_D

Initialising  HMM proto/L . . . 
 States   :   2  3  4 (width)
 Mixes  s1:   1  1  1 ( 26  )
 Num Using:   0  0  0
 Parm Kind:  MFCC_E_D
 Number of owners = 1
 SegLab   :  L
 maxIter  :  10
 epsilon  :  0.000100
 minSeg   :  3
 Updating :  Means Variances MixWeights/DProbs TransProbs

 - system is PLAIN
25 Observation Sequences Loaded
Starting Estimation Process
Iteration 1: Average LogP =  -424.39636
Iteration 2: Average LogP =  -420.31281  Change =     4.08355
Iteration 3: Average LogP =  -419.43475  Change =     0.87804
Iteration 4: Average LogP =  -419.35437  Change =     0.08038
Iteration 5: Average LogP =  -419.32385  Change =     0.03050
Iteration 6: Average LogP =  -419.32387  Change =    -0.00001
Estimation converged at iteration 7
Output written to directory hmms/hmm.0

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
                  KEEPDISTINCT               FALSE
                  SAVEGLOBOPTS                TRUE
                  TARGETKIND              MFCC_E_D



Calling HRest for HMM S
HRest -A -u tmvw -w 3 -v 0.05 -i 10 -L labels/bcplabs/mon -l S -C toolconfs/hrest.conf -D -M hmms/hmm.1 -T 1 hmms/hmm.0/S data/train/tr1.mfc data/train/tr2.mfc data/train/tr3.mfc data/train/tr4.mfc data/train/tr5.mfc data/train/tr6.mfc data/train/tr7.mfc 

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
#                 KEEPDISTINCT               FALSE
#                 SAVEGLOBOPTS                TRUE
#                 TARGETKIND              MFCC_E_D

Reestimating HMM hmms/hmm.0/S . . . 
 States   :   2  3  4 (width)
 Mixes  s1:   1  1  1 ( 26  )
 Num Using:   0  0  0
 Parm Kind:  MFCC_E_D
 Number of owners = 1
 SegLab   :  S
 MaxIter  :  10
 Epsilon  :  0.000100
 Updating :  Transitions Means Variances 

 - system is PLAIN
16 Examples loaded, Max length = 20, Min length = 13
Ave LogProb at iter 1 = -785.97754 using 16 examples
Ave LogProb at iter 2 = -799.75970 using 16 examples  change =  -13.78217
Ave LogProb at iter 3 = -799.59235 using 16 examples  change =    0.16736
Ave LogProb at iter 4 = -799.49408 using 16 examples  change =    0.09827
Ave LogProb at iter 5 = -799.43396 using 16 examples  change =    0.06012
Ave LogProb at iter 6 = -799.36908 using 16 examples  change =    0.06488
Ave LogProb at iter 7 = -799.31201 using 16 examples  change =    0.05707
Ave LogProb at iter 8 = -799.28625 using 16 examples  change =    0.02576
Ave LogProb at iter 9 = -799.26813 using 16 examples  change =    0.01813
Ave LogProb at iter 10 = -798.93494 using 16 examples  change =    0.33319
Estimation aborted at iteration 10

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
                  KEEPDISTINCT               FALSE
                  SAVEGLOBOPTS                TRUE
                  TARGETKIND              MFCC_E_D



Calling HRest for HMM C
HRest -A -u tmvw -w 3 -v 0.05 -i 10 -L labels/bcplabs/mon -l C -C toolconfs/hrest.conf -D -M hmms/hmm.1 -T 1 hmms/hmm.0/C data/train/tr1.mfc data/train/tr2.mfc data/train/tr3.mfc data/train/tr4.mfc data/train/tr5.mfc data/train/tr6.mfc data/train/tr7.mfc 

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
#                 KEEPDISTINCT               FALSE
#                 SAVEGLOBOPTS                TRUE
#                 TARGETKIND              MFCC_E_D

Reestimating HMM hmms/hmm.0/C . . . 
 States   :   2  3  4 (width)
 Mixes  s1:   1  1  1 ( 26  )
 Num Using:   0  0  0
 Parm Kind:  MFCC_E_D
 Number of owners = 1
 SegLab   :  C
 MaxIter  :  10
 Epsilon  :  0.000100
 Updating :  Transitions Means Variances 

 - system is PLAIN
90 Examples loaded, Max length = 25, Min length = 3
Ave LogProb at iter 1 = -525.97860 using 90 examples
Ave LogProb at iter 2 = -530.95642 using 90 examples  change =   -4.97785
Ave LogProb at iter 3 = -530.95356 using 90 examples  change =    0.00286
Ave LogProb at iter 4 = -530.95312 using 90 examples  change =    0.00043
Ave LogProb at iter 5 = -530.95304 using 90 examples  change =    0.00009
Estimation converged at iteration 5

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
                  KEEPDISTINCT               FALSE
                  SAVEGLOBOPTS                TRUE
                  TARGETKIND              MFCC_E_D



Calling HRest for HMM V
HRest -A -u tmvw -w 3 -v 0.05 -i 10 -L labels/bcplabs/mon -l V -C toolconfs/hrest.conf -D -M hmms/hmm.1 -T 1 hmms/hmm.0/V data/train/tr1.mfc data/train/tr2.mfc data/train/tr3.mfc data/train/tr4.mfc data/train/tr5.mfc data/train/tr6.mfc data/train/tr7.mfc 

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
#                 KEEPDISTINCT               FALSE
#                 SAVEGLOBOPTS                TRUE
#                 TARGETKIND              MFCC_E_D

Reestimating HMM hmms/hmm.0/V . . . 
 States   :   2  3  4 (width)
 Mixes  s1:   1  1  1 ( 26  )
 Num Using:   0  0  0
 Parm Kind:  MFCC_E_D
 Number of owners = 1
 SegLab   :  V
 MaxIter  :  10
 Epsilon  :  0.000100
 Updating :  Transitions Means Variances 

 - system is PLAIN
68 Examples loaded, Max length = 28, Min length = 3
Ave LogProb at iter 1 = -590.79446 using 68 examples
Ave LogProb at iter 2 = -600.09358 using 68 examples  change =   -9.29914
Ave LogProb at iter 3 = -600.08226 using 68 examples  change =    0.01131
Ave LogProb at iter 4 = -600.07560 using 68 examples  change =    0.00668
Ave LogProb at iter 5 = -600.07071 using 68 examples  change =    0.00491
Ave LogProb at iter 6 = -600.06859 using 68 examples  change =    0.00215
Ave LogProb at iter 7 = -600.06830 using 68 examples  change =    0.00030
Ave LogProb at iter 8 = -600.06801 using 68 examples  change =    0.00028
Ave LogProb at iter 9 = -600.06801 using 68 examples  change =   -0.00002
Estimation converged at iteration 9

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
                  KEEPDISTINCT               FALSE
                  SAVEGLOBOPTS                TRUE
                  TARGETKIND              MFCC_E_D



Calling HRest for HMM N
HRest -A -u tmvw -w 3 -v 0.05 -i 10 -L labels/bcplabs/mon -l N -C toolconfs/hrest.conf -D -M hmms/hmm.1 -T 1 hmms/hmm.0/N data/train/tr1.mfc data/train/tr2.mfc data/train/tr3.mfc data/train/tr4.mfc data/train/tr5.mfc data/train/tr6.mfc data/train/tr7.mfc 

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
#                 KEEPDISTINCT               FALSE
#                 SAVEGLOBOPTS                TRUE
#                 TARGETKIND              MFCC_E_D

Reestimating HMM hmms/hmm.0/N . . . 
 States   :   2  3  4 (width)
 Mixes  s1:   1  1  1 ( 26  )
 Num Using:   0  0  0
 Parm Kind:  MFCC_E_D
 Number of owners = 1
 SegLab   :  N
 MaxIter  :  10
 Epsilon  :  0.000100
 Updating :  Transitions Means Variances 

 - system is PLAIN
16 Examples loaded, Max length = 13, Min length = 4
Ave LogProb at iter 1 = -395.06061 using 16 examples
Ave LogProb at iter 2 = -403.25287 using 16 examples  change =   -8.19226
Ave LogProb at iter 3 = -403.23053 using 16 examples  change =    0.02234
Ave LogProb at iter 4 = -403.20822 using 16 examples  change =    0.02231
Ave LogProb at iter 5 = -403.19427 using 16 examples  change =    0.01395
Ave LogProb at iter 6 = -403.19070 using 16 examples  change =    0.00357
Ave LogProb at iter 7 = -403.19000 using 16 examples  change =    0.00070
Ave LogProb at iter 8 = -403.18976 using 16 examples  change =    0.00024
Ave LogProb at iter 9 = -403.18970 using 16 examples  change =    0.00006
Estimation converged at iteration 9

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
                  KEEPDISTINCT               FALSE
                  SAVEGLOBOPTS                TRUE
                  TARGETKIND              MFCC_E_D



Calling HRest for HMM L
HRest -A -u tmvw -w 3 -v 0.05 -i 10 -L labels/bcplabs/mon -l L -C toolconfs/hrest.conf -D -M hmms/hmm.1 -T 1 hmms/hmm.0/L data/train/tr1.mfc data/train/tr2.mfc data/train/tr3.mfc data/train/tr4.mfc data/train/tr5.mfc data/train/tr6.mfc data/train/tr7.mfc 

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
#                 KEEPDISTINCT               FALSE
#                 SAVEGLOBOPTS                TRUE
#                 TARGETKIND              MFCC_E_D

Reestimating HMM hmms/hmm.0/L . . . 
 States   :   2  3  4 (width)
 Mixes  s1:   1  1  1 ( 26  )
 Num Using:   0  0  0
 Parm Kind:  MFCC_E_D
 Number of owners = 1
 SegLab   :  L
 MaxIter  :  10
 Epsilon  :  0.000100
 Updating :  Transitions Means Variances 

 - system is PLAIN
25 Examples loaded, Max length = 14, Min length = 4
Ave LogProb at iter 1 = -419.20465 using 25 examples
Ave LogProb at iter 2 = -425.78465 using 25 examples  change =   -6.58000
Ave LogProb at iter 3 = -425.76195 using 25 examples  change =    0.02268
Ave LogProb at iter 4 = -425.74531 using 25 examples  change =    0.01665
Ave LogProb at iter 5 = -425.73094 using 25 examples  change =    0.01436
Ave LogProb at iter 6 = -425.72137 using 25 examples  change =    0.00956
Ave LogProb at iter 7 = -425.71652 using 25 examples  change =    0.00485
Ave LogProb at iter 8 = -425.71375 using 25 examples  change =    0.00277
Ave LogProb at iter 9 = -425.71164 using 25 examples  change =    0.00210
Ave LogProb at iter 10 = -425.71000 using 25 examples  change =    0.00164
Estimation aborted at iteration 10

HTK Configuration Parameters[3]
  Module/Tool     Parameter                  Value
                  KEEPDISTINCT               FALSE
                  SAVEGLOBOPTS                TRUE
                  TARGETKIND              MFCC_E_D



Iteration 1 of Embedded Re-estimation
HERest -A -w 3 -v 0.05 -C toolconfs/herest.conf -u tmvw -d hmms/hmm.1 -D -M hmms/hmm.2 -L labels/bcplabs/mon -t 2000.0 -T 1 lists/bcplist data/train/tr1.mfc data/train/tr2.mfc data/train/tr3.mfc data/train/tr4.mfc data/train/tr5.mfc data/train/tr6.mfc data/train/tr7.mfc 

HTK Configuration Parameters[4]
  Module/Tool     Parameter                  Value
#                 BINARYACCFORMAT              TRUE
#                 KEEPDISTINCT                TRUE
#                 SAVEGLOBOPTS                TRUE
#                 TARGETKIND              MFCC_E_D

HERest  ML Updating: Transitions Means Variances 

 System is PLAIN
5 Logical/5 Physical Models Loaded, VecSize=26
Pruning-On[2000.0]
 Processing Data: tr1.mfc; Label tr1.lab
 Utterance prob per frame = -5.980291e+01
 Processing Data: tr2.mfc; Label tr2.lab
 Utterance prob per frame = -5.937575e+01
 Processing Data: tr3.mfc; Label tr3.lab
 Utterance prob per frame = -5.935562e+01
 Processing Data: tr4.mfc; Label tr4.lab
 Utterance prob per frame = -5.919727e+01
 Processing Data: tr5.mfc; Label tr5.lab
 Utterance prob per frame = -5.789522e+01
 Processing Data: tr6.mfc; Label tr6.lab
 Utterance prob per frame = -5.910780e+01
 Processing Data: tr7.mfc; Label tr7.lab
 Utterance prob per frame = -5.739422e+01
Total 27 floored variance elements in 15 different mixes
Saving hmm's to dir hmms/hmm.2
Reestimation complete - average log prob per frame = -5.900193e+01
     - total frames seen          = 1.811000e+03

HTK Configuration Parameters[4]
  Module/Tool     Parameter                  Value
                  BINARYACCFORMAT              TRUE
                  KEEPDISTINCT                TRUE
                  SAVEGLOBOPTS                TRUE
                  TARGETKIND              MFCC_E_D

cp: la cible `hmms/tmp' n'est pas un répertoire


Iteration 2 of Embedded Re-estimation
HERest -A -w 3 -v 0.05 -C toolconfs/herest.conf -u tmvw -d hmms/tmp -D -M hmms/hmm.2 -L labels/bcplabs/mon -t 2000.0 -T 1 lists/bcplist data/train/tr1.mfc data/train/tr2.mfc data/train/tr3.mfc data/train/tr4.mfc data/train/tr5.mfc data/train/tr6.mfc data/train/tr7.mfc 

HTK Configuration Parameters[4]
  Module/Tool     Parameter                  Value
#                 BINARYACCFORMAT              TRUE
#                 KEEPDISTINCT                TRUE
#                 SAVEGLOBOPTS                TRUE
#                 TARGETKIND              MFCC_E_D

  ERROR [+5010]  InitSource: Cannot open source file hmms/tmp/C
  ERROR [+7010]  LoadHMMSet: Can't find file
  ERROR [+2321]  Initialise: LoadHMMSet failed
 FATAL ERROR - Terminating program HERest
cp: la cible `hmms/tmp' n'est pas un répertoire


Iteration 3 of Embedded Re-estimation
HERest -A -w 3 -v 0.05 -C toolconfs/herest.conf -u tmvw -d hmms/tmp -D -M hmms/hmm.2 -L labels/bcplabs/mon -t 2000.0 -T 1 lists/bcplist data/train/tr1.mfc data/train/tr2.mfc data/train/tr3.mfc data/train/tr4.mfc data/train/tr5.mfc data/train/tr6.mfc data/train/tr7.mfc 

HTK Configuration Parameters[4]
  Module/Tool     Parameter                  Value
#                 BINARYACCFORMAT              TRUE
#                 KEEPDISTINCT                TRUE
#                 SAVEGLOBOPTS                TRUE
#                 TARGETKIND              MFCC_E_D

  ERROR [+5010]  InitSource: Cannot open source file hmms/tmp/C
  ERROR [+7010]  LoadHMMSet: Can't find file
  ERROR [+2321]  Initialise: LoadHMMSet failed
 FATAL ERROR - Terminating program HERest
cp: la cible `hmms/tmp' n'est pas un répertoire
Removed 0 files from hmms/tmp

Testing on the training set
Can't open test
root@beji-mohamed-desktop:~/Téléchargements/samples/HTKDemo#

---

### Post by bejimed on 2010-07-03
please answer me our friens it's very urgent

---

### Post by jean-louis on 2010-07-05
Hi Bejimed,

The error you get:
> **bejimed said:**
> 
Removed 0 files from hmms/tmp

Testing on the training set
Can't open test

seems to have been already discussed here (with some corrections I would propose, in red):
> **Partyboi2 said:**
> Create in the HTKDemo directory a  new directory called proto and  hmms/hmm.0
So change directory into the HTKDemo directory and create the directories with
```

mkdir proto
mkdir hmms
mkdir hmms/hmm.0

```then run
```
[COLOR=Red].[/COLOR]/runDemo configs/monPlainM1S1.dcf
```again. If it says it cannot open any of the following create the directory for them
```

[COLOR=Red]mkdir[/COLOR] hmms/hmm.1 
[COLOR=Red]mkdir[/COLOR] hmms/hmm.2
[COLOR=Red]mkdir[/COLOR] test

```

That has solved the runDemo problem for me. Now let's see whether I can do other things with HTK... 

By the way, I also found that information on that blog:
[http://jrgemini.blogspot.com/2008/07/htk-rundemo.html](http://jrgemini.blogspot.com/2008/07/htk-rundemo.html)
whose author believes that problem might come from a bad Perl interpreter. I did not check that yet, though. 

cheers,

jean-louis

---

### Post by bejimed on 2010-07-06
Thank you for your support. Htk works in my system now.

---

### Post by halfblood88 on 2010-11-12
I try to test HTKDemo but the output on terminal is :
```
 Test Config File Read
 =====================
Parameter         Value
-----------------------

hsKind              p
covKind             d
nStreams            1
nMixes              1
Context             m
TiedState           n
VQ_clust            l
HERest_Iter         3
HERest_par_mode     n
Clean_up            y
Trace_tool_calls    y


HCopy               n
HList               n
HQuant              n
HLEd                n
HInit               y
HRest               y
HERest              y
HSmooth             n
HVite               y

Cleaning up directories
Done cleaning


./MakeProtoHMMSet protoconfs/proto_s1_m1_dc.pcf
 Proto Config File Read
 ======================
Parameter         Value
-----------------------

hsKind              p
covKind             d
nStates             3
nStreams            1
sWidths             26
mixes               1
parmKind            MFCC_E_D
vecSize             26
outDir              proto
hmmList             lists/bcplist


Writing HMMSet

Writing HMMDef to proto/S
Writing HMMDef to proto/C
Writing HMMDef to proto/V
Writing HMMDef to proto/N
Writing HMMDef to proto/L


Calling HInit for HMM S
sh: HInit: not found


Calling HInit for HMM C
sh: HInit: not found


Calling HInit for HMM V
sh: HInit: not found


Calling HInit for HMM N
sh: HInit: not found


Calling HInit for HMM L
sh: HInit: not found
Source Directory Empty hmms/hmm.0
binok@ubuntu:~/samples/HTKDemo$
```I've already created proto,hmms (hmm.0,hmm.1,hmm.2,hmm.3,temp),test folders.My bin folder is at home/binok/htk3.4/
Anybody help me?

---

### Post by fan_diana on 2011-03-11
hi, thaks for you
i solved this problem by installing libx11-dev as:
sudo apt-get install libx11-devd 

at the first time i have no result but after that i robot my machine, htk was installed

i whoul add that i do :"sudo make install" instead of "make install"

---

### Post by ahmed.gaber on 2011-04-11
> **Partyboi2 said:**
> I don't speak Portuguese but it looks like libx11-dev may not be installed. Open a terminal and try installing libx11-dev with
```
sudo apt-get install libx11-dev
```

Thanks So Much :)) I had the same problem and this worked very well with me.

---

### Post by dabraude on 2011-10-27
> **halfblood88 said:**
> I try to test HTKDemo but the output on terminal is :
```
 Test Config File Read
 =====================
Parameter         Value
-----------------------

hsKind              p
covKind             d
nStreams            1
nMixes              1
Context             m
TiedState           n
VQ_clust            l
HERest_Iter         3
HERest_par_mode     n
Clean_up            y
Trace_tool_calls    y


HCopy               n
HList               n
HQuant              n
HLEd                n
HInit               y
HRest               y
HERest              y
HSmooth             n
HVite               y

Cleaning up directories
Done cleaning


./MakeProtoHMMSet protoconfs/proto_s1_m1_dc.pcf
 Proto Config File Read
 ======================
Parameter         Value
-----------------------

hsKind              p
covKind             d
nStates             3
nStreams            1
sWidths             26
mixes               1
parmKind            MFCC_E_D
vecSize             26
outDir              proto
hmmList             lists/bcplist


Writing HMMSet

Writing HMMDef to proto/S
Writing HMMDef to proto/C
Writing HMMDef to proto/V
Writing HMMDef to proto/N
Writing HMMDef to proto/L


Calling HInit for HMM S
sh: HInit: not found


Calling HInit for HMM C
sh: HInit: not found


Calling HInit for HMM V
sh: HInit: not found


Calling HInit for HMM N
sh: HInit: not found


Calling HInit for HMM L
sh: HInit: not found
Source Directory Empty hmms/hmm.0
binok@ubuntu:~/samples/HTKDemo$
```I've already created proto,hmms (hmm.0,hmm.1,hmm.2,hmm.3,temp),test folders.My bin folder is at home/binok/htk3.4/
Anybody help me?

Looks like there is no link to it, check your bin folder is in the PATH environmental variable by typing 

echo $PATH

---

### Post by oldos2er on 2011-10-27
This thread is up way past its bed time. Closed.

---

