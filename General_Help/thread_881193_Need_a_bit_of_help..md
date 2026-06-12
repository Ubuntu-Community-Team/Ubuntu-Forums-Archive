---
title: "Need a bit of help."
date: 2008-08-05
forum: General Help
---

### Post by Kyle12349 on 2008-08-05
I didn't really know where to put this thread so I've put it in general, if it's wrong then please redirect. I've been trying to upgrade my aMSN for a few months now but I can't get my head around it and I keep getting the same error over and over. There error message is:

root@Linux-Kyle:/home/kyle/Desktop/amsn-0.97.2# ./configure
checking for prefix by checking for wish... /usr/bin/wish
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking tcl build dir... using tcl library in /usr/lib/tcl8.4
checking tk build dir... using tk library in /usr/lib
./configure: line 3611: /usr/lib/tkConfig.sh: No such file or directory
root@Linux-Kyle:/home/kyle/Desktop/amsn-0.97.2#

Can someone please help me? And I would use a different messenger but I don't like the interfaces of the rest, I barely like the MSN interface itself. Any help would be appreciated.

---

### Post by ibuclaw on 2008-08-05
run
```
sudo apt-get build-dep amsn
```

And try it again

Regards
Iain

---

### Post by Kyle12349 on 2008-08-05
Ah :) Thank you so much. I've thanked you too.

---

### Post by hndaklr8480 on 2008-10-26
this didn't work for me still get the same error

checking for prefix by checking for wish... /usr/bin/wish
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking tcl build dir... using tcl library in /usr/lib/tcl8.4
checking tk build dir... using tk library in /usr/lib
./configure: line 3611: /usr/lib/tkConfig.sh: No such file or directory

---

