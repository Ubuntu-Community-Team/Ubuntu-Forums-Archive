---
title: "[SOLVED] Help Installing .tar.bz2"
date: 2008-08-27
forum: General Help
---

### Post by fparedesg on 2008-08-27
I just downloaded the latest version of Compiz Fusion (0.7.6) and I'm trying to install it. It's already extracted on my Desktop, so I do this:
```
federico@Anchova:~$ cd Desktop
federico@Anchova:~/Desktop$ cd compiz-bcop-0.7.6/
federico@Anchova:~/Desktop/compiz-bcop-0.7.6$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
federico@Anchova:~/Desktop/compiz-bcop-0.7.6$ sudo make
make: *** No targets specified and no makefile found.  Stop.
federico@Anchova:~/Desktop/compiz-bcop-0.7.6$ 

```

I don't know what to do. This has happened with other programs. When I'm trying to install, I get:
```
make: *** No targets specified and no makefile found.  Stop.
```

---

### Post by mb_webguy on 2008-08-27
Look at the output of the configure command -- it's not executing cleanly.  That means there's nothing to make.

It could be that there are unmet dependencies.  Open the terminal and type "sudo apt-get build-dep compiz", then try the configure command again and see if it executes properly this time.

---

### Post by oldos2er on 2008-08-27
First of all, do not run ./configure as root. Second, you need to install the package "build-essential". Ubuntu does not come with a default compiler, but build-essential will provide you with one.

---

### Post by mb_webguy on 2008-08-27
You don't need to run make as root, either.

./configure
make
sudo make install

---

### Post by fparedesg on 2008-08-28
> **mb_webguy said:**
> You don't need to run make as root, either.

./configure
make
sudo make install

I installed a package which seems to change the output. The package is:```
sudo apt-get install build-essential
```

When I don't run ./configure as root, I get this:
```
federico@Anchova:~/Desktop/compiz-bcop-0.7.6$ ./configure
./configure: line 1386: config.log: Permission denied
./configure: line 1396: config.log: Permission denied

```

What I now get is this:
```
federico@Anchova:~$ cd Desktop/compiz-bcop-0.7.6/
federico@Anchova:~/Desktop/compiz-bcop-0.7.6$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking dependency style of gcc... none
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) none
checking how to run the C preprocessor... gcc -E
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
checking whether byte ordering is bigendian... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LIBXSLT... yes
configure: creating ./config.status
config.status: creating bcop.pc
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/bcop
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
federico@Anchova:~/Desktop/compiz-bcop-0.7.6$ make
make  all-recursive
make[1]: Entering directory `/home/federico/Desktop/compiz-bcop-0.7.6'
Making all in src
make[2]: Entering directory `/home/federico/Desktop/compiz-bcop-0.7.6/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/federico/Desktop/compiz-bcop-0.7.6/src'
make[2]: Entering directory `/home/federico/Desktop/compiz-bcop-0.7.6'
make[2]: Leaving directory `/home/federico/Desktop/compiz-bcop-0.7.6'
make[1]: Leaving directory `/home/federico/Desktop/compiz-bcop-0.7.6'
federico@Anchova:~/Desktop/compiz-bcop-0.7.6$ sudo make install
Making install in src
make[1]: Entering directory `/home/federico/Desktop/compiz-bcop-0.7.6/src'
make[2]: Entering directory `/home/federico/Desktop/compiz-bcop-0.7.6/src'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
 /usr/bin/install -c 'bcop' '/usr/local/bin/bcop'
test -z "/usr/local/share/bcop" || /bin/mkdir -p "/usr/local/share/bcop"
 /usr/bin/install -c -m 644 'bcop.xslt' '/usr/local/share/bcop/bcop.xslt'
make[2]: Leaving directory `/home/federico/Desktop/compiz-bcop-0.7.6/src'
make[1]: Leaving directory `/home/federico/Desktop/compiz-bcop-0.7.6/src'
make[1]: Entering directory `/home/federico/Desktop/compiz-bcop-0.7.6'
make[2]: Entering directory `/home/federico/Desktop/compiz-bcop-0.7.6'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/pkgconfig" || /bin/mkdir -p "/usr/local/share/pkgconfig"
 /usr/bin/install -c -m 644 'bcop.pc' '/usr/local/share/pkgconfig/bcop.pc'
make[2]: Leaving directory `/home/federico/Desktop/compiz-bcop-0.7.6'
make[1]: Leaving directory `/home/federico/Desktop/compiz-bcop-0.7.6'

```

---

### Post by fparedesg on 2008-08-28
Ok, Compiz Fusion is installed. I added the source "http://ppa.launchpad.net/compiz/ubuntu hardy main" and refreshed sources. The packages needed to install the latest version of Compiz Fusion were there.

---

