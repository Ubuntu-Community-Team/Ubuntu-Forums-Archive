---
title: "Getting VEOH player to work."
date: 2008-07-13
forum: General Help
---

### Post by Lodui on 2008-07-13
I'm trying to get VEOH player to work for me on linux.

I found this which looked helpful.

[http://ichthudion.wordpress.com/how-to-use-vget/](http://ichthudion.wordpress.com/how-to-use-vget/)

But when I got to the part where it tells me to type 

make sockets

from the veoh directory it feeds me this:

cd src/sockets-cpp && make -f Makefile
make[1]: Entering directory `/home/lode/openveoh/src/sockets-cpp'
g++  -Wall -g  -MD -D_VERSION='"2.1.7"' -O2 -DLINUX   -c -o Socket.o Socket.cpp
make[1]: g++: Command not found
make[1]: *** [Socket.o] Error 127
make[1]: Leaving directory `/home/lode/openveoh/src/sockets-cpp'
make: *** [sockets] Error 2


I'm thinking maybe I need to install some C++ libraries, but I'm just guessing. 

Help please.

---

