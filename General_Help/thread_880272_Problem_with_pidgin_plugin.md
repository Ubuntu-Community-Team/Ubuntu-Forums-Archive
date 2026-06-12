---
title: "Problem with pidgin plugin"
date: 2008-08-04
forum: General Help
---

### Post by medeshago on 2008-08-04
I'm trying to compile pidgin-latex and this is what I get after make:

gcc `pkg-config pidgin --cflags` -fPIC -Wall -Werror   -c -o pidgin-latex.o pidgin-latex.c
gcc `pkg-config pidgin --cflags` -fPIC -Wall -Werror   -c -o urlhandler.o urlhandler.c
gcc `pkg-config pidgin --cflags` -fPIC -Wall -Werror   -c -o plugin.o plugin.c
gcc `pkg-config pidgin --cflags` -fPIC -Wall -Werror   -c -o ui.o ui.c
gcc -o pidgin-latex.so pidgin-latex.o urlhandler.o plugin.o ui.o `pkg-config pidgin --libs` -shared `pkg-config pidgin --cflags` -fPIC -Wall -Werror
/usr/bin/ld: cannot find -lpurple
collect2: ld devolvió el estado de salida 1
make: *** [pidgin-latex.so] Error 1

I'm running hardy heron, pidgin 2.4.2 and I have installed pidgin-dev and liburple0-dev.

---

