---
title: "how do I update sauerbraten?"
date: 2008-07-27
forum: General Help
---

### Post by rdpsycho on 2008-07-27
hello, this is my first post. i am a former winxp user & gamer, i recently switched completely to ubuntu(hardy) and i am not a programmer so i dont really understand alot but anyways. 

i just downloaded sauerbraten from the sypnatic package manager and I really like the game but there is only 1 online server that has the same version as I do, the rest read "server has newer protocol" which i guess means my version is outdated.

there didnt appear to be any in-game updater, can someone please tell me the terminal command or w/e so that i can update the game? thank you very much. 

btw i have already tried the main ubuntu update manager and that didn't seem to find anything.

---

### Post by Ryadt on 2008-07-27
You will have to download it from its website and then install.

---

### Post by rdpsycho on 2008-07-27
the entire installer? there isnt like a small update file?

---

### Post by northern lights on 2008-07-27
Nope.

First run ```
sudo apt-get autoremove sauerbraten
```to remove the version you have installed now.

Then download from [here]("http://downloads.sourceforge.net/sauerbraten/sauerbraten_2008_06_20_ctf_edition_linux.tar.bz2"), extract the archive and start the game by running the 'Sauerbraten_Unix' script.

You can find the manual on sauerbraten.org

---

### Post by Vadi on 2008-07-27
getdeb.net has easy .debs to install, but unfortunately it's down at the moment (first time I've seen it happen).

---

### Post by northern lights on 2008-07-27
> **Vadi said:**
> getdeb.net has easy .debs to install
Same time to download (either way 300megs) and most likely the same version that is in the repos...

---

### Post by Vadi on 2008-07-27
No theirs has the summer CTF one.

---

### Post by rdpsycho on 2008-07-27
ok well i downloaded it from sourceforge, extracted the folder to /home and then tried to run sauerbraten by double clicking it, it wouldnt do anything, so i tried to install from the terminal well here is what i did in terminal

> 
clinton@clinton-desktop:~$ cd sauerbraten
clinton@clinton-desktop:~/sauerbraten$ sauerbraten
The program 'sauerbraten' is currently not installed.  You can install it by typing:
sudo apt-get install sauerbraten
bash: sauerbraten: command not found
clinton@clinton-desktop:~/sauerbraten$ '/home/clinton/sauerbraten/sauerbraten_unix' 
Your platform does not have a pre-compiled Sauerbraten client.
Please follow the following steps to build a native client:
1) Ensure you have the SDL, SDL-image, SDL-mixer, and OpenGL libraries installed.
2) Change directory to src/ and type "make install".
3) If the build succeeds, return to this directory and run this script again.
clinton@clinton-desktop:~/sauerbraten$ cd src/
clinton@clinton-desktop:~/sauerbraten/src$ make install
cd enet; ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking for ranlib... ranlib
checking for gethostbyaddr_r... yes
checking for gethostbyname_r... yes
checking for poll... yes
checking for fcntl... yes
checking for inet_pton... yes
checking for inet_ntop... yes
checking for struct msghdr.msg_flags... yes
checking for socklen_t... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking whether to use CRC32... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating include/Makefile
config.status: creating include/enet/Makefile
config.status: executing depfiles commands
make	-C enet/ all
make[1]: Entering directory `/home/clinton/sauerbraten/src/enet'
cd . && /bin/bash /home/clinton/sauerbraten/src/enet/missing --run aclocal-1.9 
/home/clinton/sauerbraten/src/enet/missing: line 52: aclocal-1.9: command not found
WARNING: `aclocal-1.9' is missing on your system.  You should only need it if
         you modified `acinclude.m4' or `configure.in'.  You might want
         to install the `Automake' and `Perl' packages.  Grab them from
         any GNU archive site.
 cd . && /bin/bash /home/clinton/sauerbraten/src/enet/missing --run automake-1.9 --foreign 
/home/clinton/sauerbraten/src/enet/missing: line 52: automake-1.9: command not found
WARNING: `automake-1.9' is missing on your system.  You should only need it if
         you modified `Makefile.am', `acinclude.m4' or `configure.in'.
         You might want to install the `Automake' and `Perl' packages.
         Grab them from any GNU archive site.
cd . && /bin/bash /home/clinton/sauerbraten/src/enet/missing --run autoconf
/home/clinton/sauerbraten/src/enet/missing: line 52: autoconf: command not found
WARNING: `autoconf' is missing on your system.  You should only need it if
         you modified `configure.in'.  You might want to install the
         `Autoconf' and `GNU m4' packages.  Grab them from any GNU
         archive site.
