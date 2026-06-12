---
title: "Help with aMSN 0.95b"
date: 2005-12-05
forum: General Help
---

### Post by alekz on 2005-12-05
Hi im trying to install aMSN 0.95b but i got this error on ./configure
can some one help me ?

alekz@ubuntu:~/msn$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking for prefix by checking for wish... /usr/bin/wish
checking tcl build dir... using tcl library in /usr/lib/tcl8.4
checking tk build dir... using tk library in /usr/lib
./configure: line 3162: /usr/lib/tkConfig.sh: No such file or directory
alekz@ubuntu:~/msn$

thanks :)

---

### Post by -DarkMind- on 2005-12-05
sudo apt-get install tcl8.4-dev tk8.4-dev

---

