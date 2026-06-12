---
title: "Fingerprint Reader"
date: 2007-12-10
forum: Hardware &amp; Laptops
---

### Post by LinuxIsInnovation on 2007-12-10
I am using HP nx6320 Laptop.. Ive downloaded bioapi but I cannot make it work for my fingerprint reader. How do I use it.. please give the biometric software installation steps. Thanx in advance..

---

### Post by LinuxIsInnovation on 2007-12-10
I checked other topics from where, I tried thinkwiki forums. I did as indicated but when I tried to configure the file I go this:

glade@glade-laptop:~/bioapi-1.2.3$ ./configure --with-Qt-dir=no
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for flex... flex
checking lex output file root... lex.yy
checking lex library... -lfl
checking whether yytext is a pointer... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for bison... bison -y
configure: error: cannot run /bin/bash ./config.sub
glade@glade-laptop:~/bioapi-1.2.3$

---

### Post by LinuxIsInnovation on 2007-12-16
Bump..

---

### Post by LinuxIsInnovation on 2007-12-16
Ive installed pam_fprint, but its just askin for my right index finger, despite of the fact that all my fingers are enrolled.. Someone here using pam_fprint?

---

