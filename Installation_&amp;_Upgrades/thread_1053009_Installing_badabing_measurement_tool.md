---
title: "Installing badabing measurement tool"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by ipelotas on 2009-01-28
Hi everybody:

I'm trying to install a network measurement tool, namely Badabing, but I have encounter some problems. I've downloaded the package from [http://wail.cs.wisc.edu/waildownload.py](http://wail.cs.wisc.edu/waildownload.py). 

After extracting it, I have followed the instructions in the README for the installation: they are very simple: configure & make!

But configure doesn't work properly and so make. 

configure output:

```
$ sudo ./configure 
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... grep: ^ *+: No such file or directory
yes
checking whether g++ accepts -g... grep: ^ *+: No such file or directory
yes
grep: ^ *+: No such file or directory
grep: ^ *+: No such file or directory
grep: ^ *+: No such file or directory
grep: ^ *+: No such file or directory
checking whether make sets $(MAKE)... grep: temp=: No such file or directory
no
checking for a BSD-compatible install... /usr/bin/install -c
checking build system type... grep: ^LIBC=: No such file or directory
i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking how to run the C++ preprocessor... grep: ^ *+: No such file or directory
grep: ^ *+: No such file or directory
g++ -E
grep: ^ *+: No such file or directory
grep: ^ *+: No such file or directory
checking for egrep... egrep
checking for ANSI C header files... grep: ^ *+: No such file or directory
no
checking for sys/types.h... grep: ^ *+: No such file or directory
yes
checking for sys/stat.h... grep: ^ *+: No such file or directory
yes
checking for stdlib.h... grep: ^ *+: No such file or directory
yes
checking for string.h... grep: ^ *+: No such file or directory
yes
checking for memory.h... grep: ^ *+: No such file or directory
yes
checking for strings.h... grep: ^ *+: No such file or directory
yes
checking for inttypes.h... grep: ^ *+: No such file or directory
yes
checking for stdint.h... grep: ^ *+: No such file or directory
yes
checking for unistd.h... grep: ^ *+: No such file or directory
yes
checking sys/socket.h usability... grep: ^ *+: No such file or directory
yes
checking sys/socket.h presence... grep: ^ *+: No such file or directory
yes
checking for sys/socket.h... yes
checking float.h usability... grep: ^ *+: No such file or directory
yes
checking float.h presence... grep: ^ *+: No such file or directory
yes
checking for float.h... yes
checking for socklen_t... grep: ^ *+: No such file or directory
yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
grep: ^[         ]*#[    ]*define: No such file or directory
config.status: config.h is unchanged
```

make output:
```
$ sudo make
g++ -c badabing.cc  -g -pipe -Wall
badabing.cc: In member function ‘void BadaBing::receiver()’:
badabing.cc:318: error: ‘SOCKLEN_T’ was not declared in this scope
badabing.cc:318: error: expected `;' before ‘fromlen’
badabing.cc:319: error: ‘fromlen’ was not declared in this scope
make: *** [badabing.o] Error 1
```

Any clue on how to fit the error? I neither know what the error is!
I use Ubuntu 7.10 with kernel 2.6.22-16-generic.

Thank you in advance!

---

### Post by Partyboi2 on 2009-01-28
Have you installed the build-essential package?
```
sudo apt-get install build-essential
```

---

### Post by ipelotas on 2009-01-29
> **Partyboi2 said:**
> Have you installed the build-essential package?
```
sudo apt-get install build-essential
```
yes, it is in its last version. What else can be the problem?

---

