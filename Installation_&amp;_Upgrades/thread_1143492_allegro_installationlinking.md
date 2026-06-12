---
title: "allegro installation/linking"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by dulahdaglace on 2009-04-30
so im a newb, but im trying to link the libraries for allegro to my program

i tried adding 
PATH=$PATH:~/src/allegro-4.2.2/lib 
export PATH
to my ~/.bashrc file

and when i echo'ed $PATH it was there...
so when i ran g++ test.cpp -lalleg

/usr/bin/ld: cannot find -lalleg
collect2: ld returned 1 exit status

...im frustrated... ive googled and  stuff, ive uninstalled it and reinstalled it(./configure, make, sudo make install)...

much appreciation if anyone knows...

---

### Post by mike173 on 2009-04-30
> **dulahdaglace said:**
> so im a newb, but im trying to link the libraries for allegro to my program

i tried adding 
PATH=$PATH:~/src/allegro-4.2.2/lib 
export PATH
to my ~/.bashrc file

and when i echo'ed $PATH it was there...
so when i ran g++ test.cpp -lalleg

/usr/bin/ld: cannot find -lalleg
collect2: ld returned 1 exit status

...im frustrated... ive googled and  stuff, ive uninstalled it and reinstalled it(./configure, make, sudo make install)...

much appreciation if anyone knows...

Try this command:

g++ test.cpp -L~/src/allegro-4.2.2/lib -lalleg

PATH is not used to search for headers and libraries.  Run 'man gcc' and read about LIBRARY_PATH and CPATH.

Actually, allegro has configuration utility to help building programs.  For example:

> allegro-config --cflags --libs
> g++ test.cpp `allegro-config --cflags --libs`

---

### Post by dulahdaglace on 2009-04-30
those commands u gave resulted in the same message

---

