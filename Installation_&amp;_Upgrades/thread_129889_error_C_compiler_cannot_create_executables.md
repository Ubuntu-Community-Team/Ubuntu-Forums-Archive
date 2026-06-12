---
title: "error: C compiler cannot create executables"
date: 2006-02-14
forum: Installation &amp; Upgrades
---

### Post by dantheman on 2006-02-14
I don't understand what's going on? I am trying to install xmms and mplayer. Xmms used to be in "apt-get" but all I get is this...
```
dan@cleardan:~$ sudo apt-get install xmms
Reading package lists... Done
Building dependency tree... Done
Package xmms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xmms has no installation candidate
dan@cleardan:~$
```
So I downloaded it, unzipped it and now trying to install it in the terminal. Generally, it would be 
./configure
make
make install 
and then you're done... but the ./configure gives me this error: 
```
dan@cleardan:~/Desktop/xmms-1.2.10$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for prefix by checking for xmms... no
checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot create executables
See `config.log' for more details.
dan@cleardan:~/Desktop/xmms-1.2.10$
```
Here is the interesting part of the config.log file... 
```
gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
configure:2415: $? = 0
configure:2417: gcc -V </dev/null >&5
gcc: '-V' option must have argument
configure:2420: $? = 1
configure:2444: checking for C compiler default output
configure:2447: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:2450: $? = 1
configure: failed program was:
| #line 2423 "configure"
| /* confdefs.h.  */
|
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "xmms"
| #define VERSION "1.2.10"
| #define DEV_DSP "/dev/dsp"
| #define DEV_MIXER "/dev/mixer"
| /* end confdefs.h.  */
|
| int
| main ()
| {
|
|   ;
|   return 0;
| }
configure:2489: error: C compiler cannot create executables
See `config.log' for more details.
```

This also give me the same error trying to ./configure MPlayer. 

I tried installing a new gcc version, and did (gcc4.0.2), but that didn't help... :-k 

Can anyone help? Thanks
-Dan-

---

### Post by Sutekh on 2006-02-14
What would you rather sort out?  XMMS should be in the repositories, so perhaps we can fix that problem.  

As with all compiling exercises have you installed **build-essential**?
It has important dev tools like make, and gcc.```
sudo apt-get install build-essential
```

Anyway, xmms should be in the repos, what's your sources.list?
```
cat /etc/apt/sources.list
```

---

### Post by dantheman on 2006-02-14
thanks for the build-essential... helped a lot....

now I need glib-config 

I'm trying to find an install for it... apt-get didn't find it... :-k

---

### Post by linear on 2006-02-14
There are some useful suggestions on finding missing pieces here:

[https://wiki.ubuntu.com/CompilingSoftware#head-69bd6c392f766fa1598f09efdc69d26c8afcaad8](https://wiki.ubuntu.com/CompilingSoftware#head-69bd6c392f766fa1598f09efdc69d26c8afcaad8)

Also, [Ubuntu packages]("http://packages.ubuntu.com/") allows you to search.

---

