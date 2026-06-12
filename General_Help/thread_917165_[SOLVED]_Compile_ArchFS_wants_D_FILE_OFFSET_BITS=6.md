---
title: "[SOLVED] Compile ArchFS wants D_FILE_OFFSET_BITS=64"
date: 2008-09-11
forum: General Help
---

### Post by SanskritFritz on 2008-09-11
Well, this is not strictly Kubuntu specific, but I count on this great community :-)
Here is my problem described:

[http://code.google.com/p/archfs/issues/detail?id=11](http://code.google.com/p/archfs/issues/detail?id=11)
```

frank@HomeC:~/Programs/ArchFS/Stable$ make
make  all-recursive
make[1]: Entering directory `/home/frank/Programs/ArchFS/Stable'
Making all in layout
make[2]: Entering directory `/home/frank/Programs/ArchFS/Stable/layout'
gcc -DHAVE_CONFIG_H -I. -I..     -Wall -O3  -D_GNU_SOURCE -MT core.o -MD
-MP -MF .deps/core.Tpo -c -o core.o core.c
In file included from /usr/include/fuse/fuse.h:26,
                 from /usr/include/fuse.h:9,
                 from ../headers.h:21,
                 from core.h:4,
                 from core.c:1:
/usr/include/fuse/fuse_common.h:32:2: error: #error Please add
-D_FILE_OFFSET_BITS=64 to your compile flags!
make[2]: *** [core.o] Error 1
make[2]: Leaving directory `/home/frank/Programs/ArchFS/Stable/layout'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/frank/Programs/ArchFS/Stable'
make: *** [all] Error 2
```Please can anybody find out what the problem is? Where must I put this flag, I guess in the makefile? Thanks in advance!

---

### Post by lukjad on 2008-09-11
Did you try to ./config or ./configure first? Also, maybe the command you are looking for is make install? I haven't tried to install for a while, so I'm not up to snuff here...

---

### Post by SanskritFritz on 2008-09-12
> **lukjad007 said:**
> Did you try to ./config or ./configure first? Also, maybe the command you are looking for is make install? I haven't tried to install for a while, so I'm not up to snuff here...Yes, ./configure went without a hitch. When I get home, I will post the results of that command as well.

---

### Post by SanskritFritz on 2008-09-13
Here is the output of 

frank@HomeC:~/Programs/ArchFS/Stable$ ./configure

```
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
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
checking for gzgets in -lz... yes
checking for fuse_main in -lfuse... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for an ANSI C-conforming const... yes
checking for off_t... yes
checking for size_t... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking whether closedir returns void... no
checking for pid_t... yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking whether time.h and sys/time.h may both be included... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for alarm... yes
checking for working mktime... yes
checking whether lstat dereferences a symlink specified with a trailing slash... yes
checking whether stat accepts an empty string... no
checking for getcwd... yes
checking for memset... yes
checking for rmdir... yes
checking for strtol... yes
checking for get_current_dir_name... yes
checking for getline... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating layout/Makefile
config.status: creating structure/Makefile
config.status: creating retriever/Makefile
config.status: creating support/Makefile
config.status: creating config.h
config.status: executing depfiles commands
```

---

### Post by SanskritFritz on 2008-09-23
Just for the record, the new version of ArchFS compiles and works well on my Kubuntu Hardy, I already have mounted my backup repository. Special thanks go to Gavin on the rdiff-backup list, who helped a lot, and to artoole who actually made the fix.

---

### Post by domu on 2008-11-17
I too have a problem with running make for ArchFS on Ubuntu 8.10 (sorry this is server not Kubuntu but this seemed a relevant thread), I run configure successfully then on doing 'make' I get:

```
dominic@rdiff-backup1:/usr/src/archfs$ sudo make
make  all-recursive
make[1]: Entering directory `/usr/src/archfs'
Making all in layout
make[2]: Entering directory `/usr/src/archfs/layout'
gcc -DHAVE_CONFIG_H -I. -I..     -Wall -O3 -D_FILE_OFFSET_BITS=64 -I/usr/include/fuse   -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -MT core.o -MD -MP -MF .deps/core.Tpo -c -o core.o core.c
mv -f .deps/core.Tpo .deps/core.Po
gcc -DHAVE_CONFIG_H -I. -I..     -Wall -O3 -D_FILE_OFFSET_BITS=64 -I/usr/include/fuse   -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -MT all.o -MD -MP -MF .deps/all.Tpo -c -o all.o all.c
mv -f .deps/all.Tpo .deps/all.Po
gcc -DHAVE_CONFIG_H -I. -I..     -Wall -O3 -D_FILE_OFFSET_BITS=64 -I/usr/include/fuse   -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -MT versions.o -MD -MP -MF .deps/versions.Tpo -c -o versions.o versions.c
mv -f .deps/versions.Tpo .deps/versions.Po
gcc -DHAVE_CONFIG_H -I. -I..     -Wall -O3 -D_FILE_OFFSET_BITS=64 -I/usr/include/fuse   -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -MT support.o -MD -MP -MF .deps/support.Tpo -c -o support.o support.c
support.c: In function ‘snapshot_copy’:
support.c:316: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
support.c: In function ‘snapshot_append’:
support.c:344: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
support.c:346: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
In function ‘open’,
    inlined from ‘unzip_revs’ at support.c:74:
/usr/include/bits/fcntl2.h:51: error: call to ‘__open_missing_mode’ declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[2]: *** [support.o] Error 1
make[2]: Leaving directory `/usr/src/archfs/layout'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/archfs'
make: *** [all] Error 2
```

Any suggestions very gratefully received!

Dominic

---

### Post by SanskritFritz on 2008-11-18
Have you tried *make* without *sudo*? *sudo* is only needed when doing *make install*.

---

### Post by domu on 2008-11-18
Thanks for the suggestion, maybe I didn't need the 'sudo', but anyway the problem was solved by a one-line fix to the code for archfs (0.5.3).

I presume this fix will be incorporated into the next release; if anyone needs it now, in layout/support.c at line 74 change:
```

if ((descriptor = open(mirror, O_WRONLY | O_CREAT)) == -1)
```
to:
```
if ((descriptor = open(mirror, O_WRONLY | O_CREAT, 0777)) == -1) 
```

My thanks to Andrew Ferguson for this!

---

### Post by SanskritFritz on 2008-11-18
This is interesting, I have compiled the 0.5.2 code base, and there is no difference in that line, so how come I was able to compile it?

---

### Post by domu on 2008-11-19
Not sure, perhaps you have a different compiler? I am using Ubuntu Server 8.10, and have gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11).

I have hit further problems with archfs trying to get it to play with samba. I have a bug fix (again from Andrew Ferguson) to allow other users to access an archfs mount, but I have an outstanding problem that inside the archfs mount - but only when viewed through samba - directories below the date level appear as zero length files.

---

### Post by SanskritFritz on 2008-11-19
I just compiled [archfs-0.5.3.tar.gz]("http://archfs.googlecode.com/files/archfs-0.5.3.tar.gz") successfully on
Kubuntu 8.04 Hardy
gcc (GCC) 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
Kernel 2.6.24-19-generic (I know, its old!)

---