Making all in include
make[2]: Entering directory `/home/clinton/sauerbraten/src/enet/include'
Making all in enet
make[3]: Entering directory `/home/clinton/sauerbraten/src/enet/include/enet'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/clinton/sauerbraten/src/enet/include/enet'
make[3]: Entering directory `/home/clinton/sauerbraten/src/enet/include'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/clinton/sauerbraten/src/enet/include'
make[2]: Leaving directory `/home/clinton/sauerbraten/src/enet/include'
make[2]: Entering directory `/home/clinton/sauerbraten/src/enet'
if gcc -DPACKAGE_NAME=\"libenet\" -DPACKAGE_TARNAME=\"libenet\" -DPACKAGE_VERSION=\"10-12-2007\" -DPACKAGE_STRING=\"libenet\ 10-12-2007\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"libenet.a\" -DVERSION=\"10-12-2007\" -DHAS_GETHOSTBYADDR_R=1 -DHAS_GETHOSTBYNAME_R=1 -DHAS_POLL=1 -DHAS_FCNTL=1 -DHAS_INET_PTON=1 -DHAS_INET_NTOP=1 -DHAS_MSGHDR_FLAGS=1 -DHAS_SOCKLEN_T=1 -I. -I. -Iinclude/    -g -O2 -MT host.o -MD -MP -MF ".deps/host.Tpo" -c -o host.o host.c; \
	then mv -f ".deps/host.Tpo" ".deps/host.Po"; else rm -f ".deps/host.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"libenet\" -DPACKAGE_TARNAME=\"libenet\" -DPACKAGE_VERSION=\"10-12-2007\" -DPACKAGE_STRING=\"libenet\ 10-12-2007\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"libenet.a\" -DVERSION=\"10-12-2007\" -DHAS_GETHOSTBYADDR_R=1 -DHAS_GETHOSTBYNAME_R=1 -DHAS_POLL=1 -DHAS_FCNTL=1 -DHAS_INET_PTON=1 -DHAS_INET_NTOP=1 -DHAS_MSGHDR_FLAGS=1 -DHAS_SOCKLEN_T=1 -I. -I. -Iinclude/    -g -O2 -MT list.o -MD -MP -MF ".deps/list.Tpo" -c -o list.o list.c; \
	then mv -f ".deps/list.Tpo" ".deps/list.Po"; else rm -f ".deps/list.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"libenet\" -DPACKAGE_TARNAME=\"libenet\" -DPACKAGE_VERSION=\"10-12-2007\" -DPACKAGE_STRING=\"libenet\ 10-12-2007\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"libenet.a\" -DVERSION=\"10-12-2007\" -DHAS_GETHOSTBYADDR_R=1 -DHAS_GETHOSTBYNAME_R=1 -DHAS_POLL=1 -DHAS_FCNTL=1 -DHAS_INET_PTON=1 -DHAS_INET_NTOP=1 -DHAS_MSGHDR_FLAGS=1 -DHAS_SOCKLEN_T=1 -I. -I. -Iinclude/    -g -O2 -MT callbacks.o -MD -MP -MF ".deps/callbacks.Tpo" -c -o callbacks.o callbacks.c; \
	then mv -f ".deps/callbacks.Tpo" ".deps/callbacks.Po"; else rm -f ".deps/callbacks.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"libenet\" -DPACKAGE_TARNAME=\"libenet\" -DPACKAGE_VERSION=\"10-12-2007\" -DPACKAGE_STRING=\"libenet\ 10-12-2007\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"libenet.a\" -DVERSION=\"10-12-2007\" -DHAS_GETHOSTBYADDR_R=1 -DHAS_GETHOSTBYNAME_R=1 -DHAS_POLL=1 -DHAS_FCNTL=1 -DHAS_INET_PTON=1 -DHAS_INET_NTOP=1 -DHAS_MSGHDR_FLAGS=1 -DHAS_SOCKLEN_T=1 -I. -I. -Iinclude/    -g -O2 -MT packet.o -MD -MP -MF ".deps/packet.Tpo" -c -o packet.o packet.c; \
	then mv -f ".deps/packet.Tpo" ".deps/packet.Po"; else rm -f ".deps/packet.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"libenet\" -DPACKAGE_TARNAME=\"libenet\" -DPACKAGE_VERSION=\"10-12-2007\" -DPACKAGE_STRING=\"libenet\ 10-12-2007\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"libenet.a\" -DVERSION=\"10-12-2007\" -DHAS_GETHOSTBYADDR_R=1 -DHAS_GETHOSTBYNAME_R=1 -DHAS_POLL=1 -DHAS_FCNTL=1 -DHAS_INET_PTON=1 -DHAS_INET_NTOP=1 -DHAS_MSGHDR_FLAGS=1 -DHAS_SOCKLEN_T=1 -I. -I. -Iinclude/    -g -O2 -MT peer.o -MD -MP -MF ".deps/peer.Tpo" -c -o peer.o peer.c; \
	then mv -f ".deps/peer.Tpo" ".deps/peer.Po"; else rm -f ".deps/peer.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"libenet\" -DPACKAGE_TARNAME=\"libenet\" -DPACKAGE_VERSION=\"10-12-2007\" -DPACKAGE_STRING=\"libenet\ 10-12-2007\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"libenet.a\" -DVERSION=\"10-12-2007\" -DHAS_GETHOSTBYADDR_R=1 -DHAS_GETHOSTBYNAME_R=1 -DHAS_POLL=1 -DHAS_FCNTL=1 -DHAS_INET_PTON=1 -DHAS_INET_NTOP=1 -DHAS_MSGHDR_FLAGS=1 -DHAS_SOCKLEN_T=1 -I. -I. -Iinclude/    -g -O2 -MT protocol.o -MD -MP -MF ".deps/protocol.Tpo" -c -o protocol.o protocol.c; \
	then mv -f ".deps/protocol.Tpo" ".deps/protocol.Po"; else rm -f ".deps/protocol.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"libenet\" -DPACKAGE_TARNAME=\"libenet\" -DPACKAGE_VERSION=\"10-12-2007\" -DPACKAGE_STRING=\"libenet\ 10-12-2007\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"libenet.a\" -DVERSION=\"10-12-2007\" -DHAS_GETHOSTBYADDR_R=1 -DHAS_GETHOSTBYNAME_R=1 -DHAS_POLL=1 -DHAS_FCNTL=1 -DHAS_INET_PTON=1 -DHAS_INET_NTOP=1 -DHAS_MSGHDR_FLAGS=1 -DHAS_SOCKLEN_T=1 -I. -I. -Iinclude/    -g -O2 -MT unix.o -MD -MP -MF ".deps/unix.Tpo" -c -o unix.o unix.c; \
	then mv -f ".deps/unix.Tpo" ".deps/unix.Po"; else rm -f ".deps/unix.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"libenet\" -DPACKAGE_TARNAME=\"libenet\" -DPACKAGE_VERSION=\"10-12-2007\" -DPACKAGE_STRING=\"libenet\ 10-12-2007\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"libenet.a\" -DVERSION=\"10-12-2007\" -DHAS_GETHOSTBYADDR_R=1 -DHAS_GETHOSTBYNAME_R=1 -DHAS_POLL=1 -DHAS_FCNTL=1 -DHAS_INET_PTON=1 -DHAS_INET_NTOP=1 -DHAS_MSGHDR_FLAGS=1 -DHAS_SOCKLEN_T=1 -I. -I. -Iinclude/    -g -O2 -MT win32.o -MD -MP -MF ".deps/win32.Tpo" -c -o win32.o win32.c; \
	then mv -f ".deps/win32.Tpo" ".deps/win32.Po"; else rm -f ".deps/win32.Tpo"; exit 1; fi
rm -f libenet.a
ar cru libenet.a host.o list.o callbacks.o packet.o peer.o protocol.o unix.o win32.o 
ranlib libenet.a
make[2]: Leaving directory `/home/clinton/sauerbraten/src/enet'
make[1]: Leaving directory `/home/clinton/sauerbraten/src/enet'
g++ -Wall -fsigned-char -O3 -fomit-frame-pointer -Ishared -Iengine -Ifpsgame -Irpggame -Ienet/include -I/usr/X11R6/include `sdl-config --cflags`   -c -o shared/tools.o shared/tools.cpp
/bin/sh: sdl-config: not found
/bin/sh: g++: not found
make: *** [shared/tools.o] Error 127
clinton@clinton-desktop:~/sauerbraten/src$

---

### Post by northern lights on 2008-07-27
Run ```
cd sauerbraten && sh sauerbraten_unix
```

---

### Post by rdpsycho on 2008-07-27
clinton@clinton-desktop:~$ cd sauerbraten && sh sauerbraten_unix
Your platform does not have a pre-compiled Sauerbraten client.
Please follow the following steps to build a native client:
1) Ensure you have the SDL, SDL-image, SDL-mixer, and OpenGL libraries installed.
2) Change directory to src/ and type "make install".
3) If the build succeeds, return to this directory and run this script again.
clinton@clinton-desktop:~/sauerbraten$ sh sauerbraten_unix
Your platform does not have a pre-compiled Sauerbraten client.
Please follow the following steps to build a native client:
1) Ensure you have the SDL, SDL-image, SDL-mixer, and OpenGL libraries installed.
2) Change directory to src/ and type "make install".
3) If the build succeeds, return to this directory and run this script again.
clinton@clinton-desktop:~/sauerbraten$ cd sauerbraten && sh sauerbraten_unix
bash: cd: sauerbraten: No such file or directory
clinton@clinton-desktop:~/sauerbraten$

---

### Post by northern lights on 2008-07-27
Hmm. Will think about it. No idea of hand.

Never had to compile or install.

Before posting I downloaded the whole thing today and ran it: Downloaded, extracted, ran script - Sauerbraten started, good version, could connect to servers...

---

### Post by Vadi on 2008-07-27
Click [here]("apt:build-essential") to install build-essential, and try compiling again (the make command).

---

### Post by rdpsycho on 2008-07-27
Thank you so much Vadi, it works now. I was about to switch back to winxp. I love you but I'm not in love with you.

---

### Post by Vadi on 2008-07-27
Heh you're welcome. Let us know if you'll need any other help!

---

